# Volatility Index Enabled Trading Alert System #

### Business Case ###
The world is living through its 2nd pandemic of 21st Century (first being 2009 H1N1 influenza pandemic). In midst of all this doom and stock market gyrations, one category of investors has stood tall and more often than not only beaten established mutual funds and hedge funds. More and more news headlines attest to this fact as we enter the 2nd half of 2020

As the current crises continues to increase volatility due conflicting progress against COVID-19 and a monumental Presidential election around the corner, its imperitive that small mom/pop trader better understand volatility and utilize cutting edge data science techniques to forecast expected volatility and incorporate these insights regarding volatility into stock-trading behavior

For most mom/pop investors focusing on investing in cyclicals like Technology stocks, valuations are increasing a function of sentiment and subject to 'substiantial' change when other sectors of the economy recover 

We have all heard the maxim - 'buy when other sell and sell when others buy'. One literal intrepration of this maxim would be to buy when others are fearful and panicking and sell when others are overly europhic and start buying

Clearly there is a use case for a volatility predictor which can used to improve 'entry' and 'exit' strategies  

While it is widely acknowledged that predicting asset prices is a perilous profession, I believe there maybe a workaround in trying to predict broader market volatility and explore if such insight can augment trading strategies in such times

### Associated Sub-theme (For Stretch Goal) ###

I also wanted to explore if investors experienced different levels of volatility under two Presidents and extract insights for a major upcoming event that will be 'cataclysmic' from a volatility standpoint - the 2020 Presidential Election - irrespective of who wins!


### Using Data Science to Demystify/Understand Volatility ###

While looking for data to best understand volatility for trading, I choose the CBOE Volatility Index (VIX) - VIX is widely acknowledged as the foremost indicator of implied market volatility for over 25 years

So what is the VIX? Its a real-time market index that represents the market's expectation of 30-day forward-looking volatility. VIX estimates how volatile the market will be by aggregating the weighted prices of S&P 500 puts and calls over a wide range of strike prices. More specifically, the VIX is calculated by looking at the midpoints of real-time S&P 500 option bid and ask prices

Why VIX - Unlike indiviual stocks in S&P500 (and associated option chains) which may be undergoing some structural realingment (GE & BOEING are classic examples), VIX is 'diversified' and 'balanced' number that most accurately estimates investor sentiment going into the future. Since VIX is derived from future price expectations for every stock on the S&P500, it accurately captures the hedging strategies of large institutional players - which in turn impacts current and future stock prices

Key Charateristic of Index - 'Long Term Mean Reversion' - Simply put folks dont stay fearful for too long nor do they remain euphoric all the time to whatever happens (Clearly investors could also benefit from learning Zazen and other zen meditation techniques but I'll save that for a later blog about how to maintain equanimity during 'high-volatility' trading sessions)

Another important 'lesser' charateristic is that VIX has a strong negative correlation to the S&P 500, tending to rise when the stock market dives, and vice versa, and as such futures based on the VIX, traded at the CBOE (retail buyers hardly use CBOE since its been designed for large institutional investors), can be an effective vehicle for hedging stock market positions 

### Steps to Solutioning ###

1. Data Gathering - I webscraped 2517 observations for daily adjusted closing prices of VIX starting '2010-06-23' to '2020-06-24' to build the volatility predictor. gathered data was stored in a 'pickle'. 

2. Data Pre-processing - Use of datetimestamp and index

3. Exploratory Data Analysis - Used to identify suitable 'transformations' of data for modeling purposes 

4. Model Development and Evalution Criteria (RMSE)
    1. Baseline - Persistence Model
    2. Facebook Prophet 
    3. ARIMA
    4. LSTM (for final presentation)

5. Choice of Preferred Predictor Explained - the best performing model is the baseline - Persistence Model with a RMSE of 3.34 - hard to explain but I'm hoping the LSTM can outperform the baseline model  

### Key Findings about the VIX ###
1. Mean ~ 17 with Standard Deviation - ~7
2. Highest recorded value - ~82 (March 2020 - peak of market meltdown in response to Covid19 lockdown)
3. End of Q1 & Q2 seen most volatility - End of a critical Q2 is upon us!!!
4. Elections (We have a big one coming up) result in a spike in volatility 
5. Relative rate of change in volatility needs to factored in building models that use short term change in VIX to predict  

### Future Steps ###

Each VIX index value represents an implied annual volatility for the S&P500. So a VIX of 16 implies an annual implied change (up or down) of 16% in the S&P

For a day trader/scalper/swing trader, this 16% implied annual volatility remains instrutable however when converted into a daily implied movement of ~1 % (16/sqrt(252)), things start to make sense. At a higher VIX, scalpers can look to make anywhere from 1-5% returns (provided they make the right picks of course) 

I aim to fine-tune the predictor and identify critical thresholds that can serve as 'triggers' for traders (subscribing to my app). Alerts would be generated when 'relative' volatility changes help identify start of high 'fear' cycles aka buying opportunities and low 'fear' cycles aka sell high and sit on cash 

The END GOAL - use VIX to 'directionally' predict which way the market is going (of course in the short run) so traders can factor in VIX into decision making

To conclude:

“My interest is in the future…I am going to spend the rest of my life there”
– C.F. Kettering

### Links to Presentation & Academic Literature 
Presentation - https://docs.google.com/presentation/d/1ZFODWgJR_lD_ECELpOK0WLRsaTyFbnwPVT3cFBHadls/edit?usp=sharing

Articles Reviewed  
1. General Overview 
- https://www.spglobal.com/spdji/en/education-a-practitioners-guide-to-reading-vix.pdf
- https://www.investopedia.com/ask/answers/010915/volatility-good-thing-or-bad-thing-investors-point-view-and-why.asp
- https://ftalphaville.ft.com/2018/02/28/1519839805000/An-abridged--illustrated-history-of-volatility/

2. Weakness - https://www.barrons.com/articles/the-pros-and-cons-of-vix-the-markets-fear-gauge-1505942074


### Sources for Code, Images etc ###

Learn Lessons on Time Series Forecasting & Modeling  
Baseline - Persistence Model - https://machinelearningmastery.com/persistence-time-series-forecasting-with-python/
GridSearch - Arima Hyperparamter tuning - https://machinelearningmastery.com/grid-search-arima-hyperparameters-with-python/
TimeSeries Forecasting 
https://www.machinelearningplus.com/time-series/arima-model-time-series-forecasting-python/
Cross-Validation of ARIMA - https://alkaline-ml.com/pmdarima/auto_examples/model_selection/example_cross_validation.html
Images for deck - Google Images Search 

