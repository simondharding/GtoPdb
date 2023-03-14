# IUPHAR/BPS Guide to Pharmacology
<b>Copying chemical data between Oracle and PostgreSQL </b>

The chemical structures and physchem properties are stored in the Oracle database. To provide a single downloadable file of the database as a PostgresSQL dump, the public set of chemical structures must be copied to the public PostgreSQL database following the public database release (see protocol on doing database updates). For dev work sometimes the latest version of the chemical structures is needed to be copied over to the dev Postgres database.  

A useful tool to download data from the Oracle database is the Oracle SQL Developer. Export the data in CSV format and then it is ready to be uploaded to the PostgreSQL database. 

To do this: 

In SQL Developer login to either the dev ‘iuphardbdev’ database or the public ‘iuphardbuser’ database as required 

Click on the IUPHAR_LIGANDS table 

Click on the Data tab 

Right click anywhere on the table and select “Export” 

Change format to CSV and choose location to save the file 

Click “Next” and then “Finish”, and close the Oracle connection promptly (there is a limit to how many open connections to Oracle there can be at any one time). 

(Optional) Open the saved file and reorder the columns to match the order of columns in the PostgreSQL ‘ligand_structure’ table, which makes it easier to upload – just need to move the SMILES column from position 2 to 5. 

(Note, “INCHI_STANDARD” = “isomeric_standard_inchi”; “INCHI_KEY_STANDARD” = “isomeric_standard_inchi_key”; “SMILES” = “nonisomeric_smiles”; “CAN_INCHI_STANDARD” = “nonisomeric_standard_inchi”; “CAN_INCHI_KEY_STANDARD” = “nonisomeric_standard_inchi_key”) 
