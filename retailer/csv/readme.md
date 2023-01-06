# CSV Documentation
This document outlines CSV file formatting and delivery instructions for retailer inventory data sent to the PureMoto network.

### CSV File Requirements
* CSV files must use the first row in the file to specify the column headers.
* CSV files must contain columns for the following: part number, in store part quanity, retail part price, part cost, and part supplier code
* CSV files may optionally contain column headers for the following: quantity on order, part description, and last count date.

### Required Column Header Naming Scheme

| Name          | Column Description                        |
| ------------- | ----------------------------------------- |
| part_number   | Part number/SKU used to identify the part |
| qty_on_hand   | In-stock sellable quantity                |
| retail_price  | Price the part sells for                  |
| cost          | Cost of the part                          |
| supplier_code | Distributor/supplier code                 |

### Optional Column Header Naming Scheme:

| Name          | Column Description                                           |
| ------------- | ------------------------------------------------------------ |
| qty_on_order  | Part quantity on order. Default value: 0                     |
| description   | Part description. Default value: “”                          |
| last_count    | Latest update date for the part. Default value: current date |

### CSV Supported File Formats
* Most email clients enforce a strict 20-25Mb size limit for attachments. As CSV files must be delivered through email attachments, two file formats are supported for CSV file attachments:
    * If the file size of your CSV attachment does not exceed the attachment size limit of the email client used to send the attachment, you may send the attachment as a raw CSV file.
    * If the file size of your CSV attachment exceeds the attachment size limit of the email client used to send the attachment, you may send the attachment as a zipped/compressed file containing the CSV file.

### CSV Delivery Instructions
* Ensure the email addresses used to send attachments have been provided to PureMoto during the signup process.
    * Each email address provided to PureMoto is bound to a single retailer location within our system. As a result, attachments must always be sent from the email addresses provided during the signup process.
    * If a retailer has multiple locations, each file attachment sent must originate from the corresponding email address bound to that specific retailer location.
* Raw CSV/zipped attachments must be sent to csv@puremoto.com
    * Each email must contain a single CSV/zipped file attachment.

### Notes
* Existing inventory will be removed if a CSV attachment is not received and processed within a 72 hour period.
    * An email reminder will be sent notifying the retailer when their inventory has expired on the PureMoto network.
* If the CSV file excludes one or more of the required column headers, the file will not be processed and a notification will be sent to the retailer through email.
* If the CSV file excludes any of the optional columns, those values will be set to their default values when the file is processed.
* If a row contains invalid/missing data for any of the required columns, the row will be discarded.
* Sending multiple raw CSV attachments in a single email will cause the attachments to be overwritten when uploaded to the PureMoto network.
* If multiple CSV files are sent in a single zipped attachment, only a single CSV file from the zipped attachment will be processed and uploaded to the PureMoto network. The other CSV files will be discarded.
* Multiple email addresses may be provided for each retailer location.