# PubMed Data Extraction Pipeline for AI Systems

## 🔷 1. Project Overview
📌 What is this project?

The PubMed Fetcher is a command-line Python application that retrieves research papers from the PubMed database based on a user-defined query and filters results to identify non-academic (industry) authors such as those from pharmaceutical or biotech companies.

## 🎯 Purpose of the Project

- Automate extraction of research papers from PubMed
- Identify industry involvement in research
- Convert unstructured API data into structured CSV format
- Build a real-world CLI-based data pipeline

## 🔷 2. Problem Statement

- PubMed provides vast research data, but:
- It is not directly structured for analysis
- No built-in way to filter industry vs academic authors
- Manual extraction is time-consuming and inefficient

👉 This project solves that by:

- Automating data retrieval
- Filtering relevant author types
- Exporting clean, usable data

## 🔷 3. Key Features

🔍 Accepts advanced PubMed queries
📡 Fetches data using API
🧪 Filters non-academic authors
📧 Extracts corresponding author emails
📄 Saves results as CSV
⚙️ CLI support:
--help
--debug
--file

## 🔷 4. System Architecture (High-Level Flow)
User Input (Query)
        ↓
CLI Interface (argparse)
        ↓
PubMed API Call (requests)
        ↓
Fetch Paper IDs (ESearch)
        ↓
Fetch Paper Details (EFetch)
        ↓
Parse XML Data
        ↓
Filter Non-Academic Authors
        ↓
Extract Required Fields
        ↓
Write to CSV

## 🔷 5. Project Structure
pubmed_fetcher/
│
├── pubmed_fetcher/
│   ├── __init__.py
│   ├── fetcher.py        # API calls
│   ├── parser.py         # XML parsing
│   ├── filter.py         # Non-academic filtering
│   ├── utils.py          # Helper functions
│
├── cli.py                # Command-line interface
├── pyproject.toml        # Poetry config
├── README.md             # Documentation
├── output.csv            # Sample output

## 🔷 6. Technologies Used & Why
🐍 Python
Easy to use
Strong libraries for API & data handling

📦 Poetry
Why used?

Dependency management
Cleaner than pip + requirements.txt
Helps package the project professionally

🌐 Requests Library
Why used?

To make API calls to PubMed
Simple and reliable HTTP handling

🧾 XML Parsing (xml.etree.ElementTree)
Why used?

PubMed API returns XML data
Needed to extract structured information

🧮 CSV Module
 Why used?

Convert extracted data into structured format
Easy to use and widely supported

⚙️ argparse (CLI)

## Why used?
Accept user input from terminal
Makes project interactive and real-world ready

## 🔷 7. How It Works (Step-by-Step)
Step 1: User Input

User runs command:

get-papers-list "cancer therapy" --file results.csv
Step 2: Fetch Paper IDs

Use PubMed ESearch API
Get list of PubMed IDs

Step 3: Fetch Paper Details

Use EFetch API
Retrieve full paper metadata in XML

Step 4: Parse XML

Extract:
 Title
 Authors
 Affiliations
 Email
Publication date

Step 5: Filter Non-Academic Authors

Logic:

If affiliation contains:
"University" → academic ❌
"Pharma", "Biotech", "Inc", "Ltd" → non-academic ✅

Step 6: Save to CSV
Final output includes:

PubmedID
Title
Publication Date
Non-academic Authors
Company Affiliations
Corresponding Author Email

🔷 8. Key Design Decisions
✅ Modular Design

Separation of concerns:
- Fetching
- Parsing
- Filtering
👉 Makes code clean and maintainable

✅ CLI-Based Tool

- Real-world usage simulation
- More professional than a simple script

✅ Filtering Logic

- Focus on industry relevance
- Useful for research analysis

## 🔷 9. Challenges Faced

📄 Parsing complex XML structure
🧠 Identifying academic vs non-academic authors
🔗 Handling missing fields (emails, affiliations)
⚡ Managing API limits and delays

## 🔷 10. What We Learned
💡 Technical Learnings

- Working with real-world APIs
- Handling XML data parsing
- Building CLI tools
- Writing modular Python code
- Using Poetry for packaging

## 💡 Conceptual Learnings

- Difference between structured vs unstructured data
- Importance of data cleaning and filtering
- Designing scalable pipelines

## 💡 Industry-Relevant Skills

- API integration
- Data extraction pipelines
- Clean coding practices
- CLI application development

## 🔷 11. Applications of the Project

📊 Research analysis
🧪 Pharma/biotech insights
📈 Industry trend tracking
🧠 Data science pipelines

## 🔷 12. Limitations

- Filtering is based on keyword matching (not 100% accurate)
- PubMed API rate limits
- Some papers may have missing metadata

## 🔷 13. Future Improvements

🔍 Use NLP to classify authors more accurately
🌐 Add web interface (Flask/Streamlit)
🗄 Store data in database
📊 Add visualization dashboard

## Setup Instructions (to be completed after Python install)
Installation & Setup

1. Install Poetry
Check if Poetry is installed:
poetry --version

3. Clone the Repository

git clone https://github.com/Anusha6882/pubmed-paper-fetcher.git
cd pubmed-paper-fetcher

3. Install Dependencies
poetry install

4. Run the Program
poetry run python main.py -q "covid vaccine" -f covid_results.csv

## Filtering Logic
To identify non-academic authors:
Affiliations not containing common academic keywords like:"University", "College", "Institute", "Hospital", "School", "Center", "Department".

If author affiliation includes keywords like: "Pharma", "Biotech", "Inc", "Ltd", "Corp", "Company" — it is considered pharmaceutical/biotech.

## Tools Used

- [Poetry](https://python-poetry.org/) for packaging
- [Requests](https://docs.python-requests.org/) for HTTP API calls

## conclusion

This project was developed as part of a home exercise assignment to demonstrate the ability to build a modular, command-line Python tool for fetching and filtering PubMed research papers. The task involved not only implementing functional logic using public APIs but also showcasing real-world development practices such as clean code structuring, packaging with Poetry, and documenting with clarity.

Through this assignment, I aimed to:
- Break down a complex API problem into simpler components.
- Leverage modern Python packaging and CLI design.
- Integrate basic NLP-inspired logic to identify relevant papers based on author affiliations.
- Produce a complete, beginner-friendly, and easily extensible solution.
