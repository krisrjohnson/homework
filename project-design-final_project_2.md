# Project Design Writeup and Approval Template

Follow this as a guide to completing the project design writeup. The questions for each section are merely there to suggest what the baseline should cover; be sure to use detail as it will make the project much easier to approach as the class moves on.

### Project Problem and Hypothesis
* What's the project about? What problem are you solving?
	The project is predicting Zillow home sale price logerrors from Oct through Dec 2016 for three California counties based on Zillow data for Jan-Sep 2016. I'm solving what features have high accuracy in predicting sale price through the log error.
* Where does this seem to reside as a machine learning problem? Are you predicting some continuous number, or predicting a binary value?
	I'm predicting a continuous number. As far as machine learning, this resides in the multivariate linear regression area. The standard statistical predicting future data based on past data.
* What kind of impact do you think it could have?
	The goal is to attain higher accuracy for home prices, which will allow home owners to better understand the underlying value in their home. As well as what features could possibly add outsize value (such as a hot tub or fireplace). Also, housing price estimates have very real affects on existing home owners, including a property down the street selling for less than expected resetting all near by house's prices.
* What do you think will have the most impact in predicting the value you are interested in solving for?
	My assumption is the basic square footage and number of bedrooms and bathrooms have the largest impact in predicting sales price, so are likely already highly mined. As well as location to a lesser extent. This means the impact of less common features to Zillow's error rate on housing prices will likely be the areas with room for improvement.

### Datasets
* Description of data set available, at the field level (see table)
1. airconditioningtypeid           type of cooling system
2. architecturalstyletypeid        ranch, colonial, etc
3. basementsqft                    basement sq ft
4. bathroomct                      # of bathrooms
5. bedroomct                       # of bedrooms
6. buildingqualitytypeid           overall assessment of condition from best (lowest) to worst (highest)
7. buildingclasstypeid             building frame type (steel, wood, concrete/brick)
8. calculatedbathnbr               # of 3/4 bathrooms (shower+sink+toilet)
9. finishedfloor1squareft          sq footage of first floor
10. calculatedfinishedsquarefeet   calculated total finished living area of home
11. finishedsquarefeet6            base unfinished and finished area
12. finishedsquarefeet12           finished living area
13. finishedsquarefeet15           perimeter area
14. finishedsquarefeet50           sq footage first floor
15. fips                           federal information processing standard code - wikipedia.org/wiki/FIPS_county_code
16. fireplacecnt                   # fireplaces
17. fireplaceflag                  presence of fireplace bitflag
18. fullbathcnt                    # full baths
19. garagecarcnt                   garages including an attached garage
20. garagetotalsqft                garges sq footage
21. hashottuborspa                 has hot tub or spa
22. heatingorsystemtypeid          heating system
23. latitude                       lat of middle times 10e6
24. longitude                      lat of middle times 10e6
25. lotsizesquarefeet              sq footage of lot
26. numberofstories                # of stories
27. parcelid                       unique_id for parcels (lots)
28. poolcnt                        # of pools
29. poolsizesum                    sq footage of pools
30. pooltypeid10                   spa or hot tub
31. pooltypeid2                    pool w/ spa or hot tub
32. pooltypeid7                    pool without hot tub
33. propertycountylandusecode      county's zoning code
34. propertylandusetypeid          type of zoning
35. propertyzoningdesc             description of zoning uses
36. rawcensustractandblock         Census tract and block ID combined - also contains blockgroup assignment by extension
37. censustractandblock            Census tract and block ID combined - also contains blockgroup assignment by extension
38. regionidcounty                 county
39. regionidcity                   city
40. regionidzip                    zip
41. regionidneighborhood           neighborhood
42. roomcnt                        # of rooms
43. storytypeid                    type of floors - basement, main level, etc
44. typeconstructiontypeid         materials of home
45. unitcnt                        # of units (2=duplex, 3=triplex, etc)
46. yardbuildingsqft17             patio in yard
47. yardbuildingsqft26             storage shed/building in yard
48. yearbuilt
49. taxvaluedollarcnt              tax assessed value of parcel
50. structuretaxvaluedollarcnt     assessed value of structure on lot
51. landtaxvaluecnt                assessed value of lot
52. taxamount
53. assessmentyear
54. taxdelinquencyflag             property taxes for lot are past due as of 2015
55. taxdelinquencyyear             year for which unpaid taxes were due
* If from an API, include a sample return (this is usually included in API documentation!) (if doing this in markdown, use the javacription code tag)


### Domain knowledge
* What experience do you already have around this area?
	Little to no experience with the housing market. Unrelated to my field and I'm not a home owner.
