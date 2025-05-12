Code Run
To run the code, you can either run it on docker natively or run it on Google Collab. 
You need to install pandas, boto3, duckdb, cassandra, and cassandra-sigv4. 
This Jupyter Notebook takes in 7 .csv files and outputs my answers to DE_300 Homework2 notebook.
The 7 csvs are names ADMISSIONS, D_ICD_PROCEDURES, DRGCODES, ICUSTAYS, PATIENTS, PRESCRIPTIONS, and PROCEDURES_ICD.

Expected Outputs
In part 1, there are three questions that grab the SQL query that answers the following three questions:
1) Create a summary of type of drugs and their total amount used by ethnicity. Report the top usage in each ethnicity group
2) Create a summary of procedures performed on patients by age groups (<=19, 20-49, 50-79, >80). Report the top three procedures, along with the name of the procedures, performed in each age group.
3) How long do patients stay in the ICU? Is there a difference in the ICU length of stay among gender or ethnicity?

There are some queries that are also included in the .ipynb file, specifically for question 2 and 3 that build up to the final question.
Furthermore, there is a plot for question 1.

In part 2, we use Cassandra and upload data into our Cassandra table. These queries replicate the same outputs as part 1. The order of the outputs are not the same, but are the same data.

