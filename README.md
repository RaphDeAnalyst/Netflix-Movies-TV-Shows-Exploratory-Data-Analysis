# Netflix Movies & TV Shows Exploratory Data Analysis (EDA)

## Introduction

## About the Dataset

For this pet project, Netflix movies and TV shows data was used and it was acquired from [here](https://raw.githubusercontent.com/kedeisha1/Challenges/main/netflix_titles.csv), since it was not downloadable, I copied and pasted it in notepad, saved it as a csv file then later converted it to an excel document. I have equally uploaded the xlsx file for download.

#### *From here onwards Tv shows and Movie will be collectively referered to as shows*

## Data Description
Originally, this dataset consisted of 8810 rows and 12 columns, the column names are listed and described below;

1. show_id: Holds unique id of each show
2. type: Contains the category the show falls in either TV shows or Movies
3. title:  Name of the show
4. director: Name of the direstor of the show
5. cast: Name of actors and actresses in the show
6. country: Countries where the show is available to watch on Netflix
7. date_added: When the show was added to Netflix
8. rating: Show's rating on Netflix
9. released_year: The year the show was released
10. duration: Time duration of the show
11. listed_in: Genre of the show
12. description: Summary of the show

## Aim of this Project

Netflix is one of the leading media-streaming and video-rental company, Netflix also produces and acquires exclusive right to many movies and TV shows. This project was born out of my curiosity to answers some lingering question which includes but not limited to:

1. Understanding the top demographics where netflix movies are predominantly produced
2. Determining what kind of shows Netflix fouses on mostly
3. To determine what kind of shows (based on rating) is more popular on Netflix.

*Non-programming tool; Microsoft Excel and Power BI were used for this project*

## Data Transformation

This process includes, identifying incorrect data type, finding missing values and dealing with them accordingly, modifying, removing or replacing irrelevant data and creation of extra columns and tables.

### Handling duplicate values
There was no duplicate values in this dataset

### Handling missing values

I realized that this dataset contains 4331 missing values by using the countif function in excel =COUNTIF(TableName, ""), since I had to handle this before proceeding with the analysis, removing the empty cells would result in losing a significant amount of the data, therefore, I filled the missing values with N/A across all affected cells using excel's find and replace field. I then moved the dataset to Power Query,

### New tables

▪️ Because, I needed to get the count of individual genre in the listed_in column, since multiple genres are combines in one cell. 
In order to determine the number of times they appear in the dataset, I used the following steps to do this:
1. I duplicated the main table;
2. Removed other column leaving only "listed_in";
3. Split the column by delimiter ",";
4. Highlited the columns created and then unpivoted them;
5. Renamed the columns (Words) and the table (IndividualWords);
6. Applied the changes and loaded into Power BI;
7. In Power BI, I created a measure to count all the rows in the table using the DAX formula:	WordCount = COUNTROWS(IndividualWords), before creating visuals.
    
This same steps where applied to the country and cast columns to get the individual countries and actors respectively.

▪️ rating group: In the original table, the rating column contains rating for each shows in codes, using DAX formulas I grouped the ratings respectively using the switch funtion. the code I used is shown below:

rating group = SWITCH(
    TRUE(),
    Lookup_rating[rating] = "PG-13", "Teens",
    Lookup_rating[rating] = "TV-MA", "Adults",
    Lookup_rating[rating] = "PG", "Older Kids",
    Lookup_rating[rating] = "TV-Y", "Kids",
    Lookup_rating[rating] = "TV-14", "Teens",
    Lookup_rating[rating] = "R", "Adults",
    Lookup_rating[rating] = "TV-PG", "Older Kids",
    Lookup_rating[rating] = "TV-Y7", "Older Kids",
    Lookup_rating[rating] = "TV-G", "General",
    Lookup_rating[rating] = "G", "General",
    Lookup_rating[rating] = "NC-17", "Adults",
    Lookup_rating[rating] = "N/A", "No Rating",
    Lookup_rating[rating] = "NR", "Adults",
    Lookup_rating[rating] = "TV-Y7-FV", "Older Kids",
    Lookup_rating[rating] = "UR", "Adults"
)

### New columns

New columns where created from the date_added column in order to derive more meanig from the data
▪️ month_added and year_added was extracted from the data and time column under the transform tab.

## EDA and Visualization

#### Shows distribution by category
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/0c1a3654-a3af-4bd1-8df0-f785f14b7a8d)

#### Top 5 countries by number of shows for streaming
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/cef9023e-f1a7-4fd6-953b-a9ab3bde0445)

#### Top 5 most popular genre
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/2e14a7d9-0947-4916-a52d-17504b3eccfd)

#### Top 5 years by shows added
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/89c481de-7893-43f2-95d2-77354bc8b823)

#### Top 10 years by shows released
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/f02d6827-eba8-4a09-b008-749f8217e6e1)

#### Shows count by rating
![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/8a75260f-d34e-4232-a64d-68f419e05a5d)

#### The full dashboard is shown below

![image](https://github.com/RaphDeAnalyst/Netflix-Movies-TV-Shows-Exploratory-Data-Analysis/assets/76891015/247e987d-2ed3-4bb5-b0e0-43b1df8aecbe)

## Key Findings
1. Movies was the most popular shows on Netflix
2. Netflix released the highest numbers of shows in 2018
3. United States had the highest number of shows produced
4. Netflix produces adult shows morw
5. The most important genre on Netflix
6. Overall, Netflix has more Tv shows with only one season duration; this could be due to cancellation of the show, on category levels, one season is more for TV shows and 90 minutes has more content for movies

## Conclusion

Working on this project has been an eye opener for me, due to the magnitude of work carried out on this data, it has expanded my analytical skill and has boosted my confidence level in handling complex dataset. Hopefully, in the future further analysis would be carried out on the project and this readme file updated 😊

I have provided the neccesary files including the data used for the analysis.





 

