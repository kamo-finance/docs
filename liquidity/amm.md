# AMM

**Basic Definitions:**

**Market:** A platform where users can trade SY for PT, or provide liquidity. The market contains a specific number of SY and PT tokens at any given time.

* **SY (Standardized Yield Token):** Defined separately, SY represents a standardized yield over time. At any given time tt, the market possesses n\_sy(t) SY tokens.
* **PT (Principal Token):** Defined in the Yield Tokenization paper, PT correlates to the SY token. At any given time tt, the market holds n\_pt(t) PT tokens.

**Asset:** The primary asset associated with the SY token.

**sy\_ExchangeRate(t):** This parameter indicates the rate at which one SY token can be exchanged for the underlying asset at a given time t (For example, 1 **SY** can swap to **sy\_ExchangeRate(t)** asset). The exchange utilizes underlying protocols such as Haedal, SpringSUI, etc

**Total Asset:** The total equivalent value of the asset that the SY tokens in the market are worth at time t, abbreviated as n\_asset(t):

* n\_asset(t) = n\_sy(t) \* sy\_ExchangeRate(t)

**Expiry and Time Metrics:**

* **Expiry:** The designated expiry time of the PT token.
* **timeToExpiry(t):** The remaining time at **t** until the PT token expires, calculated as timeToExpiry(t) = Expiry - t
* **yearsToExpiry(t):** The time to expiry expressed in years, computed as yearsToExpiry(t) = timeToExpiry(t) / (one year duration).

**Market Dynamics:**

* **Proportion (proportion(t)):** Indicates the proportion of PT in the market at time t, calculated as p(t)=n\_pt(t) + n\_asset(t) .
* **Scalar Root:** A fixed parameter for each market, adjusting the capital efficiency based on the rate scaler.
* **Initial Anchor:** Establishes the initial rate anchor to enhance capital efficiency around a certain interest rate.
* **Fee Rate Root:** A fixed market parameter determining the fees rate in terms of interest rate.
* **Rate Scalar (rateScalar(t)rateScalar(t)):** A parameter for adjusting the capital efficiency of the exchange rate at time tt, defined as scalarRootyearsToExpiry(t)\frac{scalarRoot}{yearsToExpiry(t)}.
* **Rate Anchor (rateAnchor(t)rateAnchor(t)):** Adjusts the interest rate around which trading will be most capital efficient.

**Exchange Rate:**

* **Exchange Rate (exchangeRate(t)exchangeRate(t)):** The spot exchange rate of the asset in PT, excluding any fees, where exchangeRate(t)=ln⁡(p(t)1−p(t))×rateScaler(t)+rateAnchor(t)exchangeRate(t) = \ln\left(\frac{p(t)}{1-p(t)}\right) \times rateScaler(t) + rateAnchor(t). The value of 1 PT should naturally be less than or equal to the value of 1 asset, meaning exchangeRate(t)≥1exchangeRate(t) \geq 1.

**Implied Rate:**

* **Implied Rate for a Specific Exchange Rate (impliedRateForExchangeRate(exchangeRate0,t)impliedRateForExchangeRate(exchangeRate0, t)):** The annual return rate implied by valuing PT at exchangeRate0exchangeRate0 asset, with a capital of 1 asset equaling exchangeRate0exchangeRate0 PT, leading to exchangeRate0exchangeRate0 asset after the duration of timeToExpiry(t)timeToExpiry(t).
* **Exchange Rate for an Implied Rate (exchangeRateForImpliedRate(impliedRate0,t)exchangeRateForImpliedRate(impliedRate0, t)):** The exchange rate equivalent to an implied rate of impliedRate0impliedRate0 at time tt.

**Liquidity Tokens and Providers:**

* **Liquidity Token:** Represents ownership in the market liquidity pool. At time tt, there are L(t)L(t) liquidity tokens available.
* **Liquidity Providers:** Users who contribute liquidity to the market. At any given time tt, a liquidity provider uu holds lu(t)lu(t) liquidity tokens, where lu(t)=L(t)lu(t) = L(t).
