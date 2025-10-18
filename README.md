# Sign-Up Bot

An automated booking bot for sessions on SignUpGenius.

## Overview

This Python-based automation tool helps automatically sign up for available sessions. The bot uses Selenium WebDriver to navigate the SignUpGenius booking page, find available slots, and complete the registration process.

## Features

- **Automatic Session Detection**: Finds any available "Sign Up" button on the booking page
- **Smart Button Recognition**: Uses multiple methods to locate and click booking buttons
- **Anti-Detection Measures**: Configured to avoid bot detection mechanisms
- **Privacy Popup Handling**: Automatically handles cookie consent dialogs
- **Form Auto-Fill**: Automatically fills in personal information (name, email)
- **reCAPTCHA Detection**: Alerts user when manual verification is needed
- **Comprehensive Logging**: Detailed logs saved to `signup_bot.log`
- **Screenshot Capture**: Saves screenshots at key steps for debugging
- **Headless Mode Support**: Can run with or without visible browser window

## Technology Stack

- **Python 3.x**
- **Selenium WebDriver**: Browser automation
- **ChromeDriver**: Chrome browser control
- **webdriver-manager**: Automatic driver management

## Installation

### Prerequisites

- Python 3.7 or higher
- Google Chrome browser
- Internet connection

### Setup Steps

1. **Clone or download the repository**
   ```bash
   cd C:\Users\franksun\Desktop\python_project\session_booking_bot
   ```

2. **Create a virtual environment (recommended)**
   ```bash
   python -m venv .venv
   .venv\Scripts\activate
   ```

3. **Install required packages**
   ```bash
   pip install selenium webdriver-manager
   ```

## Configuration

Edit the configuration section in `TableTennisSignUpBot.py` (around line 656):

```python
# ========== 配置区域 ==========
FIRST_NAME = "YourFirstName"     # Your first name
LAST_NAME = "YourLastName"       # Your last name
EMAIL = "your.email@ed.ac.uk"    # Your email address
HEADLESS = False                  # False=show browser, True=background mode
# =============================
```

### Configuration Options

- **FIRST_NAME**: Your first name for registration
- **LAST_NAME**: Your last name for registration
- **EMAIL**: Your email address (preferably @ed.ac.uk)
- **HEADLESS**: 
  - `False` - Shows browser window (recommended for first-time use)
  - `True` - Runs in background without GUI

## Usage

### Basic Usage

Run the script directly:

```bash
python TableTennisSignUpBot.py
```

### What Happens

1. Browser opens and navigates to the EUTTC booking page
2. Handles any privacy popups automatically
3. Searches for available "Sign Up" buttons
4. Clicks on the first available session
5. Fills in your personal information
6. Submits the form
7. Verifies the booking was successful
8. Keeps browser open for 10 seconds before closing

## Output Files

The bot generates several files during execution:

### Log Files
- **signup_bot.log**: Detailed execution logs with timestamps

### Screenshots
- **success_YYYYMMDD_HHMMSS.png**: Successful booking confirmation
- **error_*.png**: Error screenshots for debugging
- **no_available_button.png**: When no slots are available
- **debug_page.html**: Page source for debugging (when errors occur)

## How It Works

### Workflow

1. **Initialize Browser**: Sets up Chrome with anti-detection features
2. **Navigate**: Opens the SignUpGenius booking page
3. **Handle Popups**: Dismisses cookie consent dialogs
4. **Find Slots**: Searches for available "Sign Up" buttons using multiple strategies:
   - Exact button text match
   - CSS class-based search
   - AngularJS-aware detection
5. **Click Button**: Uses multiple click methods (regular, JavaScript, AngularJS)
6. **Save & Continue**: Proceeds to the registration form
7. **Fill Form**: Enters name and email information
8. **Submit**: Completes the booking (handles reCAPTCHA if present)
9. **Verify**: Checks for success indicators

### Button Detection Methods

The bot uses three approaches to find available buttons:

1. **Method 1**: Exact match for `<button class="btn-signup">Sign Up</button>`
2. **Method 2**: Loose text matching for buttons containing "Sign Up"
3. **Method 3**: CSS selector-based search for `button.btn-signup`

### Anti-Detection Features

- Custom User-Agent string
- WebDriver property masking
- Realistic window size (1920x1080)
- Human-like delays between actions
- Disabled automation flags


## Code Structure

```
TableTennisSignUpBot.py
├── EUTTCSignUpBot Class
│   ├── __init__()                          # Initialize bot
│   ├── setup_driver()                      # Configure Chrome driver
│   ├── navigate_to_page()                  # Open booking page
│   ├── handle_privacy_popup()              # Handle cookie consent
│   ├── find_any_available_signup_button()  # Locate available slots
│   ├── click_save_and_continue()           # Proceed to form
│   ├── fill_signup_form()                  # Fill personal info
│   ├── check_recaptcha()                   # Detect CAPTCHA
│   ├── submit_form()                       # Submit booking
│   ├── verify_success()                    # Confirm booking
│   └── run()                               # Main execution flow
└── main()                                  # Entry point
```

## License

This is a personal automation tool. Use at your own discretion.

