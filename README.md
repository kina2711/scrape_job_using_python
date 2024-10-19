# Job Scraper README
# Overview
This project is a job scraping tool designed to extract job listings from itviec.com. It specifically focuses on jobs that include the keyword "Python" while excluding those related to "Hybrid". The scraped data is saved in a CSV file and emailed to a specified recipient on a daily basis.

# Features
- Web Scraping: Extracts job listings from the specified job site using BeautifulSoup.
- Job Filtering: Filters job listings based on predefined criteria.
- Data Storage: Saves the scraped job listings into a CSV file.
- Email Notifications: Sends an email with the latest job listings.
- Scheduling: Runs the job scraping process daily at a specified time.
# Prerequisites
To run this code, ensure you have the following libraries installed:
- requests
- beautifulsoup4
- pytz
- schedule
- smtplib (part of the standard library)
- csv (part of the standard library)
You can install the required libraries using pip:

```
pip install requests beautifulsoup4 pytz schedule
```
# Configuration
Before running the script, update the following configuration variables:

- EMAIL_SENDER: Your email address (the one you will use to send the email).
- EMAIL_RECEIVER: The email address where you want to receive job notifications.
- EMAIL_PASSWORD: The password for your email account (consider using an app-specific password if using Gmail).
- SMTP_PORT: The SMTP port (default is 587 for Gmail).

# Functions
```
save_to_csv(job_list, filename="jobs_list.csv")
```
- Purpose: Saves the scraped job listings to a CSV file.
- Parameters:
  + job_list: List of job dictionaries to save.
  + filename: Name of the CSV file (default is "jobs_list.csv").
```
send_email(job_list)
```
- Purpose: Sends an email with the latest job listings.
- Parameters:
  + job_list: List of the latest job listings to include in the email.
```
filter_job(text)
```
- Purpose: Filters job descriptions based on inclusion and exclusion criteria.
- Parameters:
  + text: Job description to filter.
- Returns: True if the job meets the criteria, False otherwise.
```
scrape_jobs()
```
- Purpose: Scrapes job listings from the specified URL.
- Returns: A tuple containing:
  + job_list: All scraped job listings.
  + latest_job_list: Job listings posted within the last 24 hours.
```
job_scraper()
```
- Purpose: Main function to run the job scraping, save data, and send emails.

# Scheduling
The job scraper is scheduled to run daily at 09:00 AM (local time). You can adjust the time by modifying the schedule.every().day.at("09:00").do(job_scraper) line in the code.

# Usage
To run the script, uncomment the job_scraper() line at the bottom of the code. The script will run indefinitely, executing the scraping process at the scheduled time.

# Notes
- Ensure that your email settings allow for sending emails through the script.
- Adjust the scraping criteria by modifying the CRITERIA dictionary as needed.

# License
This project is open-source and can be modified as per your requirements.
