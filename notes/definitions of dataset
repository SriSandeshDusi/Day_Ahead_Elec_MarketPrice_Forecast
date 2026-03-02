# IEX Electricity Market Dataset — Definitions & Field Notes

This document defines every column in the electricity market dataset used for the project **“Forecasting Electricity Market Prices using Cascaded Neural Networks and Evolutionary Optimization.”**
It serves as a reference for data preprocessing, modeling, and interpretation.

---

# 1. Market Context

The dataset comes from the **Day‑Ahead Market (DAM)** of an electricity exchange (e.g., IEX India).

In DAM:

* Electricity for the next day is traded
* Each day is divided into **96 time blocks**
* Each block = **15 minutes**
* Market determines a uniform clearing price per block

This clearing price is called **MCP (Market Clearing Price)**.

---

# 2. Time Structure Columns

## Date

Calendar delivery date of electricity (YYYY‑MM‑DD).

Important: This refers to the **delivery day**, not the trading day.

---

## Hour

Hour of the day (1–24).

Used for:

* hourly aggregation
* diurnal pattern analysis

---

## Time Block

Index of the 15‑minute interval within the day.

Range: **1–96**

Example:

* Block 1 → 00:00–00:15
* Block 2 → 00:15–00:30
* …
* Block 96 → 23:45–00:00

This represents the **position within daily price curve**.

---

# 3. Market Price Columns

## MCP (Rs/MWh)

**Market Clearing Price** for the time block.

Definition:

> The uniform price at which electricity supply equals demand in the market auction.

Units: INR per MWh

Role in project:

* Primary prediction target
* Forecasted for next 96 blocks

Properties:

* Highly nonlinear
* Seasonal (daily pattern)
* Spike‑prone
* Influenced by bids and constraints

---

# 4. Volume / Bid Columns

## Purchase Bid (MW or MWh)

Total demand volume submitted by buyers for the block.

Represents:

* Market demand pressure
* Expected consumption

Interpretation:

* Higher purchase bids → upward price pressure

---

## Sell Bid (MW or MWh)

Total supply volume submitted by generators for the block.

Represents:

* Available generation
* Supply availability

Interpretation:

* Higher sell bids → downward price pressure

---

## MCV (MW or MWh)

**Market Clearing Volume**.

Definition:

> Total electricity volume matched at MCP in the auction.

Meaning:

* Amount of energy actually traded
* Intersection quantity of supply & demand curves

Use in modeling:

* Demand–supply balance indicator
* Market tightness proxy

---

## Final Scheduled Volume (MW or MWh)

Final dispatch volume after operator scheduling adjustments.

Usually ≈ MCV, but may differ due to:

* grid constraints
* ramp limits
* system balancing

Model role:

* Realized market outcome
* Stability indicator

---

# 5. Derived Market Relationships

The DAM auction clears where:

Supply(price) = Demand(price)

At that intersection:

* Price → MCP
* Quantity → MCV

So MCP depends on:

* Purchase Bid
* Sell Bid
* System constraints
* Expected demand
* Generator availability

---

# 6. Modeling Interpretation

For forecasting MCP, dataset variables act as:

Inputs (features):

* Past MCP values
* Purchase Bid
* Sell Bid
* MCV / Volume
* Time Block (seasonality)

Target:

* Future MCP values (next‑day 96 blocks)

---

# 7. Time‑Series Properties of MCP

Electricity price series shows:

* Daily seasonality (96‑block cycle)
* Peak hours (morning/evening)
* Night troughs
* Price spikes (scarcity)
* Nonlinear response to bids

Implication:

Neural networks are suitable due to nonlinear mapping between bids, volume, and price.

---

# 8. Units Summary

* MCP → Rs/MWh
* Purchase Bid → MW or MWh
* Sell Bid → MW or MWh
* MCV → MW or MWh
* Final Scheduled Volume → MW or MWh

(Confirm dataset uses consistent unit convention.)

---

# 9. Role of Dataset in Project Pipeline

Dataset supports:

1. Lag feature creation
2. Multivariate forecasting
3. Cascaded neural network inputs
4. Evolutionary optimization targets
5. Evaluation against baselines

---

# 10. Quick Reference Table

| Column                 | Meaning            | Market Role         | Modeling Role |
| ---------------------- | ------------------ | ------------------- | ------------- |
| Date                   | Delivery day       | Time index          | Sequence      |
| Hour                   | Hour index         | Seasonality         | Feature       |
| Time Block             | 1–96 interval      | Daily cycle         | Feature       |
| MCP                    | Clearing price     | Market outcome      | Target        |
| Purchase Bid           | Demand volume      | Demand pressure     | Input         |
| Sell Bid               | Supply volume      | Supply availability | Input         |
| MCV                    | Cleared quantity   | Balance point       | Input         |
| Final Scheduled Volume | Scheduled dispatch | Realized volume     | Input         |

---

# 11. Key Concept Summary

* Electricity DAM clears per 15‑min block
* MCP is intersection price of supply & demand
* Bids determine price dynamics
* MCP shows strong daily seasonality
* Forecasting = mapping past market state → future MCP curve

---

**End of dataset definitions**
