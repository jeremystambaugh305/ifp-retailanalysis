# ifp-retailanalysis

Is my individual formative project carried out on 13-14Aug 2025 as part of the Code Institute Data Analysis and AI Bootcamp.

The project repository is located here 
https://github.com/jeremystambaugh305/ifp-retailanalysis

and the project planning is located here
https://github.com/users/jeremystambaugh305/projects/4

Context

The challenge involves making decisions based on limited historical data, particularly around holidays and promotional events. The dataset includes historical sales data for 45 stores in different regions, with details about store types, sizes, and promotional markdowns.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)


## Dataset Content
*  Datasets were obtained from 
https://www.kaggle.com/datasets/manjeetsingh/retaildataset 
comprising 3 datasets 
These datasets comprise the following 3 csv files which contain data on historical sales data for 45 stores located in different regions - each store contains a number of departments. 
'sales data-set.csv'
'Features data set.csv'
'Stores data.csv'

To repove potential vscode errors in reading these files, I renamed them replacing spaces with uncerscores i.e., naming the files as below:-

'sales_data-set.csv' (I refer to this as the sales dataset from now)
'Features_data set.csv' (I refer to this as the features dataset from now)
'Stores_data.csv' (I refer to this as the stores dataset from now)

The company runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. I believe this set of holidays only occurs in the USA, so I assume this is a business operating in the USA.

Then sales dataset is by far the largest. It comprises 5 columns and 421,570 rows of date. For each of the 45 stores and each department within each store, it appears to contain a date for each week from 05/02/2010 to 26/10/2022 (range and completeness to be confirmed (TBC) during data transformations), a number under a column called 'Sales' and whether or not each date is a holiday or not.

The features dataset is smaller containing only 8,190 rows but more columns (12) with data on various dates (apparently weekly from 05/02/2010 to 26/07/2013 TBC) for each of the 45 stores, each spanning all departments. One reason (probably the main reason) the dataset has so many less rows than the sales dataset is that it is not broken down by department for each store. As with the stores dataset there is a column indicating whether or not the date was a holiday, but it also contains numberical data in 5 markdown columns and on temperature, fuel price, CPI, and unemployment.

The stores dataset is a relatively small dataset with 45 rows and 3 columns containing the type (a letter) and store size (a number) for each of the 45 stores.

Whilst appreciating the values within columns can be incomplete and/or contain errors, none of the column headings include units, making it impossible to understand what the numbers represent without guesswork.  I could not find this information within the source Kaggle website.

I have assumed that the numbers in the sales dataset column 'weekly_sales' and in the features dataset columns 'MarkDown1-5' are absolute US dollar amounts.  The MarkDown numbers are too large to be percentages.  I initially assumed the size columns in the Stores dataset are total annual dollar turnover but the lack of correlation with total sales suggests this may be another parameter e.g. floor area.

In real life I would immediately seek clarification from the client rather than guessing. As the owner of the data and given the importance of understanding the precise meaning of each dataset column, they should be in a position and happy to provide it.

## Business Requirements
* Data analysis goals: Analyse retail sales data to identify trends, insights, and the impact of promotional markdowns on sales. Provide comprehensive, visually appealing sales reports and insights to assist in strategic decision-making.


## Hypothesis and how to validate?
* List here your project hypothesis(es) and how you envision validating it (them) 
My initial hypotheses (to be tested by data analysis) are

1. I expect sales to increase most significantly during markdown periods.
2. I expect from the Kaggle description that most markdowns are during or in the lead up to national holidays.
3. I expect unemployment to have the next most significant impact on sales.
4. I doubt if other parameters in the features dataset have a significant impact on sales but will assess their correlation to see.


## Project Plan
* Steps taken for the analysis:-

1. I set up a GitHub repository for this project at the URL above, making it public 
2. Used the Code Institute GitHub repository template to generate a repository within my repository.
3. Cloned the Github repository to vscode
4. Created a subdirectory for data <Dataset/Raw>
5. Downloaded the datasets (3 csv files) from the Kaggle source website as a Zip folder, extracted  the 3 files with Winzip, renamed them replacing spaces with underscores and dragged them from Windows Explorer to the Dataset/Raw subdirectory within vscode.

Within vscode:-

6. Copied the template Jupyter notebook <Notebook_Template.ipynb> and named the copy <ETL.ipynb> which I later copied and renamed <ETL2.ipynb> due to problems with internet connection dropouts and file size, deleting the old version.

Carried out all analysis within this one Jupyter notebook <ETL2.ipynb> using python code and Markdown narrations to:-

Section 1:-

7. Import all necessary Python Libtaries (NumPy, Pandas, MatPlotLib etc.)
8. Reset display max rows and columns to default after expanding in subsequent steps for readability and file size minimisation.
9. Read the csv files into dataframes and display basic summary .info() on data types and null counts and note my observations in Markdown cell.  
Key finding:-Many nulls in features dataset (mainly MarkDown columns) but other datasets complete.

Section 2:-

10. Aggregate total weekly_sales from sales dataset converting to millions, make copy of stores dataset with suffix _T to distinguish from raw dataset, add aggregated weekly_sales column, summarise and assess correlation of total sales vs store size by store type.

