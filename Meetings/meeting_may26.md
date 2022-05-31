# Meeting 1

# Reseach

- ***Theory***  behind language analysis in financial markets (not just NLP / tech)
- ***NLP-Specific*** analysis together with the theory can give interest insights that can help us create a model
    - E.g: Negative language in finance is often written in ways that are more complicated than positive news
    - The use of financial-specific word banks for NLP is shown to be more effective than general word banks (pre-trained data)
    - Identification of risks during a time-period
    - Impact of language on stock price can be either defined as just up/down movement or specific % changes

# Modelling

- Use of Bond prices can de-noise some of the stock price movements
- Using just stock price & language relationship can be hard to explain if language is truly having an impact (since stock price movements can be due to a multitude of different factors)
- We could try to show time-specific risks
    - *Points to note*: we’d rely on time periods being mentioned within the reports
- Bloomberg (our data source for transcript) already does some NLP and identifies different issues mentioned in the reports. We’d need to try to gather it somehow
- Re-group firms to better identify types of risk - using news could help us identify external risks more easily in each region or country
- Political risk rankings time series
    - S&P, Moodys, Fitch, MSCI

# Inputs & Outputs

**Input** 

- Earnings calls
- Bond interest rate
- news titles
- country risk

**Output**

- % change on stock (up or down)
- type of risk (topic)