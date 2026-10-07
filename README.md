# LogisticsLayer

Analysis of shipping routes and distribution patterns through Gmail tracking data and public DC locations.

## Project Overview

LogisticsLayer explores carrier routing networks by correlating:
- Historical shipping data from Gmail (tracking numbers, delivery dates, shipper origins)
- Public distribution center (DC) location datasets
- Carrier-specific facility information

## Current Data

- **Amazon Events**: 26 order/ship/delivery events extracted from Gmail (Sept-Aug 2026)
- **Tracking Numbers**: 5 carrier tracking records (UPS, FedEx, USPS)
- **DC Locations**: 9 major regional distribution hubs

## Next Steps

- [ ] Expand DC location dataset to 50+ facilities
- [ ] Extract carrier tracking data from HTML emails
- [ ] Build routing probability model
- [ ] Visualize heatmap by frequency
- [ ] Analyze seasonal patterns

## Data Sources

- Gmail shipping notifications
- Amazon Fulfillment Center directory
- UPS/FedEx/USPS facility locators
- Bureau of Transportation Statistics

