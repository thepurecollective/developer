# CSV Documentation
This document outlines CSV file formatting and delivery methods for retailer inventory data sent to the PureMoto network.

## Table of Contents

 1. [CSV File Structure](#csv-file-structure)
    1. [CSV Header Requirements](#csv-header-requirements)
    2. [Required Column Header Naming Scheme](#required-column-header-naming-scheme)
    3. [Optional Column Header Naming Scheme](#optional-column-header-naming-scheme)
    4. [Sample CSV File](#download-a-sample-csv-file)
 2. [Supported CSV Delivery Methods](#supported-csv-delivery-methods)
     1. [Email](#email)
     2. [SFTP](#sftp)
 3. [Important Notes](#important-notes)

## CSV File Structure

* ### CSV Header Requirements
    * CSV files must use the first row in the file to specify the column headers.
    * CSV files must contain columns for the following: part number, in store part quanity, retail part price, part cost, and part supplier code
    * CSV files may optionally contain column headers for the following: quantity on order, part description, and last count date.

* ### Required Column Header Naming Scheme:

| Column Name   | Column Description                        | Column Data Type |
| ------------- | ----------------------------------------- | ---------------- |
| part_number   | Part number/SKU used to identify the part | Text             |
| qty_on_hand   | In-stock sellable quantity                | Number           |
| retail_price  | Price the part sells for                  | Number           |
| cost          | Cost of the part                          | Number           |
| supplier_code | Distributor/supplier code                 | Text             |

* ### Optional Column Header Naming Scheme:

| Column Name  | Column Description            | Column Data Type | Default Value |
| ------------ | ----------------------------- | ---------------- | ------------- |
| qty_on_order | Part quantity on order        | Number           | 0             |
| description  | Part description              | Text             | Empty         |
| last_count   | Last update date for the part | See sample CSV   | Current date  |

* ### [Download a sample CSV file](sample-csv.csv)

## Supported CSV Delivery Methods

* ### Email:
    * Most email clients enforce a strict 20-25Mb size limit for attachments. The PureMoto network accepts two separate file formats for CSV files as a result.
        * If the file size of your CSV does not exceed the attachment size limit of the email client used to send the attachment, you may send the attachment as a raw CSV file.
        * If the file size of your CSV exceeds the attachment size limit of the email client used to send the attachment, you may send the attachment as a zipped/compressed file containing the CSV file.
    * **Raw CSV/zipped attachments must be sent to csv@puremoto.com**
        * Ensure the email addresses used to send attachments have been provided to PureMoto during the signup process.
            * Email addresses are bounded to a single retailer location within our system. As a result, email attachments must always be sent from the email addresses provided during the signup process.
            * If a retailer has multiple locations, each file attachment sent must originate from the corresponding email address bound to that specific retailer location.

* ### SFTP:
    * Provide PureMoto with a valid public SSH key before delivering a raw CSV file via SFTP.
        * [Supported SSH key algorithms](https://docs.aws.amazon.com/transfer/latest/userguide/key-management.html#key-algorithms).
    * Once a valid public SSH key has been provided, the retailer will be given login credentials to the PureMoto SFTP server.
        * Raw CSV files may be uploaded to the users root folder or to any user created sub folders.
    * **Note:** 
        * CSV inventory files are automatically deleted from the SFTP server upon successful upload and processing by the PureMoto network.
        * To receive email notifications when an inventory file fails to be processed due to an invalid format or if their inventory has expired on the network, they may provide PureMoto with an email address where notifications may be sent.

## Important Notes
* All existing inventory on the PureMoto network will be expired if a CSV file is not received and successfully processed within a 72 hour period.
    * An email notification will be sent to retailers who submit CSV files via email when their inventory has expired.
    * If CSV files are submitted via SFTP, provide PureMoto with a email address to receive an email notification when inventory expires.
* If the CSV file excludes one or more of the required column headers, the file will not be processed.
    * An email notification will be sent to retailers who submit CSV files via email when this issue occurs.
    * If CSV files are submitted via SFTP, provide PureMoto with a email address to receive an email notification when this issue occurs.
* If the CSV file excludes any of the optional columns, those values will be set to their default values when the file is processed.
* If a row contains invalid/missing data for any of the required columns, the row will be discarded when inventory is uploaded to the PureMoto network.
* If multiple CSV files are sent in a single zipped attachment, only a single CSV file from the zipped attachment will be processed and uploaded to the PureMoto network. The other CSV files will be discarded.