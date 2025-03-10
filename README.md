# ASX Financial Data & Risk Metrics (2000 - Present)

A comprehensive dataset and analysis of Australian financial markets, covering equities, bonds, real estate, commodities, forex, and macroeconomic indicators.

## Data Set

1) **Equities:** (2000 – Present) Historical data for the ASX 200 Index and sector indices, including Banking, Energy, Materials, Technology, Industrials, Healthcare, Consumer Goods, and Real Estate.
2) **Bonds:** (2000 – Present) Monthly historical data for Australian Government Bond yields (1-year, 5-year, 10-year, 20-year) and corporate bond yields (investment-grade & high-yield).
3) **Real Estate:** (2010 – Present) Quarterly data for residential and commercial property price indices, rental yields by major cities, and performance data for ASX-listed REITs.
4) **Commodities:** (2000 – Present) Daily historical data for commodity prices in AUD, including gold, iron ore, coal, lithium, and agricultural commodities.
5) **Forex:** (2000 – Present) Daily historical exchange rates for AUD/USD, along with the Trade-Weighted Index (TWI) and Australia’s forex reserves.
6) **Macroeconomic Indicators:** (2000 – Present) Annual and quarterly data on Australia’s GDP growth, inflation rates (CPI), interest rates (RBA cash rate, treasury yields), unemployment rates, and government debt levels.

---

## Risk & Volatility Calculations

- **Standard Deviation (Volatility):**  
  ```math
  \sigma = \sqrt{\frac{\sum (r_i - \bar{r})^2}{N}}
  ```  
  Calculated using Excel’s `STDEV.P()` function on simple returns.

- **Beta (for Equities & REITs relative to ASX 200 Index):**  
  ```math
  \beta = \frac{\text{Cov}(R_{asset}, R_{market})}{\text{Var}(R_{market})}
  ```  
  Computed using monthly returns to ensure consistency across asset classes.

- **Sharpe Ratio:**  
  ```math
  \text{Sharpe Ratio} = \frac{\text{Mean Return} - \text{Risk-Free Rate}}{\text{Standard Deviation of Returns}}
  ```  
  - **For Bonds:**  
    ```math
    \text{Sharpe Ratio} = \frac{\text{Average}(((\text{Annual Yield})/4) - \text{Risk-Free Rate})}{\text{Standard Deviation of Yield Change}}
    ```  
  - **For Rental Yields:**  
    ```math
    \text{Sharpe Ratio} = \frac{\text{Average}(((\text{Annual Yield})/12) - \text{Risk-Free Rate})}{\text{Standard Deviation of Yield Change}}
    ```

- **Maximum Drawdown:**  
  Represents the largest peak-to-trough decline in value over the period.

- **Correlation Matrix:**  
  Displays how different asset classes correlate with one another.

  **[Placeholder for Correlation Heatmap]**

---

## Data Processing

- **Equities:** Data was adjusted to a consistent timeframe to align with the available yfinance dataset.
- **Commodities:** Missing values were estimated using multivariate regression imputation, leveraging correlations with related commodities and indices (e.g., gold prices correlated with AUD/USD) to maintain dataset integrity.
- **Real Estate (CPPI):** Missing quarterly values were interpolated using multivariate techniques, referencing related indices such as the residential property index and REIT performance.
- **Bonds:** In the absence of coupon prices, bond prices were approximated under the assumption of zero-coupon bonds.

### **Bond Price Formula:**
```math
P = \frac{100}{(1 + YTM)^T}
```
where:
- \( P \) = Bond price
- \( YTM \) = Yield to Maturity
- \( T \) = Time to maturity (in years)

**[Placeholder for Bond Yield Curve Visualization]**

---

## Data Normalization & Interpolation

- **Returns Calculation:**
  - **Equities, Commodities, Real Estate, Forex:**
    ```math
    r_t = \frac{P_t - P_{t-1}}{P_{t-1}}
    ```
    where \( P \) represents the price at time \( t \).
  - **Bonds:**
    - Returns were derived from percentage changes in yields instead of price returns.

- **Data Resampling:**
  - To maintain consistency across asset classes, all data was standardized to a quarterly frequency.

---

## Data Delivery

- **Final Dataset:** A comprehensive workbook containing processed data, risk metrics, and monthly returns for correlation analysis.
- **Raw Data:** Provided separately to illustrate pre-processing steps.
- **Note:** All values are denominated in AUD. Data constraints due to free resources may limit historical coverage for some assets.

---

This project delivers a structured and comprehensive dataset for financial risk analysis across Australian markets, facilitating data-driven insights into volatility, correlations, and asset performance over time.

