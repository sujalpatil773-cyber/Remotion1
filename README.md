# BTC Microstructure Terminal

A browser-native BTCUSDT market-microstructure dashboard using live public Binance WebSocket feeds. It is deliberately **not a fake prediction model**: every displayed metric is calculated from incoming market data in the browser.

## Live feeds

- Binance Spot `btcusdt@depth20@100ms`
- Binance Spot `btcusdt@aggTrade`
- Binance Spot `btcusdt@bookTicker`
- Binance USDⓈ-M Futures `btcusdt@bookTicker`

## Metrics

- L2 order-book imbalance across the top 20 levels
- Quote/order-flow imbalance from best bid/ask changes
- Taker buy/sell aggression from aggregate trades
- Best-level queue depth
- Displayed-liquidity withdrawal/cancellation proxy
- Order/depth arrival intensity
- Liquidity additions/replenishment
- Bid/ask spread and spread in bps
- Microprice and microprice edge
- 1-minute realized volatility estimate
- Spot/futures basis and basis in bps
- Live top-of-book visualization
- 60-second signed trade-flow timeline
- Feed event age / observed websocket event latency

## Important measurement limits

Public Binance L2 does not expose your personal queue position, so the dashboard explicitly reports queue position as `N/A` and shows the live best-level queue instead. Likewise, public depth updates do not identify a cancellation separately from every other displayed-size reduction, so the cancellation panel is labeled as a **proxy** rather than pretending it is exact.

The dashboard is market-data analytics only and does not place orders.

## Run

Serve this directory from any static web server and open `index.html`. A normal local server is recommended because browser WebSocket/security behavior can differ when an HTML file is opened directly from disk.

No API key is required for these public market-data streams.
