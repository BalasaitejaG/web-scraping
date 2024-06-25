# Automating Web Scraping with AutoScraper

This project demonstrates how to use the `AutoScraper` library to automate web scraping tasks. Specifically, it shows how to scrape product details from Amazon and process the scraped data using pandas.

## Installation

To run this project, you'll need to install the following dependencies:

```bash
pip install autoscraper pandas
```
## Usage
### Import Libraries and Set Up the Scraper

First, import the necessary libraries and configure the URL for scraping:
```bash
from autoscraper import AutoScraper
import pandas as pd

url = 'https://www.amazon.com/s?k=laptop'
```
### Define the Desired Data

Specify the data you want to scrape by providing a list of example items. This helps 'AutoScraper' identify and collect similar data from the page:
```bash
wanted_list = [
    "https://m.media-amazon.com/images/I/71yAdFdFPdL._AC_UY218_.jpg",
    "$289.98",
    "HP 14 Laptop, Intel Celeron N4020, 4 GB RAM, 64 GB Storage, 14-inch Micro-edge HD Display, Windows 11 Home, Thin & Portable, 4K Graphics, One Year of Microsoft 365 (14-dq0040nr, Snowflake White)",
    "1,394"
]
```
### Build and Execute the Scraper

Build the scraper with the defined data and execute it to collect the desired information:
```bash
scraper = AutoScraper()
result = scraper.build(url, wanted_list)
```
### Process the Scraped Data

After scraping, process the data and convert it into a pandas DataFrame for further analysis:
```bash
import pandas as pd

# Example of converting the scraped data into a DataFrame
df = pd.DataFrame({
    'Title': result['rule_title'],
    'Price': result['rule_price'],
    'Stars': result['rule_stars'],
    'Image': result['rule_image']
})

print(df)
```
## Example Output

The script extracts details such as product titles, prices, star ratings, and images from Amazon search results. Here is a snippet of the resulting DataFrame:
```bash
                                               Title      Price  Stars                                               Image
0  HP 14 Laptop, Intel Celeron N4020, 4 GB RAM, 6...   $289.98  1,394  https://m.media-amazon.com/images/I/71yAdFdFPdL._AC_UY218_.jpg
1  HP 15.6" Portable Laptop (Include 1 Year Micro...   $209.99  1,372  https://m.media-amazon.com/images/I/711OHeRmEaL._AC_UY218_.jpg
...
```
# Acknowledgments

AutoScraper for providing an easy-to-use scraping tool.
pandas for data manipulation and analysis.
