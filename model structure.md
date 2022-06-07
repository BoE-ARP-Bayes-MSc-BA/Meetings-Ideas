## Jun 8 Meeting Agenda


### The dataframw we would get after pre-processing:

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
