# PureMoto Network CSV Documentation

### CSV File Requirements
* The first row of the CSV file must contain the required column header names.
* The CSV file is required to contain columns for the following: part number (SKU), in store quantity, retail price, cost, and supplier code.
* The CSV file may optionally contain columns for quantity on order, description, and last count

### Required Column Header Names
| Column Name   | Column Description                        |
| ------------- | ----------------------------------------- |
| part_number   | Part number/SKU used to identify the part |
| qty_on_hand   | In-stock sellable quantity                |
| retail_price  | Price the part sells for                  |
| cost          | Cost of the part                          |
| supplier_code | Distributor/supplier code                 |

### Optional Column Header Naming Format:

| Column Name   | Column Description                                           |
| ------------- | ------------------------------------------------------------ |
| qty_on_order  | Part quantity on order. Default value: 0                     |
| description   | Part description. Default value: “”                          |
| last_count    | Latest update date for the part. Default value: current date |

### CSV Submission Instructions
* The email address used to send CSV file attachments must be provided to PureMoto for verification.
    * All CSV attachments sent must originate from the email address that is provided to PureMoto for verification.
* CSV files must be sent as an email attachment to csv@puremoto.com to be processed.

### Notes
* Existing inventory will be removed if a CSV attachment is not received and processed within a 72 hour period.
* If the CSV file excludes one or more of the required column headers, the file will not be processed and an error email will be sent back to the dealer.
* If the CSV file excludes any of the optional columns, those values will be set to their default values when the file is processed.
* If a row contains invalid/missing data for any of the required columns, the row will be discarded.