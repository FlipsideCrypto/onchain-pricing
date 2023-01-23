# Topic: Onchain-Pricing

For a deeper dive into AMMs, I recommend reviewing the [Uniswap v2 Explainer](https://science.flipsidecrypto.xyz/uni_v2_explained) which dives into the most popular/forked/copied AMM model 
in crypto and its math and key vocabulary: slippage and price impact.

This report details an on-chain pricing methodology for historical *block level* pricing. Historical data on prices is available from central exchanges and 3rd parties like Coingecko. While point in time prices can be accessed on chain with oracles like Chainlink or pool-specific price reads from Decentralized Exchanges like Uniswap. 

The motivation is 3-fold:

1. Historical Prices should be usable for analysis of small time-windows, e.g., < 60 minutes. 
2. Historical Prices should be "realistic", that is, we should believe that our price *could have been* realized somewhere in the ecosystem within the small time-window.
3. Historical Prices should be smooth in normal times, but reactive to sustained volatility that did occur.

For a deeper dive into the context, you can check out the report on our [research site](https://science.flipsidecrypto.xyz/research/) at [onchain-pricing](https://science.flipsidecrypto.xyz/onchain-pricing).

If you aren't interested in code and want the shortest summary of the situation, you can check out the email sized [onchain-pricing](https://flipsidecrypto.beehiiv.com/p/onchain-pricing) on our research beehiiv and subscribe to get (summaries of) the best crypto research direct to your inbox.

# Reproduce Analysis

All analysis is reproducible using the R programming language. You'll need (1) an shroomDK API key to copy our SQL queries and extract data from the [FlipsideCrypto data app](https://next.flipsidecrypto.xyz/); and (2) renv to get the exact package versions we used.

## shroomDK

shroomDK is an R package that accesses the FlipsideCrypto REST API; it is also available for Python. You pass SQL code as a string to our API and get up to 1M rows of data back!

Check out the [documentation](https://docs.flipsidecrypto.com/shroomdk-sdk/get-started) and get your free API Key today.

## renv

renv is a package manager for the R programming language. It ensures analysis is fully reproducible by tracking the exact package versions used in the analysis.

`install.packages('renv')`

## Instructions

To replicate this analysis please do the following:

1.  Clone this repo.
2.  Save your API key into a .txt file as 'api_key.txt' (this exact naming allows the provided .gitignore to ignore your key and keep it off github).
3.  Open the `onchain-pricing` R Project file in your R IDE (we recommend, RStudio).
4.  Confirm you have renv installed.
5.  Restore the R environment using `renv::restore()` while in the `onchain-pricing` R Project.
6.  You can now run `onchain-pricing.Rmd`

If any errors arise, double check you have saved your API key in the expected file name and format.
