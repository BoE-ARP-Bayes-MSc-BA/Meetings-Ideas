# Jun 8 Meeting Agenda
1. discuss the different grouping to see whether it's appliable like below (seperated by region):
<img width="1022" alt="Screenshot 2022-06-07 at 3 40 44 PM" src="https://user-images.githubusercontent.com/61338647/172408809-9c39da5e-f6db-4d6c-8108-e488c227a006.png">
<img width="1025" alt="Screenshot 2022-06-07 at 3 42 52 PM" src="https://user-images.githubusercontent.com/61338647/172409312-3fe0dbcb-3d96-4c69-8e3c-62cb941c00a9.png">
2. discuss about the papers we've seen


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
#### 1. Sentiment Analysis
#### 2. Common (Previously) Risk
#### 3. Future Risk
4. Topic Importance 
    - Across groups, year










