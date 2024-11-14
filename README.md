---

# Automated Google Sheet Screenshot and Twitter Posting

This project automates the process of capturing a screenshot of a specific Google Sheet, cropping the image, and posting it on Twitter at scheduled times. The script is designed to run on Google Colab, where all dependencies are installed automatically.

## Table of Contents

-   [Features](#features)
-   [Setup and Installation](#setup-and-installation)
-   [Usage Instructions](#usage-instructions)
-   [Configuration](#configuration)
-   [Dependencies](#dependencies)

## Features

-   **Automated Screenshot Capture**: Uses Selenium to capture a screenshot of a specified Google Sheet.
-   **Image Cropping**: Crops the screenshot to a desired region.
-   **Twitter Integration**: Posts the cropped screenshot to Twitter with a customizable tweet text.
-   **Scheduled Posts**: Automates posting at specific times, set up using APScheduler.
-   **Time Zone Scheduling**: Supports posting at specific times in the EST time zone.

## Setup and Installation

1. **Open Google Colab**: Upload this notebook to Google Colab.
2. **Install Dependencies**: Run the first cell to install all required packages.

```python
!pip install selenium opencv-python pytesseract pillow tweepy apscheduler
!apt-get update
!apt install chromium-chromedriver
!cp /usr/lib/chromium-browser/chromedriver /usr/bin
```

> **Note**: These commands are included in the notebook and will be executed automatically in Google Colab.

## Usage Instructions

1. **Configure Parameters**: Update the script parameters such as Twitter API keys, Google Sheet URL, cropping coordinates, and scheduling times (see [Configuration](#configuration)).
2. **Run the Script**: After setting parameters, run the notebook cells sequentially. The script will:

    - Capture a screenshot of the Google Sheet.
    - Crop the screenshot to the specified dimensions.
    - Post the cropped image to Twitter at the scheduled times.

3. **Keep Colab Active**: To ensure the scheduled tasks continue running, keep the Colab session active. Scheduled tweets will continue until the Colab environment is interrupted or stopped.

## Configuration

Modify the following parameters in the code:

-   **Twitter API Credentials**:
    ```python
    consumer_key = "your_consumer_key"
    consumer_secret = "your_consumer_secret"
    access_token = "your_access_token"
    access_token_secret = "your_access_token_secret"
    ```
-   **Screenshot Coordinates**: Define the cropping area by setting these coordinates:

    ```python
    top_left_x, top_left_y, bottom_right_x, bottom_right_y = 110, 160, 1000, 550
    ```

-   **Google Sheet URL**:

    ```python
    sheet_url = 'https://docs.google.com/spreadsheets/...'
    ```

-   **Scheduling Times in EST**:
    ```python
    sched.add_job(scheduled_post, trigger="cron", hour=9, minute=40, timezone=est)
    ```

## Dependencies

This project uses the following libraries:

-   `selenium`: Automates browser actions to capture screenshots.
-   `Pillow`: Crops and processes screenshots.
-   `tweepy`: Integrates with the Twitter API for posting.
-   `apscheduler`: Schedules posting tasks.
-   `pytz`: Manages time zone conversions for scheduling.

All dependencies are installed directly in the notebook.

---
