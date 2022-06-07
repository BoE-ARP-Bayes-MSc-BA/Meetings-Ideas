# Jun 8 Meeting Agenda
1. discuss the different grouping to see whether it's appliable like below (seperated by region):
<img width="1022" alt="Screenshot 2022-06-07 at 3 40 44 PM" src="https://user-images.githubusercontent.com/61338647/172408809-9c39da5e-f6db-4d6c-8108-e488c227a006.png">
<img width="1025" alt="Screenshot 2022-06-07 at 3 42 52 PM" src="https://user-images.githubusercontent.com/61338647/172409312-3fe0dbcb-3d96-4c69-8e3c-62cb941c00a9.png">
2. Clarify the goals and expectations from BoE in term's of findings/deliverable in the project, from us (do you think we could ask another meeting with the partner)  
3. the big picture of model plan is provided as below (including questions):
    - exact date extracting & information loss
    - Future Risk output
    - if the whole (benchmarking) model is robutness
4. Concern about complexity of the project -- Computational & time. 

## Inputs
- Earning’s Call transcripts for each insurer
    - 2011-2021
    - PDF format
- Stock price for each insurer
    - Daily
*currently we didn't take news, bond interest and inflation rate (to denoise the stock price) into considerationm, but if time premit we could*
    
## Pipeline
### The PDF-transformed dataframe we would get after pre-processing:
1. Note that the participant and participant_title will extract from the whole meeting and give the label of eaach sentences (just like method 2: Topic Modelling does)
2. note that the PDF format is not consistent, so if participant_title is not shown, would us the frequency of the participant shown in the meeting to replace
3. Currently would only doing on the Python as dataframe to test on a small MVP, but the whole dataset would using database to manage
4. the data-cleaning part could be seen inside the [repo](https://github.com/BoE-ARP-Bayes-MSc-BA/data_collecting)

#### Mthhod 1: Find Date & Time (*with specific sentence*)
1. will seperate the sentences by the stopping words (especiallly dot)
  - e.g “Last quarter…”, “In January…”
  - Extract only sections where dates are mentioned (Possible information loss?)
2. the issue of the date: 
  - different speaking style
  - what if it's only year or month but not the exact date?
3. if finding the exact issue happening date & time:
  - would link to the stock market change of the day
  - measuring the impact of at that moment and the duration of before and after impact on price

| **group** | **nompany_name** | **sentence** | **participant** | **participant_title** | **date_time**|
|-----|-----|-----|-----|-----|-----|
| European (Re)Insurers | HNR1 GY | Well 2014 for us was quite a good year, I would say. As you can see, we managed to increase the after-tax earnings of the group by more than 10%, and as this has been driven by strong underlying earnings from all segments, so that we could continue with our rather conservative policy when it comes to the reserves, be it on the P&C side or be it on the Life & Health side. | Ulrich Wallin | CEO | 2014/01/01|
| ...... | ...... | ...... | ...... | ...... | ...... |
  
#### Mthhod 2: Topic Modelling (*with all the meeting*)
1. would be like the relevant topic that shown as in the Bloomberg Terminal:
  - but we could control how many are the topics (to be general like 10 topics or 80 topics)
  - e.g CSR Concerns, Market Share, Rates, etc.

#### Mthhod 3: Sentiment Analysis (*with specific sentence*)
1. concern/outlook over each sentence
2. could see the file in the [repo](https://github.com/BoE-ARP-Bayes-MSc-BA/Model)

| **sentence** | **topic** | **sentiment_score** | **stock_price_change** |
|-----|-----|-----|-----|
| Well 2014 for us was quite a good year, I would say. As you can see, we managed to increase the after-tax earnings of the group by more than 10%, and as this has been driven by strong underlying earnings from all segments, so that we could continue with our rather conservative policy when it comes to the reserves, be it on the P&C side or be it on the Life & Health side. | Life & Health | +1 | +3 |
| ...... | ...... | ...... | ...... | ...... | ...... |

### Apply data to the model
Relationship between topic & sentiment and Stock Price 
    - Time-specific if date-time is available
    - Regression
    
### What we want to discover:
![WhatsApp Image 2022-05-31 at 6 27 58 PM](https://user-images.githubusercontent.com/61338647/172404147-2faa065c-f017-42d6-b599-35a218c4582c.jpeg)
1. Sentiment Analysis
    - each topic will be repesente by groups and to see those topic's sentiment score sum
2. Common (Previously) Risk
    - using regression to see if that's significant or not 
    - with the x of sentiment score and y of stock price changing
    - each sentence with the sentiment score & exact date time will be the datapoint
    - would also take the frequency of topic into consideration (is it important for the company and the market)
3. Future Risk
    - Topic Importance and Across groups, year
    - will visualize it and detect the trend 
    - should we built the model or any method we could use for prediction?


## Research 
[➡️  notion Page](https://www.notion.so/matheusmaciel/Research-Summary-and-Guide-9ef62d43d95d4f2e96ed269049c85d50)


[****An Exploratory Study of Stock Price Movements from Earnings Calls****]([https://www.notion.so/Doing-Well-by-Talking-Good-A-Topic-Modelling-Assisted-Discourse-Study-of-Corporate-Social-Responsib-9fdd249c34014370b347d6cf81ff9aec](https://tinyurl.com/27jdd4fn))

[****Doing Well by Talking Good: A Topic Modelling-Assisted Discourse Study of Corporate Social Responsibility****](https://www.notion.so/Doing-Well-by-Talking-Good-A-Topic-Modelling-Assisted-Discourse-Study-of-Corporate-Social-Responsib-9fdd249c34014370b347d6cf81ff9aec)

[****Sentiment Analysis for Trading with Reddit Text Data****](https://www.notion.so/Sentiment-Analysis-for-Trading-with-Reddit-Text-Data-51fcccc0c425487b842a56d719b65bc6)

[Textual Analysis of Stock Market PredictionUsing Breaking Financial News: The AZFinText System](https://www.notion.so/Textual-Analysis-of-Stock-Market-PredictionUsing-Breaking-Financial-News-The-AZFinText-System-fafc1ebe64f04a749837c92c851fa14c)

[NLP for Stock Market Prediction with Reddit Data](https://www.notion.so/NLP-for-Stock-Market-Prediction-with-Reddit-Data-b9cf4fb634d54a39b699cc7629090e54)

[Big Data and Machine Learning in Quantitative Investment](https://www.notion.so/Big-Data-and-Machine-Learning-in-Quantitative-Investment-57895c9d0bb24c5fb4a5365ae83d1a74)

[Analyst Information Discovery and Interpretation Roles](https://www.notion.so/Analyst-Information-Discovery-and-Interpretation-Roles-51c2b9e8883e4bd2947cf865fb9f560a)

[Natural language based financial forecasting: a survey
](https://www.notion.so/Natural-language-based-financial-forecasting-a-survey-7db2d987f5e24ba29ceffb5a46ef4b61)

[Deep Learning for Stock Market Prediction Using Event Embedding and Technical Indicators
](https://www.notion.so/Deep-Learning-for-Stock-Market-Prediction-Using-Event-Embedding-and-Technical-Indicators-92be960c68ab481da952824e20e1f14e)







