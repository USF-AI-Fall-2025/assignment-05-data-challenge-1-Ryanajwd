# x62-data-challenge-student-pathways

●Data quality: For each feature (column), what is the data type? Is there any missing
data?
- The dataset mixes categorical and numeric columns. Most features like “DISTRICT_TYPE,” “DISTRICT_NAME,” “DEMO_CATEGORY,” “STUDENT_POPULATION,” and “AWARD_CATEGORY” are object type, while “DISTRICT_CODE” and the wage columns are numeric (float64). There are about 2,745 missing values in “DISTRICT_CODE,”. Each wage column (WAGE_YEAR1–4) has around 17,770 zeros, which make up roughly 85% of all rows. These zeros probably represent missing or unreported income rather than actual zero earnings, and no other columns contain missing data. Overall, the dataset is usable but due to the large number of zero wages, it could limit how well the model learns real salary patterns.


●Range: What are the unique values for each categorical column? What is the range of
values of the numeric columns? Are the numeric column values normally distributed?

- The categorical columns include a small set of repeating values. For example, “DISTRICT_TYPE” includes School District, Legislative District, and All. “DEMO_CATEGORY” includes Race, Gender, Foster Status, and Homeless Status, while “STUDENT_POPULATION” represents groups like White, Black or African American, Hispanic or Latino, Male, Female, and others. “AWARD_CATEGORY” includes Associate Degree, Bachelor’s Degree (Transferred and Did Not Transfer), and Community College Certificate, etc. The numeric wage columns range from 0.0 to roughly 150,000, but the median for each year is 0.0, meaning most respondents had no reported income while a smaller number earned much higher wages. This creates a heavily right-skewed distribution rather than a normal one, with a long tail of high earners and most data clustered near zero.


●Semantics: What is the meaning of the columns? Are any columns related to other
columns? (If so, how?)

- Each column describes a different part of the dataset’s structure. “DISTRICT_TYPE,” “DISTRICT_NAME,” and “DISTRICT_CODE” identify the school or legislative district. “ACADEMIC_YEAR” marks the time period, which is 2018–2019 for all rows. “DEMO_CATEGORY” and “STUDENT_POPULATION” describe the type of demographic group represented, and “AWARD_CATEGORY” shows the type of degree or certificate earned. The wage columns (WAGE_YEAR1–4) represent the median annual wages for that group one to four years after graduation. These columns are related in a hierarchy: the wage values depend directly on the degree type and indirectly on demographic category. There is also a trend across wage columns, WAGE_YEAR1 -> WAGE_YEAR2 -> WAGE_YEAR3 -> WAGE_YEAR4 showing that most groups see gradual wage growth over time. Meanwhile, district-related columns link those wages to specific geographic or institutionas, providing the framework for comparison across the dataset.

REFLECTION
- The model performed best when using features like degree type, demographics, and prior-year wages, since those have the strongest influence on predicted earnings. Higher degrees, especially “Bachelor’s Degree, Did Not Transfer,” generally led to higher predicted fourth-year wages. The model’s performance was within the expected range, and shows that a linear regression was effective given the data. To improve accuracy, adding new features like cost of living by district, employment sector, or GPA could provide a more realistic view of how different factors affect post graduation wages.