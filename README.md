# DDS-CaseStudy1
Authors: Meredith Ludlow & Kito Patterson

This is a repository for Case Study 1.  Analysis was done on beer and brewery data to analyze alcohol content and bitterness levels in different types of beer. To see the project output in Github, please refer to the Case Study PDF file.  

Items in the Repository:  
Beer.csv - Data set of beers made in the US.  
Brewery.csv - Data set of breweries in the US.   
CaseStudy.Rmd - Rmarkdown file for the project code.     
CaseStudy.md - MD file for the output of the CaseStudy.Rmd file.   
CaseStudy.html - HTML file for the output of the RMD file.    
CaseStudy.pdf - PDF file for the output of the RMD file.   
MLudlowPP - Meredith Ludlow's Power Point presentation for the project.  
CaseStudy_files - A file containing the output graphs from the RMD file.  

Contributions to the project:  
Meredith Ludlow:    
  Wrote the code for the first three questions.  
  Wrote the Introduction and the answers and explanations to the individual questions.   
  Wrote the comments in the code chunks.  
  Wrote the READ.ME file.  
  
Kito Patterson:
  Wrote the code for questions 4 through 7.
  Wrote the code to an additional question on interest not included in the Case Study deliverable
  Wrote the Conclusion
  Contributed to READ.ME file

Codebook:  

#Raw Datasets 
Beers.csv: Contains a list of 2410 US craft beers 
Breweries.csv: Contains a list of 558 US breweries

##Tidy Data Table Process
Altered column names (Beers):
  Brewery_ID (original) -> Brew_ID

BrewsandBeers dataframe created by merging both Beers and Breweries 
dataframes ON Brew_ID.

Altered column names (BrewsandBeers):
  Name (original) -> BeerName
  Name (original) -> BrewerieName
  
Additional Tidy Column / Feature Creation
1.) StyleCategory - extracts last word from 'Style' column in BrewsandBeers dataframe.

Supporting R code
```{r echo=TRUE}
# Rename Brewerie_ID in Beers DF
colnames(Beers)[5] <- "Brew_ID"
# Merge data sets
BrewsandBeers <- merge(Beers, Breweries, by = "Brew_ID")
# Rename columns
colnames(BrewsandBeers)[2] <- "BeerName"
colnames(BrewsandBeers)[8] <- "BrewerieName"
# Create new column from the information in the Style variable
BrewsandBeers$StyleCategory <- word(BrewsandBeers$Style,-1)
```


Object Descriptions
Breweries - Data frame that contains the data form the Brewery CSV file.  
BreweriesPerState - Data frame that contains the number of breweries in each state.  
BpS - Histogram that displays the number of breweries in each state using the BreweriesPerState data frame.  
Beers - Data frame that contains the data from the Beer CSV file.  
BrewsandBeers - Data set that contains merged data from the Beers and Breweries data frames.  
na_counts - Data frame that contains the number of missing values for each variable in the BrewsandBeers data set.  
MedianByState - Data frame that contains the median ABV and IBU for each state from the BrewsandBeers data set.  
bp_ABV - Histogram of the median ABV for each state using MedianByState.  
bp_IBU - Data frame of the median IBU for each state using MedianByState.  
MaxABVState - Date frame that contains the maximum value of ABV and the state from the BrewsandBeers data set.  
MaxIBUState - Date frame that contains the maximum value of IBU and the state from the BrewsandBeers data set.  
sp - Scatter plot of ABV and IBU for the data in BrewsandBeers.  
StyleCategory_Counts - Data frame that contains the number of each style of beer arranged in descending order from the BrewsandBeers.  
btp - Histogram of the number of each style of beer in descending order from the StyleCategory_Counts data set.  

Link to Meredith Ludlow's YouTube video: https://www.youtube.com/watch?v=m68MuFXb5_g&t=1s  
