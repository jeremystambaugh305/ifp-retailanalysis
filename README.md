# ifp-retailanalysis

**Project XYZ** 

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
'Stores.csv'

The company runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. I believe this set of holidays only occurs in the USA, so I assume this is a business operating in the USA.

'sales data-set.csv' is by far the largest dataset. It comprises 5 columns and 421,570 rows of date. For each of the 45 stores and each department within each store, it appears to contain a date for each week from 05/02/2010 to 26/10/2022 (range and completeness to be confirmed (TBC) during data transformations), a number under a column called 'Sales' and whether or not each date is a holiday or not.

'Features data set.csv' is smaller containing only 8,190 rows but more columns (12) with data on various dates (apparently weekly from 05/02/2010 to 26/07/2013 TBC) for each of the 45 stores, each spanning all departments. One reason (probably the main reason) the dataset has so many less rows than the sales dataset is that it is not broken down by department for each store. As with the stores dataset there is a column indicating whether or not the date was a holiday, but it also contains numberical data in 5 markdown columns and on temperature, fuel price, CPI, and unemployment.

'stores data-set.csv' is a relatively small dataset with 45 rows and 3 columns containing the type (a letter) and store size (a number) for each of the 45 stores.

None of the number headings show the units making it a little difficult to understand what they represent.  I can only assume at this stage that the numbers in the sales dataset column 'weekly_sales' and in the features dataset columns 'MarkDown1-5' are all absolute US dollar amounts.  At first glance, there appear to be too many of the latter to be percentages.

## Business Requirements
* Data analysis goals: Analyse retail sales data to identify trends, insights, and the impact of promotional markdowns on sales. Provide comprehensive, visually appealing sales reports and insights to assist in strategic decision-making.


## Hypothesis and how to validate?
* List here your project hypothesis(es) and how you envision validating it (them) 
My initial hypotheses (to be tested by data analysis) are

1. I expect sales increase most significantly during markdown periods.
2. I expect from the Kaggle description that most markdowns are in the lead up to national holidays.
3. I expect unemployment to have the next most significant impact on sales.
4. I doubt if other parameters in the features dataset have such a significant impact on sales but will assess their correlation to see.


## Project Plan
* Outline the high-level steps taken for the analysis.
* How was the data managed throughout the collection, processing, analysis and interpretation steps?
* Why did you choose the research methodologies you used?

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