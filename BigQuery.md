# Use cases for BigQuery

## Use a list of accessions to limit the search results
1. On the BigQuery console, Under `Resources`, your project name should be there. Mine is stupidly named `ncbi-sra`. With this highlighted, on the right hand side, click `Create Dataset`. Provide a name, e.g. `SRR_Run_IDs`
2. The dataset should now be under the project name on the right. 

Now, you made a dataset where you can add tables of SRA Run IDs/other things. Click it and select `Create Table` on the right.
3. Create table from --> Upload --> Select file. Make a file with a list of SRR run accessions and no header. Upload this file as CSV.
4. Under Table Name, give it a descriptive list. E.g., human gut viromes.
5. Under Schema --> Add Field --> Give it the column name, E.g., `acc`. Click create table

Now we have a table that can be used to restrict search results. 

## Return the taxonomy_analysis table info from a selected list of SRA Run IDs
```
SELECT T.acc, T.tax_id, T.rank, T.name, T.total_count, T.self_count
FROM nih-sra-datastore.sra_tax_analysis_tool.tax_analysis as T, ncbi-sra.Test.human_gut_viromes_042820 as A
WHERE T.acc=A.acc
```
