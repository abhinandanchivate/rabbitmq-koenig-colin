Scenario
You are building a Stock Market Notification System where different services handle different types of stock updates:

NYSE Tech Stocks
Forex Market Updates
Crypto Market Updates
✅ Routing Rules:
Routing Key Pattern	Purpose
stock.nyse.tech.*	Matches any single event from NYSE tech stocks
market.forex.#	Matches all forex updates
market.crypto.#	Matches all crypto updates
stock.nyse.tech.trade	Matches specific NYSE tech trade events
market.crypto.btc.price	Matches specific Bitcoin price updates
market.crypto.eth.*	Matches any Ethereum updates
✅ Architecture
➡️ 1 Exchange
➡️ 3 Queues:

Tech Stocks Queue – Handles NYSE tech updates
Forex Queue – Handles forex updates
Crypto Queue – Handles crypto updates

Step 1: Create the Publisher
Create a publisher that will send messages to a topic exchange with different routing keys:

 Step 2: Create Multiple Consumers
Now, we will create three consumers that will subscribe to specific patterns.

Consumer 1 – Tech Stocks
Matches:

stock.nyse.tech.*
stock.nyse.tech.trade

Consumer 2 – Forex Market
Matches:

market.forex.#

Consumer 3 – Crypto Market
Matches:

market.crypto.#
market.crypto.btc.price
market.crypto.eth.*


How It Works
Publisher sends messages with different routing keys.
RabbitMQ routes messages to queues based on patterns:
stock.nyse.tech.trade → Tech Stocks Queue ✅
market.forex.eur.usd → Forex Queue ✅
market.crypto.btc.price → Crypto Queue ✅
Consumers receive matching messages based on routing patterns.
