# Crowdfunding ETL Project

## Overview
This project is an ETL (Extract, Transform, Load) pipeline for a crowdfunding dataset. The purpose of the project is to extract data from various sources, transform it into a usable format, and load it into a database for analysis.

### Purpose

The project provides a robust framework for managing crowdfunding data, which includes contacts, campaigns, and categorical information. With this ETL pipeline, users can automate the data handling process, ensuring data integrity and consistency.

### Scope

This pipeline caters to the needs of data analysts who require a reliable and efficient way to prepare crowdfunding data for in-depth analysis. It supports various data operations, such as data cleansing, transformation, and preparation for querying and reporting.

### Objectives

- To facilitate easy and efficient extraction of data from provided .xlsx and .csv files.
- To transform the data through cleaning and normalization, making it suitable for analytical purposes.
- To load the processed data into a structured SQL database, enabling complex queries and data exploration.

By the end of the ETL process, users will have a well-organized database, ready for analysis and insight generation, to aid in the decision-making process of crowdfunding initiatives.

## Setup and Installation

To get the Crowdfunding ETL pipeline up and running on your local machine, follow these steps:

### Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.8 or higher
- Jupyter Notebooks or JupyterLab
- Any RDBMS (MySQL, PostgreSQL, etc.), if you want to run the SQL schema

### Clone the Repository

Start by cloning the repository to your local machine:

```bash
git clone https://github.com/NataliiaShevchenko620/Crowdfunding_ETL.git
cd Crowdfunding_ETL
```
## Project Structure

The Crowdfunding ETL project is organized into several key directories and files. Here's an overview of the project's structure:

- `crowdfunding_db_schema.sql`: Contains the SQL statements for creating the database schema necessary for storing the processed data.

- `ETL_Mini_Project_NShevchenko_HKKang_TBrown.ipynb`: This Jupyter Notebook contains the logic for the ETL process, including data extraction, transformation, and loading.

- `contacts.xlsx` and `crowdfunding.xlsx`: These Excel files serve as the data sources from which the ETL process extracts information.

- `schema.png`: A visual representation of the database schema.

- `/Resources`: A directory containing additional resources, like CSV files and documentation, that support the ETL process.

```
/Crowdfunding_ETL
|-- /Resources
| |-- campaign.csv
| |-- category.csv
| |-- contacts.csv
| |-- subcategory.csv
|-- crowdfunding_db_schema.sql
|-- ETL_Mini_Project_NShevchenko_HK_Kang_T_Brown.ipynb
|-- README.md (this file)
|--schema.png
|--schema.txt
 
```


## Files
- `crowdfunding_db_schema.sql`: The SQL schema for the crowdfunding database.
- `ETL_Mini_Project_NShevchenko_HKKang_TBrown.ipynb`: Jupyter notebook for the ETL process.
- `contacts.xlsx` and `crowdfunding.xlsx`: Excel files containing the data to be processed.
- `schema.png`: Image of the database schema.

## Database Schema

The database schema for the Crowdfunding ETL project is designed to efficiently organize and store data extracted from various crowdfunding platforms. The schema consists of the following tables:

### Tables

- `category`: Stores information about the different categories of crowdfunding campaigns.
  - `category_id` (VARCHAR(30), Primary Key): Unique identifier for each category.
  - `category` (VARCHAR(30)): Name of the category.

- `subcategory`: Stores details about the subcategories under each main category of crowdfunding campaigns.
  - `subcategory_id` (VARCHAR(30), Primary Key): Unique identifier for each subcategory.
  - `subcategory` (VARCHAR(30)): Name of the subcategory.

- `contacts`: Keeps the contact information of campaign creators.
  - `contact_id` (INT, Primary Key): Unique identifier for each contact.
  - `first_name` (VARCHAR(30)): First name of the contact.
  - `last_name` (VARCHAR(30)): Last name of the contact.
  - `email` (VARCHAR(50)): Email address of the contact.

- `campaign`: Contains all the details regarding individual crowdfunding campaigns.
  - `cf_id` (INT, Primary Key): Unique identifier for each campaign.
  - `contact_id` (INT, Foreign Key): Reference to the `contacts` table.
  - `company_name` (VARCHAR(50)): Name of the company running the campaign.
  - ... (Other fields as per the schema description)

### Relationships

The `campaign` table is at the core of our schema, linked to both `contacts` and `category` tables to provide a comprehensive view of each crowdfunding campaign.

- A campaign belongs to a single category and subcategory.
- Each campaign is created by a contact, with contact details stored in the `contacts` table.

![Database Schema](schema.png)

For a complete detailed view of the schema, please refer to the `crowdfunding_db_schema.sql` file which includes all the SQL commands required to create the database and its tables.

By following the database schema, the ETL process populates these tables with data transformed from raw datasets, enabling sophisticated querying and analysis.

### Prerequisites

Before you begin, ensure you have the following installed:
- Python 3.8 or higher, which can be downloaded from the official [Python website](https://www.python.org/downloads/).
- Jupyter Notebooks or JupyterLab, which can be installed via pip with `pip install notebook` or `pip install jupyterlab`.
- PostgreSQL: Make sure you have PostgreSQL installed on your system. You can download it from the official [PostgreSQL website](https://www.postgresql.org/download/). Alternatively, you can use a service like Heroku Postgres if you prefer a cloud-based solution.

## Installation
Provide instructions on setting up the development environment and how to install any required dependencies.

## Usage

Once you have the repository cloned, prerequisites installed, and the PostgreSQL database set up, follow these steps to run the ETL pipeline:

1. **Start your PostgreSQL server** to ensure the database is running and accepting connections.

2. **Create the Database and Tables:**

    Run the SQL statements from `crowdfunding_db_schema.sql` to set up the database schema in PostgreSQL. You can do this via the psql command line tool or through a GUI like pgAdmin.

    ```bash
    psql -U username -d database_name -a -f crowdfunding_db_schema.sql
    ```
   
   Replace `username` with your PostgreSQL username and `database_name` with the name of your database.

3. **Configure Database Connection:**

   Open the `ETL_Mini_Project_NShevchenko_HKKang_TBrown.ipynb` notebook in Jupyter. Locate the database connection section and configure it to connect to your PostgreSQL database. Here is an example of what the configuration might look like:

    ```python
    connection_parameters = {
        'dbname': 'your_dbname',
        'user': 'your_username',
        'password': 'your_password',
        'host': 'localhost'
    }
    ```

   Replace `your_dbname`, `your_username`, and `your_password` with your actual database name, username, and password.

4. **Run the ETL Notebook:**

   Execute the cells in the `ETL_Mini_Project_NShevchenko_HKKang_TBrown.ipynb` notebook to perform the ETL operations. The notebook is designed to extract data from the provided Excel and CSV files,


## Contribution

If you would like to contribute to the Crowdfunding ETL project, please follow these steps:

1. **Fork the Repository**

   Start by forking the project repository on GitHub. This creates a copy of the repository in your own GitHub account and serves as your private workspace for the project.

2. **Clone Your Fork**

   Clone your fork to your local machine to create a local working copy of the code.

   ```bash
   git clone https://github.com/your-username/Crowdfunding_ETL.git
   cd Crowdfunding_ETL


## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE) file for details.

### MIT License Summary

The MIT License is a permissive license that is short and to the point. It lets people do anything they want with your code as long as they provide attribution back to you and don’t hold you liable.

#### Permissions

- Commercial use
- Modification
- Distribution
- Private use

#### Conditions

- Include copyright and license notice

#### Limitations

- No Liability
- No Warranty

For the full license text, please refer to the `LICENSE.md` file in the repository.