* Does it relate or help inform the project in any way?
	Hopefully ignorance will remove biases!
* What other research efforts exist?
    * Use a quick Google search to see what approaches others have made, or talk with your colleagues if it is work related about previous attempts at similar problems.
    	There are walkthroughs of housing price predictions, likelihood a home owner is going to sell, explorations of the boston housing data set, etc, widely available. But since this is ultimately an exploration of Zillow's housing price model's errors there isn't a lot of existing public attempts.
    * This could even just be something like "the marketing team put together a forecast in excel that doesn't do well."
    	Zillow has an article from Sept 15 highlighting the competition, but not giving any technical info on internal improvements: https://www.zillow.com/blog/zestimate-220693/
    * Include a benchmark, how other models have performed, even if you are unsure what the metric means.
    	Zillow has an existing model that predicts price within 4.3% accuracy, the goal here is to identify any biases with the error rates it outputs. The competition is highest accuracy wins a million, so just hoping to find even a tiny iota.

### Project Concerns
* What questions do you have about your project? What are you not sure you quite yet understand? (The more honest you are about this, the easier your instructors can help).
	Which model to use and being able to accurately improve/tweak modeling. Data cleaning I do frequently, so not much concern there. Because of the massive amount of features (59 columns) my fear is an inability to tweak the model appropriately to fully capture the available features, which is where I believe the meat of this exercise is. Also not sure how I could combine two models, such as a classification model to id houses by some stratification, then a linear regression within that to more accurately predict within those strats.
	Don't understand all of the features, such as census tract and zoning. I'm assuming all these are residential and zip will properly capture both of those features.
* What are the assumptions and caveats to the problem?
	I assume two or three features will dominate price prediction - square footage, bedrooms, and bathrooms. The lesser features will hopefully yield the more nuanced interestinig insights, which will allow better error recognition of the Zestimates.
    * What data do you not have access to but wish you had?
    	Actual home price. Have the zillow logerror, since the goal of the kaggle competition is to incease the accuracy of the zillow estimate (zestimate). Housing prices are right skewed so Zillow uses a log error to normalize.
    	Could supplement with schools and some measure of family friendly. Maybe directly tie births to neighborhoods to eke out info like starter homes? And isolate the home buying sequence for growing or well to do families?
    * What is already implied about the observations in your data set? For example, if your primary data set is twitter data, it may not be representative of the whole sample (say, predicting who would win an election)
    	The data is fortunately largely self contained. The implicit assumption is house sale price is completely encapsulated within the features available. The time period covered is the previous year, which contains the black swan event of a Trump presidential win and resulting market spike, meaning the housing market is possibly inflated. Future black swan events are likely to be more negatively oriented (outside of tax cuts), meaning any model will likely overstate housing prices vs actual.
* What are the risks to the project?
    * What's the cost of your model being wrong? (What's the benefit of your model being right?)
    	Cost of inaccuracy is very literally cost - overpriced or underpriced directly affects buyers, sellers, possibly loan modifications, etc. If the Zillow estimates become the KBB of housing prices, then errors to Zillow models could affect every piece of the housing market. 
    * Is any of the data incorrect? Could it be incorrect?
    	There are NaN's in some instances that don't make sense. There are houses with 0 bedrooms and 0 bathrooms. 

### Outcomes
* What do you expect the output to look like?
	A multivariate linear regression model predicting the logerror for every property provided. A graph of the predicted logerror vs actual logerror will hopefully have the former closer to 0, meaning more accurate Zestimate.
* What does your target audience expect the output to look like?
	The model with plot of residuals.
* What gain do you expect from your most important feature on its own?
	Because the obvious features to predict housing price are probably heavily mined, hopefully a unique feature like fireplaceflag will yield an insight into Zillow's logerror. 
* How complicated does your model have to be?
	With the number of available features to tweak, model complexity can potentially be very high. I'm more of the simple is better mentality, so will likely bundle any features possible. As in, combine fireplace and hot tub into has_luxury_feature bit flag.
* How successful does your project have to be in order to be considered a "success"?
	Success will be median(abs(predicted logerror) < median(abs(zillow logerror)). A mega success would have (median abs(predicted_logerror)/median abs(zillow logerror)) < .75. Success can also be measured by Median Absolute Error. The public leaderboards have that around .064 for the top 100 spots, would be happy with .5?
* What will you do if the project is a bust (this happens! but it shouldn't here)?
	This seems very possible given the project here is to predict the predictions! Very possibly some of the minor features don't have much value in price predictions. If that's the case, I'll document all the different types of models I applied and why I didn't gain any advantage. Then I'll bluster for 10 mins?