Key finding:-No strong correlation of sales vs store size, negative in fact for store types B and C which seems counterintuitive indicating other factors more strongly affect sales.

Hindsight:-I should have checked weekly_sales data date counts for each store to check for consistency.  I did do later and found some small discrepancies which seem very unlikely to materially change lack of correlation, but I would take account of this here if revising.

11. Reformat dates in the sales and features datasets using the datetime function and the format='Mixed' and dayfirst=True arguments as the dtype in the sales and features raw dataset date column is string but implying not all strings are in a consistent format which can be inferred by the datetime function without the 'Mixed' argument. Most appear to be in UK dd/mm/yyyy format as observed in heads and tails and explained further above so the dayfirst='True' argument applied.  Sort in ascending order and read into new sales and features datasets suffixed _T to distinguish from original datasets.

Future improvement:-With more time I would find records where strings not in a format which datetime function can pick up without the format='Mixed' argument and check they have been interpreted correctly.

12. Tabulate basic statistical summary of MarkDown columns using .Describe function.

Key findings-numbers are generally well>100 implying these are not percentages. Guessing they are dollar amounts.  Minimum values are negative which seems anomylous but unable to confirm without understanding what MarkDowns are.

Future improvement:-would check with data holder what MarkDowns mean and replace negative values with Nulls if they are anomalies as I suspect.

Hindsight:-would have tried replacing negative MarkDown values with Nulls and assessing impact of doing so on correlation with weekly_sales.

13. Research when holiday periods occur to anticipate when markdowns can be expected.  As below the subsequent analysis shows there is data in MarkDown columns throughout the year so conclude no clear relationship but I retained the researched information in case useful for refinement.

14. Add Year and Monthno columns to transformed features dataframe using the .dt.year and dt.month functions on Date column, and a MarkdownOn column which =True if there is non null data in any of the 5 MarkDown columns.  Obtain a count of features records grouped on Year, Monthno, MarkDownOn, and IsHoliday sorted in ascending date order to see patterns of Markdown vs holiday timing.  

Key findings:-I observed many markdowns are outside holiday periods so conclude no clear relationship.

14. Merge processed sales and features dataframes with sales left and features right using an outer join on 'Store' and 'Date' columns sorted on 'Date, Store, Dept to create a new dataframe called 'df_salesfeaturesmerged'  Generates 423325 rows compared with 421570 in the original sales dataset indicating some dates are present in the features dataset and not the sales dataset.

To test, I merged the dataframes with features left and sales right and this results in same number of rows as I'd expect before reverting the order to the above and rerunning.

15. As a test, enumerate the non null counts for the merged dataset sales and MarkDown columns.  

Key findings:-I see again the non null data is in line with observations above with Markdown data from Nov 2011 onwards but also that the monthly non null counts are significantly lower from Nov 2012.

16. Assess correlations for weekly sales against other variables in salesfeatured merged dataframe in each calendar year using a correlation matrix.

Key findings:-No strong correlations between sales and any other variables including MarkDowns.

* Why did you choose the research methodologies you used?

I assessed correlation of store size with total annual sales to try to understand if 'size' is likely to be annual turnover but the lack of correlation with total sales suggests this may be another parameter e.g. floor area.

I converted sales and features dataset dates to datetime format to facilitate accurate timeline analysis and joining of dataset.





## The rationale to map the business requirements to the Data Visualisations
* List your business requirements and a rationale to map them to the Data Visualisations

## Analysis techniques used
* List the data analysis methods used and explain limitations or alternative approaches.
* How did you structure the data analysis techniques. Justify your response.
* Did the data limit you, and did you use an alternative approach to meet these challenges?
* How did you use generative AI tools to help with ideation, design thinking and code optimisation?

## Ethical considerations
* Were there any data privacy, bias or fairness issues with the data?
* How did you overcome any legal or societal issues?

## Unfixed Bugs
* Please mention unfixed bugs and why they were not fixed. This section should include shortcomings of the frameworks or technologies used. Although time can be a significant variable to consider, paucity of time and difficulty understanding implementation are not valid reasons to leave bugs unfixed.
* Did you recognise gaps in your knowledge, and how did you address them?
* If applicable, include evidence of feedback received (from peers or instructors) and how it improved your approach or understanding.

## Development Roadmap
* What challenges did you face, and what strategies were used to overcome these challenges?
* What new skills or tools do you plan to learn next based on your project experience? 


## Main Data Analysis Libraries
* Here you should list the libraries you used in the project and provide an example(s) of how you used these libraries.


## Credits 

* In this section, you need to reference where you got your content, media and extra help from. It is common practice to use code from other repositories and tutorials, however, it is important to be very specific about these sources to avoid plagiarism. 
* You can break the credits section up into Content and Media, depending on what you have included in your project. 

### Content 

- The text for the Home page was taken from Wikipedia Article A
- Instructions on how to implement form validation on the Sign-Up page was taken from [Specific YouTube Tutorial](https://www.youtube.com/)
- The icons in the footer were taken from [Font Awesome](https://fontawesome.com/)

### Media

- The photos used on the home and sign-up page are from This Open-Source site
- The images used for the gallery page were taken from this other open-source site



## Acknowledgements (optional)
* Thank the people who provided support through this project.