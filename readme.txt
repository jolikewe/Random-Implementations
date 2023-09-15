This repository contains code for calculating arbitrage opportunities between two Uniswap pools.

## Getting Started
To get started, install the following dependencies:

pip install asyncio
pip install math
pip install time

Once you have installed the dependencies, follow the code in the uniswap.py file

## PoolStatus
PoolStatus is a class that contains the following methods:
1) getPrice - obtain the ETH-DAI relative price
2) add - add X amount of ETH/DAI into the pool
3) remove - remove X amount of ETH/DAI into the pool
4) getPriceInput - generate the corresponding amount of tokens required to output X amount tokens, before accounting for 0.3% fees
5) getPriceOutput - generate the output amount of corresponding tokens when you input X amount of tokens, after accounting for 0.3% fees
6) swap - depending on the input token, the pool will adjust the balanced tokens according while maintaining k
7) check - print out the current status of the pool

## PoolStatus v2
The subsequent section shows an improved PoolStatus class whereby asynchronous running is enabled.

The function calculate_arbitrage() is also generated whereby we return the arbitrage opportunity of trading DAI between two pools. If an arbitrage opportunity exists, the function returns a tuple containing the required eth to start off the trade, the resulted profit as well as the pool in which we commence the trading.

The function opportunityStatus() prints out the details generated from calculate_arbitrage().

## Test cases
The test cases showcase the swapping of both ETH and DAI tokens, as well as how the k value increases slightly after each trade.

## Harnessing arbitrage opportunity
The final section shows the time taken when we consecutively calculate the existence of an arbitrage opportunity as well as excucuting the trade when it exists, till the opportunity disappears.


## Readings
* Uniswap - https://uniswap.org/
* Arbitrage - https://github.com/ccyanxyz/uniswap-arbitrage-analysis
* Asyncio - https://docs.python.org/3/library/asyncio.html