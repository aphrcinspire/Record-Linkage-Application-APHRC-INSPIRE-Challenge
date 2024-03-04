# RecordFuse: Merge & Clean Your Data with Ease

This project aims to create a user-friendly web application for merging and deduplicating records across various datasets. It provides researchers, data analysts, and professionals with a powerful tool to tackle common challenges in data integration and cleaning.

## Features

* **Supported Data Formats:** CSV, Excel spreadsheets
* **Matching Algorithms:** Fuzzy matching, probabilistic linking, and rule-based methods
* **Duplicate Detection & Resolution:** Identify and resolve potential duplicates accurately
* **Intuitive Interface:** Visualize, filter, and manually review linked records
* **Multiple Output Options:** Download merged datasets or export confidence scores
* **Built with:** AngularJS, NestJS, MySQL, python: Splink Package

## Status & Next Steps

Currently still in the coding phase and have managed to:

* Adding user login and create account page.
* A landing page for the user after login.
* A CSV file upload page for user to upload a file they would like to process.
* Implementing Data Retrieval from user for processing by ML model.
* Built and ML Model that is hosted in Hugging Face.

For our next steps we plan to:

* Add routing to the web application to introduce a process flow.
* Make the current user interface more friendly.
* Implement authentication and authorization
* Add options of either deduplicating or merging records according to results produced by ML model.
* Option to download fused records.

## Procedures for running the project

1. Clone the repository into your local machine using the link; https://github.com/blacklihgt/Record_Linkage.git
2. Once cloned, run the command npm install to download all project dependencies. 
    Note: Since we've used an nx monorepo setup, we may be required to install NX environment using the command 'npm add --global nx@latest'.
3. Run 'nx run frontend:serve'. This allows the angular frontend pages to be rendered on localhost:4200
4. To access the different pages in the web application, you can use the following paths after localhost:4200;
    1.  /signup - Allows creation of an admin account
    2.  /login - Allows logging in to the web application
    3.  /homepage - Allows access to page where the record linkage results are to be displayed
    4.  /file-upload - Allows for uploading CSV files to carry out record linkage.
5. To run the API endpoint that communicates with both the ML model and database, run 'nx run api:serve'. This facilitates sending data to and from the ML model.


## Learn More
* Notebook File used in training model: 
* ML Model link: https://theonlydeity-mirage.hf.space/results
* Design link: https://www.figma.com/file/vH2E7FcfuHCpEmrvPrResW/RecordFuse?type=design&node-id=0-1&mode=design&t=StC332GcXli1HjMN-0
