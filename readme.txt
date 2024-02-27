## Introduction

This repository contains the code to calculating arbitrage opportunities between two Uniswap pools. Uniswap is a decentralized exchange (DEX) platform on the Ethereum Blockchain that allows users to trade ERC20 tokens without intermediaries or platform fees. Uniswap utilizes automated market-making algorithms and liquidity pools to facilitate token trading, eliminating the need for traditional order books and matching buyers and sellers.

Each Uniswap smart contract, or pair, manages a liquidity pool made up of reserves of two ERC-20 token. Pairs act as automated market makers, standing ready to accept one token for the other as long as the “constant product” formula is preserved. This formula, most simply expressed as x * y = k, states that trades must not change the product (k) of a pair’s reserve balances (x and y). Because k remains unchanged from the reference frame of a trade, it is often referred to as the invariant. This formula has the desirable property that larger trades (relative to reserves) execute at exponentially worse rates than smaller ones. In practice, Uniswap applies a 0.30% fee to trades, which is added to reserves. As a result, each trade actually increases (k).

The Python code has been split into 4 sections to illustrate how we can have an implement asynchornous trading when there is an arbitrage opportunity between both pools.


## Getting Started
To get started, install the following dependencies:
- pip install asyncio
- pip install math
- pip install time


## Methodology

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


## Author

Jovi Lim Ke Wei
linkedin.com/jovi-lim-ke-wei/
National University of Singapore MSc. Quantitative Finance
