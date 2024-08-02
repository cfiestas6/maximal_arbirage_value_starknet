# Maximal Arbitrage Value implementation for Starknet

The paper [Layer-2 Arbitrage: An empirical Analysis of Swap Dynamics and Price Disparities on Rollups](https://arxiv.org/pdf/2406.02172) by Krzysztof Gogol et. al. was awarded as best paper from the MARBLE conference. The paper introduces the Maximal Arbitrage Value (MAV) metric to quantify arbitrage opportunities between an Automated Market Maker (AMM) and a Centralized Exchange (CEX).

The metric is similar to the Loss-Versus-Rebalancing (LVR) metric but is tailored to avoid double-counting identical arbitrage opportunites that span several blocks.

Key components of the MAV methodology:
1. Block Intervals: The methodology involves analyzing the closing prices of ETH-USDC on Binance every second and comparing them with the spot prices on the Automated Market Maker (AMM) DEX at each block. The spot price on the DEX is determined by the last swap within the block.

2. Price Re-Alignment Threshold: Only price deviations that exceed a specified threshold are considered. This threshold is determined from the empirical distribution of price differences, focusing on outliers beyond 1.5 times the interquartile range above the third quartile.

3. Empirical MAV: During periods of price misalignment, only the highest MAV within each time segment is documented to avoid counting the same price discrepancy multiple times.

4. Decay Time: The duration required for prices to re-align (i.e., when the magnitude of the price difference drops below the specified threshold) is measured to determine the decay time of price discrepancies.
