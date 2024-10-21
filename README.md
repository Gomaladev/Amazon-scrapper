Amazon Scraper

Project Overview:
       This project is an Amazon web scraper that automates the process of collecting product information based on user-defined search queries. The scraper extracts data such as product name, price, rating, and number of reviews from the Amazon search results and saves the data into a CSV file. The script utilizes Selenium for web automation, BeautifulSoup for HTML parsing, and Python's threading library for concurrent execution to speed up data collection.

Requirements:   
      Before running the script, ensure you have the following installed:
          - Python 3.x
          - Selenium (`pip install selenium`)
          - BeautifulSoup (`pip install beautifulsoup4`)
          - Edge WebDriver (compatible with Microsoft Edge)

Setup Instructions:
1.Install Python Packages:
   - Open your terminal and run:
     ```bash
     pip install selenium beautifulsoup4
     ```
2.Download Edge WebDriver:
   - Visit the [Microsoft Edge WebDriver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) page.
   - Download the version that matches your Edge browser version and place it in a known directory (or ensure it's in your system's PATH).
3.Run the Script:
   - Open the script in your preferred Python editor or IDE.
   - Run the script and input the number of product searches you'd like to perform, followed by each search query. The queries should correspond to the products you want to search on Amazon.

How It Works:
Input:
1.Search Queries:
   - The script prompts the user to input the number of product searches they wish to perform. For each product, the user provides a search term that is then formatted into a search URL for Amazon.
Scraping:
2.Multi-threading:
   - For each search query, a new thread is spawned. Each thread launches a Selenium Edge WebDriver instance to navigate to the Amazon search results page.
3.WebDriver Setup:
   - The WebDriver operates in headless mode (without opening a browser window), enhancing performance. Once the page is fully loaded, the page source is extracted for HTML parsing.
4.HTML Parsing:
   - Using BeautifulSoup, the script locates each product's name, price, rating, and number of reviews from the HTML structure of the page.
   - If a product is missing any data (e.g., no price or reviews), the script handles it by appending `None` for those missing fields.
Output:
3.Saving Data:
   - The collected data is saved to `amazon_products.csv`, containing the product name, price, rating, and number of reviews.

CSV Output Structure:
The CSV file will be structured with the following columns:
```
Name, Price, Rating, Reviews
```
Each row will correspond to a product retrieved from the Amazon search results. The data for each column may be `None` if it is unavailable for a particular product.

Notes:
1.Headless Browsing:
   - The scraper uses the headless mode of Selenium, which makes it run without displaying a browser window, ideal for automation and reducing resource consumption.
2.Rate Limits:
   - Be mindful of Amazon's rate-limiting or anti-bot measures. If scraping too many products in a short period, you may be temporarily blocked.
3.Threading:
   - The script uses Python's `threading` module to speed up the scraping process by launching multiple threads for each query. This ensures that the product data is scraped concurrently.

Troubleshooting:
1.ModuleNotFoundError:
   If you encounter a `ModuleNotFoundError` for Selenium or BeautifulSoup, ensure the required packages are installed:
   ```bash
   pip install selenium beautifulsoup4
   ```
2.WebDriver Issues:
   Ensure the Microsoft Edge WebDriver is correctly installed and compatible with your browser version. If the WebDriver isn't recognized, ensure its path is included in your system's PATH environment variable or specify the absolute path in the script.

License:  
   This project is for educational and personal use. Be mindful of scraping policies and terms of service of websites such as Amazon.
