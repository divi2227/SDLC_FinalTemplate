# Scope

## In Scope

### Core Functionality
- Stock data retrieval and display
- Support for multiple prioritization criteria: ROI, growth potential, and dividend yield
- Ranking algorithm that orders stocks based on user-selected criteria
- Display of top-performing stocks based on personalized rankings

### User Experience
- Simple, intuitive user interface for setting investment priorities
- Clear, organized presentation of stock rankings
- Fast data retrieval and response times (sub-2-minute performance)

### Initial Feature Set
- Support for major, liquid stocks (S&P 500 constituents or similar)
- Three primary metrics: ROI, growth, and dividends
- Display of top 10–50 stocks based on ranking

## Out of Scope

### Features Not Included in MVP
- Advanced technical analysis or charting tools
- Real-time portfolio tracking or holdings management
- Trade execution or order placement
- Advanced filtering beyond the three primary metrics
- Backtesting or historical performance simulation
- Mobile application (initial phase is web-based)
- Social features, community, or peer comparison
- News feeds, market updates, or financial commentary

### Data and Integration
- Integration with brokerage accounts or direct account linking
- Real-time stock price updates (acceptable with 15–30-minute delays)
- International stocks or non-US markets
- Crypto, bonds, or alternative investment vehicles
- Integration with accounting or tax software

## Assumptions

1. **Data Availability:** Historical and current stock data for major US equities is readily available via free or affordable APIs.
2. **User Base:** The initial target audience consists of retail investors with basic financial literacy.
3. **Device Access:** Users have reliable internet access and will access the platform via a web browser.
4. **Metric Consistency:** ROI, growth, and dividend metrics can be calculated and normalized consistently across all stocks.
5. **Update Frequency:** Daily or weekly data updates are sufficient for user needs; real-time updates are not required for MVP.
6. **Data Quality:** Available stock data is accurate, consistent, and suitable for direct consumer use without extensive disclaimers or financial advisory review.
