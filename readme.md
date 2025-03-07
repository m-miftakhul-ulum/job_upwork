# Job Scraper with WhatsApp Notification

This script is designed to scrape job listings from Upwork, specifically for "web scraping" related jobs, and send notifications via WhatsApp whenever a new job is found. The script uses `curl_cffi` for HTTP requests, `BeautifulSoup` for HTML parsing, and `dotenv` for environment variable management.

## Features

- **Web Scraping**: The script scrapes job listings from Upwork's search results page.
- **JSON Storage**: Stores the scraped job data in a JSON file (`jobs.json`) to keep track of previously found jobs.
- **WhatsApp Notification**: Sends a WhatsApp message to a specified number whenever a new job is found.
- **Environment Variables**: Uses `.env` file to securely store sensitive information like WhatsApp API credentials and phone number.

## Prerequisites

Before running the script, ensure you have the following installed:

- Python 3.x
- Required Python packages: `curl_cffi`, `beautifulsoup4`, `python-dotenv`

You can install the required packages using pip:

```bash
pip install curl_cffi beautifulsoup4 python-dotenv
```

## Setup

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/job-scraper.git
   cd job-scraper
   ```

2. **Create a `.env` File**:
   Create a `.env` file in the root directory of the project and add the following variables:
   ```plaintext
   NO_HP=your_phone_number
   WA_API=your_whatsapp_api_key
   ```
   Replace `your_phone_number` with your phone number (including country code, e.g., `6281234567890`) and `your_whatsapp_api_key` with your WhatsApp API key.

3. **Run the Script**:
   ```bash
   python main.py
   ```

## How It Works

1. **Scraping Job Listings**:
   - The script sends a GET request to Upwork's job search page for "web scraping" jobs.
   - It parses the HTML response using BeautifulSoup to extract job titles and links.

2. **Storing Data**:
   - The script checks if a `jobs.json` file exists. If it does, it loads the existing data; otherwise, it initializes an empty list.
   - It compares the newly scraped jobs with the existing ones and appends any new jobs to the list.

3. **Sending WhatsApp Notifications**:
   - For each new job found, the script sends a WhatsApp message to the specified phone number using the WhatsApp API.
   - The message includes the job title and link.

4. **Updating the JSON File**:
   - The script updates the `jobs.json` file with the new list of jobs.

## Customization

- **Change Job Query**: Modify the URL in the `get_job` function to search for different job categories or keywords.
- **Notification Method**: You can customize the notification method by uncommenting and modifying the `notif_up` function to use desktop notifications or other methods.

## Notes

- **Rate Limiting**: Be mindful of the rate at which you run the script to avoid being blocked by Upwork.
- **WhatsApp API**: Ensure you have a valid WhatsApp API key and that the API endpoint is correctly configured.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.





