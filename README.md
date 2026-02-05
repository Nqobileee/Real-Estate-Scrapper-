# Real Estate Scraper

A Python-based web scraping tool for extracting real estate listings data and storing it in Google Sheets. This project automates the process of collecting property information from real estate websites, performing duplicate detection, and maintaining clean data records.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Usage](#usage)
- [Notebooks](#notebooks)
- [Dependencies](#dependencies)
- [Google Sheets Integration](#google-sheets-integration)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project provides an automated solution for scraping real estate listings from websites and managing the data efficiently. The scraper collects property details such as price, location, size, and other relevant information, then stores it in Google Sheets for easy access and analysis.

---

## Features

- **Automated Web Scraping**: Extract real estate listings from target websites
- **Google Sheets Integration**: Seamlessly store and update data in Google Sheets
- **Duplicate Detection**: Identify and remove duplicate listings automatically
- **Data Formatting**: Clean and format data for consistency
- **Error Handling**: Robust error handling for reliable scraping
- **Rate Limiting**: Respectful scraping with built-in delays

---

## Project Structure

```
Real-Estate-Scrapper/
├── README.md
├── RealEstateListings2.ipynb          # Main scraping notebook
├── Duplicate Check and Delete.ipynb   # Data cleaning and duplicate removal
└── credentials.json                   # Google Sheets API credentials (not tracked)
```

---

## Prerequisites

Before setting up this project, ensure you have:

- **Python 3.8+** installed on your system
- A **Google Account** for Google Sheets API access
- **Jupyter Notebook** or **JupyterLab** installed
- Basic understanding of Python and web scraping concepts

---

## Installation

### Step 1: Install Python

Download and install Python from the official website:

**Windows/Mac/Linux**: [https://www.python.org/downloads/](https://www.python.org/downloads/)

Verify your installation:

```bash
python --version
```

### Step 2: Install Jupyter Notebook

**Option A: Using pip**

```bash
pip install notebook
```

**Option B: Using Anaconda (Recommended)**

Download Anaconda from [https://www.anaconda.com/products/distribution](https://www.anaconda.com/products/distribution)

Jupyter Notebook comes pre-installed with Anaconda.

### Step 3: Clone the Repository

```bash
git clone https://github.com/yourusername/Real-Estate-Scrapper.git
cd Real-Estate-Scrapper
```

### Step 4: Install Required Dependencies

Install all required Python libraries:

```bash
pip install requests beautifulsoup4 gspread oauth2client gspread-formatting pandas lxml
```

Or install from a notebook cell:

```python
!pip install requests beautifulsoup4 gspread oauth2client gspread-formatting pandas lxml
```

---

## Configuration

### Google Sheets API Setup

To enable Google Sheets integration, you need to set up API credentials:

1. **Create a Google Cloud Project**
   - Go to [Google Cloud Console](https://console.cloud.google.com/)
   - Create a new project or select an existing one

2. **Enable Google Sheets API**
   - Navigate to "APIs & Services" > "Library"
   - Search for "Google Sheets API" and enable it
   - Also enable "Google Drive API"

3. **Create Service Account Credentials**
   - Go to "APIs & Services" > "Credentials"
   - Click "Create Credentials" > "Service Account"
   - Fill in the service account details
   - Grant the service account appropriate permissions

4. **Download Credentials**
   - Click on the created service account
   - Go to "Keys" tab
   - Click "Add Key" > "Create New Key"
   - Choose JSON format and download
   - Save the file as `credentials.json` in the project root

5. **Share Your Google Sheet**
   - Open your target Google Sheet
   - Click "Share"
   - Add the service account email (found in credentials.json)
   - Grant "Editor" permissions

---

## Usage

### Starting Jupyter Notebook

Navigate to the project directory and launch Jupyter:

```bash
cd path/to/Real-Estate-Scrapper
jupyter notebook
```

A browser window will open with the Jupyter interface.

### Running the Scraper

1. Open **RealEstateListings2.ipynb**
2. Update the target URL and scraping parameters
3. Run all cells sequentially by pressing `Shift + Enter`
4. Monitor the output for scraping progress

### Cleaning Duplicate Data

1. Open **Duplicate Check and Delete.ipynb**
2. Specify your Google Sheet name and worksheet
3. Run all cells to identify and remove duplicates
4. Review the summary of deleted records

---

## Notebooks

### RealEstateListings2.ipynb

The main scraping notebook that:
- Connects to target real estate websites
- Extracts listing information
- Processes and formats data
- Uploads results to Google Sheets

### Duplicate Check and Delete.ipynb

A utility notebook that:
- Reads data from Google Sheets
- Identifies duplicate entries based on specified criteria
- Removes duplicate records
- Updates the sheet with clean data

---

## Dependencies

| Library | Purpose |
|---------|---------|
| **requests** | HTTP library for making web requests |
| **beautifulsoup4** | HTML/XML parsing and data extraction |
| **lxml** | XML and HTML parser (faster than default) |
| **gspread** | Google Sheets API wrapper |
| **oauth2client** | OAuth 2.0 client library for authentication |
| **gspread-formatting** | Cell formatting for Google Sheets |
| **pandas** | Data manipulation and analysis |
| **time** | Built-in module for delays and timestamps |
| **datetime** | Built-in module for date/time operations |

---

## Google Sheets Integration

The project uses Google Sheets as a database for storing scraped data. Benefits include:

- **Real-time Access**: View and edit data from anywhere
- **Collaboration**: Share data with team members
- **Easy Visualization**: Create charts and pivot tables
- **Export Options**: Download data in various formats (CSV, XLSX, PDF)
- **Version History**: Track changes over time

### Sheet Structure

Typical columns in the output sheet:

| Column | Description |
|--------|-------------|
| Title | Property title or description |
| Price | Listing price |
| Location | Property address or area |
| Size | Property size (sq ft or sq m) |
| Bedrooms | Number of bedrooms |
| Bathrooms | Number of bathrooms |
| URL | Link to the original listing |
| Date Scraped | Timestamp of when data was collected |

---

## Troubleshooting

### Common Issues

**Issue**: `ModuleNotFoundError: No module named 'gspread'`
- **Solution**: Install the missing module: `pip install gspread`

**Issue**: `gspread.exceptions.APIError: [403] The caller does not have permission`
- **Solution**: Ensure the service account email has editor access to your Google Sheet

**Issue**: Connection timeout or request errors
- **Solution**: Check your internet connection, verify the target URL is accessible, and ensure you're not being rate-limited

**Issue**: Data not appearing in Google Sheets
- **Solution**: Verify your credentials.json file is in the correct location and the sheet name matches exactly

**Issue**: Duplicate detection not working
- **Solution**: Ensure the comparison fields in the duplicate check notebook match your actual column names

---

## Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

## Disclaimer

This tool is for educational purposes only. Always ensure you have permission to scrape websites and comply with their Terms of Service and robots.txt file. Be respectful of website resources by implementing appropriate rate limiting and avoiding excessive requests.

---

## Contact

For questions, issues, or suggestions, please open an issue on GitHub or contact the repository maintainer.

---

**Note**: Remember to keep your `credentials.json` file secure and never commit it to version control. Add it to your `.gitignore` file to prevent accidental exposure of sensitive API credentials.




