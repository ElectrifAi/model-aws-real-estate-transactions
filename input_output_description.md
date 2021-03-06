# Input/Output Description

- Input: A zip file containing 5 comma separated csv files. Reference file: sample.zip
- Details for each csv file:
    - scoring_date.csv (required)
        - Required columns:
            - scoring_date: scoring date for caculating signals and generate master table, format 'YYYY-MM-DD', eg: '2020-08-01'
    - Account.csv (required) : This is a table containing account information.
        - Required columns: 
            - Account_ID  ID Associated with the Account
            - Date    Date
            - Account_Type    Account Type (Joint/Individual/Business)
            - Account_Status  Account Status (i.e. Open/Closed/Normal/Delinquent/Overlimit/etc)
            - Product_Type    Type of Product (i.e. More/Miles/ETS, Charge vs Credit Card)
            - Account_Indicator   Indicate if Account is Main or Supplementary
            - Open_Date   Date Account Opened
            - Card_Activated_Date Date Activated Credit Card
            - Balance Balance Associated with the Account
            - Credit_Limit    Total Credit Limit
            - Credit_Interest Interest
            - Cash_Advance_Amount Total Dollar Amount of Cash Advances for the Current Billing Cycle
            - Min_Payment Minimum Payment on Credit
            - Credit_Fee  Fees
            - Delinquent  Whether the Account is Delinquent
    - Bureau.csv (required) : This is a table containing Bureau information. This contains information about the credit history of the account holder.
        - Required columns: 
            - Bureau_ID   Bureau ID
            - Account_ID  ID Associated with the Account
            - Date    Date
            - Auto_Amt    Indicates whether there is initial loan amount (HC/CL) of open auto loan in the last 1 month
            - Debt_Burden Debt Burden
            - Num_Trade_Lines Total Number of Trade Lines
            - Trade_Line_Tenure   Age of Oldest Trade Lines
            - Delinquency_Information Delinquency Information
            - Bankruptcy  Any Bankruptcies
            - Num_Open_Trade_Lines    Total Number of Opened Trade Lines
            - Mortgage_Amount Highest Initial Loan Amount (HC/CL) of Open Mortgage
            - Mortgage_Payment    Average of Current Monthly Payment Amount
            - Zip_Code    Zip Code of the Account Holder
            - Wallet_Size Wallet Size
            - FICO_Score  FICO Score
    - Profile.csv (required) : This is a table with collected customer activity including assets, credit card debt, income, and demographic information. Most of these features are optional.
        - Required columns: 
            - Account_ID  ID Associated with the Account
            - Month_of_Report Month tag of the Monthly Report
            - Loan_ID Loan ID
            - Loan_APR    Loan APR
            - Loan_Amount Loan Amount
            - Loan_Type   Loan type (i.e. Crdit Card, Loan, ID theft protection, etc) 
            - Canceled    Indicate whether customer canceled the loan application
            - Withdrawn   Indicate whether customer withdrew from the loan application
            - Loan_Indicator  Indicate whether customer was approved or declined for the loan
            - Credit_Line Credit line granted
            - Own_or_Rent Indicate whether customer is a home owner or rents (i.e. renter, owner) 
            - Channel_Source  Channel used to reach customer (i.e. mail, internet, phone, internet and phone) 
            - Household_Assets    Household Assets Associated with the Account
            - Mortgage_Assets Mortgage Assets Associated with the Account
            - Income  Income Associated with the Account
            - Total_Assets    Total Assets Associated with the Account
            - Ind_Home_Loan   Account Holder has a Home Loan
            - Zip_Code    Account Holder Zip Code
            - Property_Type   Property Type
    - Transactions.csv (required) : This is a table for transaction types of activity involving a dollar amount.
        - Required columns: 
            - Transaction_ID  ID Associated with the Transaction
            - Account_ID  ID Associated with the Account
            - Time    Timestamp associated with the Transaction
            - Transaction_Type    Type of Transaction (Warehousing/Trucking/Travel/Tour)
            - Transaction_Amount  Dollar Amount of the Transaction
            
- Output: a JSON list of objects containing for each account id, one more column added named 'score' which contains model's prediction of the real estate transactions propensity score for the record. Reference file: sample.zip.out
