# Jumia Product Scraper (Selenium-Based)

This project implements an automated web scraper for Jumia, built using Selenium WebDriver and Python. It is designed to extract structured product data from multiple categories with accurate pricing, discount calculations, and smart update handling. The scraped data is stored in a MongoDB collection for further analysis or use.

## Project Objective

The primary goal of this scraper is to collect comprehensive product listings from Jumia’s online store, capturing key data points such as product titles, prices, and discount metrics. The system ensures data freshness and avoids duplication by comparing current listings with existing records.

## Extracted Data

For each product found in the specified categories, the scraper collects the following information:

- `product_title`: Full name of the product.
- `product_url`: Direct link to the product detail page.
- `current_price`: The current listed price.
- `old_price`: The original price before discount (if any).
- `discount_percentage`: Calculated percentage off.
- `discount_quantity`: Absolute discount value in currency.
- `inserted_at`: Timestamp of the first insertion.
- `updated_at`: Timestamp of the most recent update.
- `published_at`: Boolean field for custom publication logic.

## Core Features and Implementation Highlights

- **Smart Browser Automation**: Uses Selenium with a configurable Firefox profile and user-agent to simulate a real user browsing experience, including support for headless mode.
- **Popup Handling**: Automatically closes promotional popups that interfere with page loading.
- **Efficient Navigation**: Iterates through categories and paginated results using dynamically constructed URLs.
- **Robust Price Parsing**: Implements regex-based extraction and normalization of price values across various formats (e.g., commas, spaces).
- **Data Validation and Deduplication**: Prevents redundant inserts by checking for existing entries in the MongoDB collection using product title or URL.
- **Automatic Price Updates**: Updates product records if price data changes on subsequent scrapes, preserving historical price tracking.
- **Modular Architecture**: Clean separation between configuration, browser setup, page retrieval, data parsing, and database interaction.
- **Database-Ready Output**: Collected data is stored in a MongoDB database in a structured, queryable format.

## Scraping Results

The scraper targets key categories such as:

- Phones & Tablets
- Electronics

Across five pages per category, the system successfully extracted and inserted/upgraded **hundreds of product records**, depending on the availability and variation in listings. Each scrape session handles both new additions and changes to existing listings, ensuring up-to-date accuracy with minimal redundancy.

The output is structured for MongoDB, allowing easy export to JSONL or direct use in data pipelines, dashboards, or analytics tools.

## Technical Skills Demonstrated

- Advanced Selenium scripting and dynamic content handling  
- HTML parsing and DOM navigation using CSS selectors  
- Data normalization and validation with regular expressions  
- Automated browser control with user-agent and media preference configurations  
- Clean and modular Python code adhering to best practices  
- MongoDB integration for scalable data storage  
- Error-tolerant execution and popup handling logic  
- Performance tuning via headless browsing and page load timing

---

## MongoDB Atlas Snapshot

Below is a sample screenshot of the MongoDB Atlas dashboard showing the scraped data records for verification and demonstration purposes:

![MongoDB Atlas Overview](./assets/mongo.png)
<sub>_Example: Screenshot of the `products` collection displaying scraped data fields in the Atlas UI._</sub>

> To replace this image, upload your own database screenshot to the `/assets` folder and update the filename as needed.
