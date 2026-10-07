# LogisticsLayer

**A data analysis project exploring carrier routing networks and distribution patterns through personal shipping history.**

LogisticsLayer correlates shipment metadata extracted from Gmail with public distribution center (DC) facility datasets to identify and visualize heavily-used shipping routes, carrier network topology, and logistics bottlenecks for residential delivery to Lynnwood, WA.

## Project Purpose

Traditional shipping transparency is limited to point-in-time tracking updates. LogisticsLayer reverse-engineers carrier routing decisions by:
- Extracting and normalizing shipment metadata (origin, carrier, service type, delivery date) from email notifications
- Mapping carrier service types to their respective hub-and-spoke networks
- Correlating delivery times with known DC locations to infer probable transit routes
- Identifying which facilities and hubs process inbound shipments to a specific destination

This reveals patterns in how carriers optimize their networks, including:
- Primary vs. secondary routing paths
- Regional consolidation hubs vs. last-mile fulfillment centers
- Seasonal capacity shifts
- Service-tier routing differences (express vs. ground)

## Methodology

### Data Collection
1. **Gmail Extraction**: Parse shipping emails from Amazon, UPS, FedEx, and USPS
   - Amazon: Extract order date, ship date, delivery date, product category
   - Carrier notifications: Extract tracking numbers, origin, service type, estimated delivery
   - Limited by email retention windows (30-120 days for carrier tracking history)

2. **DC Reference Dataset**: Aggregate public facility directories from major carriers
   - Amazon Fulfillment Centers and Sortation Centers
   - UPS Regional Hubs and Sort Facilities
   - FedEx Air Hubs, Ground Hubs, and Regional Distribution Centers
   - USPS Processing and Distribution Centers

### Analysis Approach
- **Route Inference**: Cross-reference tracking milestones with DC locations to identify probable transit sequences
- **Network Topology**: Map carrier hub-and-spoke architectures and regional consolidation patterns
- **Delivery Pattern Analysis**: Correlate transit times with facility locations to identify primary vs. secondary routing
- **Temporal Trends**: Track seasonal shifts in routing as carrier capacity fluctuates

## Current Data

- **amazon_events.csv**: 26 order/shipment/delivery events (Sept-Aug 2026)
- **tracking_numbers.csv**: 7 carrier tracking records with shipment metadata (UPS, FedEx, USPS)
- **dc_locations.csv**: 44 major distribution facilities across all major carriers

## Project Scope

- **Destination**: All analysis focuses on residential deliveries to 18925 46th Ave W, Lynnwood, WA 98036
- **Timeframe**: September 2026 – October 2026 (limited by email retention and historical tracking data availability)
- **Carriers Tracked**: Amazon (first-party), UPS, FedEx, USPS
- **Service Types**: Ground, Home Delivery, Express, Standard

## Next Steps

- [ ] Implement route visualization (map with probable path overlays)
- [ ] Build carrier network topology diagram (hub hierarchy and interconnections)
- [ ] Analyze transit time variance by service tier and origin zone
- [ ] Identify seasonal routing shifts and capacity patterns
- [ ] Correlate facility workload (inferred from delivery frequencies) with transit times
- [ ] Extended historical tracking (prospective data collection from incoming shipments)

## Data Sources

- Gmail API (personal shipping notification emails)
- Amazon.com Fulfillment Center directory
- UPS facility locators and service documentation
- FedEx hub and facility information
- USPS Processing & Distribution Center locators
- Carrier-published routing guides and service level agreements

## Repository Structure

```
LogisticsLayer/
├── data/
│   ├── amazon_events.csv          # Order/ship/delivery event log
│   ├── tracking_numbers.csv       # Carrier tracking records with metadata
│   └── dc_locations.csv           # Distribution center reference dataset
├── README.md                       # Project documentation
└── .gitignore                      # Standard Python/Node ignores
```

## Notes on Data Quality

- **Carrier tracking history retention**: 30-120 days post-delivery (impacts historical analysis)
- **Email parsing challenges**: Carrier notifications are HTML-only; tracking numbers extracted from email source
- **Destination consistency**: All shipments analyzed converge at single Lynnwood address (simplifies route inference)
- **Service type variation**: Shipments span express, ground, and standard services (enables service-tier comparison)

