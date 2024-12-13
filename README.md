# Web-Scraping-from-Wikipedia-using-Python
Web Scraping from Wikipedia using Python

Overview

This project demonstrates how to scrape data from the Wikipedia Home Page using Python. It covers key concepts of web scraping, including data extraction, processing, and storage techniques, using widely-used Python libraries like Requests, Beautiful Soup, and Selenium. By following this guide, you will become familiar with web scraping practices and create your own web scraper.

Features

Fetch Web Pages: Uses the requests library to download web pages.

HTML Parsing: Implements Beautiful Soup for parsing and extracting structured data from HTML.

Dynamic Content Handling: Introduces Selenium for scraping dynamic websites.

Data Storage: Demonstrates exporting scraped data into structured formats such as CSV or JSON.

Requirements

Before starting, ensure you have the following installed:

Python 3.6+

Required Libraries:

requests

BeautifulSoup4

urllib3

selenium

You can install the dependencies using:

pip install virtualenv
python -m pip install selenium requests urllib3 beautifulsoup4

Process Overview

Web Scraping Basics:

Understanding the difference between web scraping and web crawling.

Fetching web pages and parsing the content.

Using Python for Web Scraping:

Configuring a virtual environment to avoid affecting global packages.

Installing necessary libraries for scraping.

HTML Content Extraction:

Parsing and navigating HTML elements with Beautiful Soup.

Extracting specific data like paragraphs (<p> tags) or elements with unique identifiers (e.g., id or class).

Exploring Page Structure:

Using Chrome Developer Tools to inspect elements and understand the webpage structure.

Locating target data and extracting nested elements.

Handling Dynamic Web Pages:

Using Selenium to interact with JavaScript-based or dynamically loaded content.

Exporting Data:

Formatting and storing extracted data into CSV or JSON.

Usage Instructions

Step 1: Fetch HTML Content with requests

import requests

page = requests.get("https://en.wikipedia.org/wiki/Main_Page")
print(page.status_code)  # Check the status of the request
print(page.content)      # Get the raw HTML content

Step 2: Parse HTML with Beautiful Soup

from bs4 import BeautifulSoup

# Parse the HTML content
soup = BeautifulSoup(page.content, 'html.parser')

# Prettify the output
print(soup.prettify())

# Extract all paragraph tags
print(soup.find_all('p'))

Step 3: Extract Specific Data

Using find and find_all:

# Find element by ID
content = soup.find(id="mp-left")

# Find all elements with a specific class
items = content.find_all(class_="mp-h2")
result = items[0]
print(result.prettify())

Step 4: Export Data

Save the extracted data to a CSV:

import csv

with open('scraped_data.csv', 'w', newline='', encoding='utf-8') as file:
    writer = csv.writer(file)
    writer.writerow(["Tag", "Content"])
    for item in items:
        writer.writerow([item.name, item.get_text()])

Tools and Technologies Used

Python: The primary language for scripting and automation.

Requests: For sending HTTP requests and fetching web pages.

Beautiful Soup: For parsing HTML and XML.

Selenium: To handle dynamic or JavaScript-generated content.

CSV/JSON: To store structured data.

Ethical Considerations

Web scraping should only be used for ethical purposes. Before scraping any website, check the site's robots.txt file and comply with its rules. Ensure you are not violating the terms of service for any website.

Output Examples

HTML Content (Prettified)

<html>
 <body>
  <p>This is an example paragraph.</p>
 </body>
</html>

Extracted Paragraphs

This is an example paragraph.

CSV Output

Tag

Content

p

This is an example paragraph.

Future Work

Expand to more complex websites with nested structures.

Incorporate additional storage options like MySQL databases.

Automate scraping and periodic data updates using schedulers.

Contributing

Feel free to fork this repository and submit pull requests for improvements.

License

This project is licensed under the MIT License - see the LICENSE file for details.

