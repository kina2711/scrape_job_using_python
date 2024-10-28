# Job Listings Scraper

A Python project designed to automatically scrape job listings from [ITViec](https://itviec.com), filter jobs based on specific criteria, save the results in a CSV file, and send an email notification of the latest job listings daily. This tool is ideal for those looking to streamline job searches by automating data collection and notification for relevant listings.

## Project Overview

This project scrapes job listings from a popular Vietnamese job board (ITViec) and filters jobs according to predetermined criteria, focusing on those that require "Python" and excluding those marked "Hybrid". The filtered listings are saved in a CSV file and emailed to a specified recipient daily. 

The project runs on a daily schedule, helping users stay up-to-date with the latest job opportunities without manually searching. 

## Key Features

- **Web Scraping**: Uses BeautifulSoup to extract job data from ITViec.
- **Job Filtering**: Filters job listings based on keywords in job descriptions to match specific requirements.
- **Data Storage**: Saves the scraped job listings in a CSV file for easy access and further analysis.
- **Email Notifications**: Sends a summary of the latest filtered job listings via email to keep users updated.
- **Scheduling**: Automates the scraping and notification process to run daily at a specified time.

## Requirements

The project requires the following libraries to be installed:

- `requests`
- `beautifulsoup4`
- `pytz`
- `schedule`
- `smtplib` (standard library)
- `csv` (standard library)

To install the required libraries, use:
```bash
pip install requests beautifulsoup4 pytz schedule
```

### Configuration

Before running the script, update the following variables to set up email notifications:

- `EMAIL_SENDER`: Your email address (for sending job notifications).
- `EMAIL_RECEIVER`: The recipient email address for job notifications.
- `EMAIL_PASSWORD`: The password for your email account. (If using Gmail, consider setting up an app-specific password).
- `SMTP_PORT`: The SMTP port for sending emails (default is 587 for Gmail).

## Core Functions

1. **`save_to_csv(job_list, filename="jobs_list.csv")`**
   - **Purpose**: Saves the scraped job listings to a CSV file.
   - **Parameters**:
     - `job_list`: List of job dictionaries to save.
     - `filename`: Name of the CSV file (default is `"jobs_list.csv"`).

2. **`send_email(job_list)`**
   - **Purpose**: Sends an email with the latest job listings.
   - **Parameters**:
     - `job_list`: List of the latest job listings to include in the email.

3. **`filter_job(text)`**
   - **Purpose**: Filters job descriptions based on inclusion (e.g., "Python") and exclusion (e.g., "Hybrid") criteria.
   - **Parameters**:
     - `text`: Job description to filter.
   - **Returns**: `True` if the job meets the criteria, `False` otherwise.

4. **`scrape_jobs()`**
   - **Purpose**: Scrapes job listings from ITViec.
   - **Returns**: A tuple containing:
     - `job_list`: All scraped job listings.
     - `latest_job_list`: Job listings posted within the last 24 hours.

5. **`job_scraper()`**
   - **Purpose**: Main function to scrape, save, and email the latest job listings.

## Scheduling

The script is scheduled to run daily at 09:00 AM local time. To change the scheduled time, adjust the line:
```python
schedule.every().day.at("09:00").do(job_scraper)
```

## Usage

1. **Run the Script**: Uncomment `job_scraper()` at the bottom of the code to initiate the scraping process at the scheduled time.
2. **Automate**: The script will run continuously, scraping job data and sending notifications daily.

## Notes

- Ensure email settings are configured to allow external apps to send emails.
- To adjust the scraping criteria, modify keywords in the `filter_job` function.

## License

This project is open-source and may be modified to suit your specific requirements.
