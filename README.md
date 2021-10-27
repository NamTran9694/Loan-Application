# Loan-Application
Problem Introduction
You will be working as a business with Hardy Business Loans (HBL), a hypothetical company that lends money to small businesses for small to medium sized equipment acquisitions. The borrower can be either the business itself or one or more of the business’s owners or partners. For example, Hardy might lend money to a restaurant for a pizza oven; in the case of a transportation company, it could be a tractor (truck).
HBL has recently acquired portfolios from “Beachside Lenders” and “Wilson & Sons” and their CEO would like for you to analyze whether or not their lending practices fit within HBL’s current models. Of course, the data files from each of these companies has different layouts, formats, and fields. Each portfolio consists of applications and loans. Each loan should have a corresponding loan application but not all loan applications lead to a loan. Applications that do not lead to loans are termed “unbooked” and applications that lead to loans are termed “booked”. Reasons that an application may be “unbooked” may be that the lender declined the application, or the borrower acquired a loan elsewhere, to name two reasons for an application failing to convert.
The lender, as required, consults several other credit rating agencies to collect information to help HBL determine the creditworthiness of its borrower. Ordinarily, credit reporting agencies supply information regarding the credit habits and experience of individuals as well as businesses. The HBL “agency” uses data collected from these credit reporting agencies.
When requested, data reporting agencies supply a variety of “low-level” data. This “low-level” data is specific to a single “customer”. It also provides a single creditworthiness score, or the “agency score”. Low-level data might include information regarding the number of times a customer was 30 days late paying a credit card bill, the number of credit cards the customer has, whether the customer has declared bankruptcy, and other items relating to the customer’s creditworthiness. The agency score is a single number intended to represent the customer’s overall creditworthiness by combining low-level customer data using its own proprietary algorithms. It is often the case that the lender, such as HBL, will make the same request for customer information to multiple credit reporting agencies, requesting the agency score as well as low-level data for its customer. The result of these multiple requests is that multiple agency scores will likely be collected for each customer. For example, HBL would use agency scores from credit rating companies such as Experian, TransUnion, and Equifax. Additionally, lenders such as HBL, often create their own assessment from low-level data provided in the same request.
The Objective
The overall objective of this project is to demonstrate your ability to clean data and develop SQL applications. As your analysis progresses, you will begin to create reports and collect detail important for communicating your work. You will combine these reports as a collection of deliverables at the time of the project completion. The objective of this project can be broken down into several smaller, general objectives; data cleaning, model building, and reporting. For the purpose of this class project, we will be focusing on the data cleaning and SQL coding objectives. A short description for each of the deliverables to support this effort follows.
1. Executive Summary
	2. Summary Statistics
	3. Graphs and Charts
	4. Test and Training Data Files
	5. Data Cleaning Journal
	6. SQL Code
	7. Python Code
Steps for creating the Predictor Data for Modeling Step
1.	Combine the two portfolios create loan application
Identify the corresponding variables in each of the 2 portfolios and combine into a single data file or table. You may need to combine variables or otherwise manipulate the data in each portfolio to complete the action(s). For each loan application, data may not be yet available on the initial step.

2.	Assemble the Predictor table
Leveraging the data in the loan application, create a new predictor table based on the specification provided by Table 1.

3.	Rate loan application and assign value to response variable
Create a response variable in your table that indicates whether the loan was “Good”, “Bad”, or "Indeterminate". Use the following business logic to determine the value for the response variable.
•	Loans graded below “C” are “Bad”
•	Loans with a status of “Charged Off” or “Default are “Bad”
•	All other loans are “Good”

4.	Create test and train data sets
After completing steps 1-3, randomly split the combined data so that you have a training set that contains 70% of the records and a test set that contains 30% of the records.
Loan and Application Portfolios
Information for the HBL loan portfolio come from two sources: Beachside Lenders and Wilson & Sons. The sources provide low-level reporting data that has been recorded at or before the active date for both booked and unbooked loans.
The Beachside Lenders data file is a CSV named Beach Loans.csv. Data for the Wilson portfolio can be found in WilsonandSons.csv. The Wilson data may contain multiple loans for a single borrower; each record may have a different application number.
Most of the variables that we need to extract may, in some cases, be constructs of the variables listed in Table 1. Predictive Model Columns.

Table 1: Predictive Model Variables
 
Table 2: Loan Application
No	Loan Application Variable	Description
1	id	A unique LC assigned ID for the loan listing.
2	addr_state	The state provided by the borrower in the loan application
3	application_type	Indicates whether the loan is an individual application or a joint application with two co-borrowers
4	emp_length	Employment length in years. Possible values are between 0 and 10 where 0 means less than one year and 10 means ten or more years.
5	annual_inc	The self-reported annual income provided by the borrower during registration.
6	annual_inc_joint	The combined self-reported annual income provided by the co-borrowers during registration
7	verified_status_joint	Indicates if the co-borrowers' joint income was verified by LC, not verified, or if the income source was verified
8	home_ownership	The home ownership status provided by the borrower during registration. Our values are: RENT, OWN, MORTGAGE, OTHER.
9	title	The loan title provided by the borrower
10	purpose	A category provided by the borrower for the loan request.
11	loan_amnt	The listed amount of the loan applied for by the borrower. If at some point in time, the credit department reduces the loan amount, then it will be reflected in this value.
12	pymnt_plan	Indicates if a payment plan has been put in place for the loan
13	int_rate	Interest Rate on the loan
14	installment	The monthly payment owed by the borrower if the loan originates.
15	loan_status	Current status of the loan
16	issue_d	The month which the loan was funded
17	last_credit_pull_d	The most recent month LC pulled credit for this loan
18	earliest_cr_line	The month the borrower's earliest reported credit line was
opened
19	mths_since_last_delinq	The number of months since the borrower's last delinquency.
20	mths_since_last_record	The number of months since the last public record.
21	open_acc	The number of open credit lines in the borrower's credit file.
22	pub_rec	Number of derogatory public records
23	inq_last_6mths	The number of inquiries in past 6 months (excluding auto and mortgage inquiries)
24	fico_range_high	The upper boundary range the borrower’s FICO at loan origination belongs to.
25	fico_range_low	The lower boundary range the borrower’s FICO at loan origination belongs to.
26	revol_bal	Total credit revolving balance
27	revol_util	Revolving line utilization rate, or the amount of credit the borrower is using relative to all available revolving credit.
28	tot_coll_amt	Total collection amounts ever owed
29	tot_cur_bal	Total current balance of all accounts
30	total_acc	The total number of credit lines currently in the borrower's credit file
31	funded_amnt	The total amount committed to that loan at that point in time.
32	term	The number of payments on the loan. Values are in months and can be either 36 or 60.
33	grade	LC assigned loan grade
34	sub_grade	LC assigned loan subgrade
