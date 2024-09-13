---
{"dg-publish":true,"permalink":"/cards/chingiz-proposal/index/","created":"2024-09-07T15:55:05.787-07:00","updated":"2024-09-11T15:53:19.651-07:00"}
---


<br /><br />


**What I have built so far:**


<u>APIs for the following</u>:
	- live price & volume data
	- historical price & volume data
	- live trading event data
	- historical trading event data
	- event filtration (what determines a tradable event?)
	- resistance / support levels
	- tickerSymbols, company information, including sector, similar companies
	- proxies
	- real-time technical analysis calculations

<u>Modules</u>:
	- logging
	- environment and configuration variables
	- utilities
	- backtesting
	- interactive brokers reader
	- interactive brokers writer

The vision for the backtesting is to have a rapid CLI, with a frontend dashboard built on-top. Backtesting can be developed separately from live-trading, but eventually will be remerged back with the live-trading, feeding backtesting results into the trading algorithm, in order to modify risk-tolerance, watchlist prioritization, defensive/offensive balances, etc. As market conditions evolve the trading algorithms will adapt based on short-term backtesting results.

Interactive Brokers API is extremely finicky. I have split the code for it into two pieces, and have isolated it as much as possible from the main codebase. My codebase will simply read statuses from interactive brokers, in order to determine whether an order has filled, at what price, etc, etc, and update the order database with this information. All trades will be created internally, and then the ibWriter will send this information to interactive brokers gateway, creating the order on the interactive brokers side. 


**<u>What I need help with</u>:**
	1. **process management**
		• using bash, pm2, ansible, or alternatives. This project is 90% nodejs, but python where it is required. In order to manage the complexities better process management will be needed in order to coordinate the different modules and handle errors.
	2. **central logging**
		• Implement a unified logging system that aggregates logs from various modules and APIs, ensuring real-time monitoring and troubleshooting.
	3. **backtesting via CLI, dashboard**
		• Develop a robust CLI-based backtesting solution.
		• Create a web-based dashboard to visualize backtesting results and provide deeper insights into strategy performance.
	4. **order managements via CLI, dashboard**
		• Build a CLI-based interface for order management to handle live and historical trading data.
		• Implement a dashboard for visual order management, including tracking and executing orders.
	5. **charting**
		• Integrate charting capabilities to visualize price data, trading events, resistance/support levels, and backtest performance.
		• this leads to insight, faster backtest analysis and trade ideas.

