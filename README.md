# Email Unsubscribe Automation Project

## Overview
This project automates the process of unsubscribing from emails by:
1. Fetching emails containing unsubscribe links.
2. Extracting and visiting the links to automate unsubscription.

It uses:
- **Python** for automation.
- **IMAP** to connect to the email server.
- **BeautifulSoup** to parse HTML content.
- **requests** to visit the unsubscribe links.

---

## Features
- **Email Connection**:
  - Connects to a Gmail inbox using credentials stored in an `.env` file.
  - Fetches emails containing the keyword "unsubscribe."

- **HTML Parsing**:
  - Extracts unsubscribe links from email content using BeautifulSoup.

- **Link Automation**:
  - Visits each unsubscribe link using HTTP requests.
  - Logs success or failure for each link.

- **Data Storage**:
  - Saves unsubscribe links to a `links.txt` file.

---

## Project Files

### 1. `.env`
Stores sensitive information securely (excluded from the repository using `.gitignore`):
```plaintext
EMAIL = "your-email@example.com"
PASSWORD = "your-app-password"
```

### 2. `.gitignore`
Ensures the `.env` file is not uploaded to GitHub:
```plaintext
.env
```

### 3. `links.txt`
Stores extracted unsubscribe links for reference:
```plaintext
https://example.com/unsubscribe-link1
https://example.com/unsubscribe-link2
```

### 4. `main.py`
The main script for automation:
- Connects to the email server using `imaplib`.
- Searches for emails with "unsubscribe" in their content.
- Parses HTML content to find unsubscribe links.
- Saves links to `links.txt` and attempts to visit them.

#### Key Functions:
- **`connect_to_mail()`**: Establishes an IMAP connection to the Gmail inbox.
- **`search_emails(limit=10)`**: Searches for emails and extracts unsubscribe links.
- **`get_links_from_html(html_content)`**: Parses HTML for unsubscribe links.
- **`click_link(link)`**: Sends HTTP GET requests to visit links.
- **`save_links(links)`**: Writes unsubscribe links to a file.

---

## How to Run the Project

1. **Setup**:
   - Clone the repository.
   - Install required Python packages:
     ```bash
     pip install python-dotenv beautifulsoup4 requests
     ```
   - Create a `.env` file in the root directory with your email credentials:
     ```plaintext
     EMAIL = "your-email@example.com"
     PASSWORD = "your-app-password"
     ```

2. **Run the Script**:
   - Execute the main script:
     ```bash
     python main.py
     ```

3. **View Results**:
   - Check `links.txt` for saved links.
   - Monitor the console for logs about visited links.

---

## Example Output
### Console Logs:
```plaintext
successfully visited https://example.com/unsubscribe-link1
failed to visit https://example.com/unsubscribe-link2 error code: 404
```

### `links.txt`:
```plaintext
https://example.com/unsubscribe-link1
https://example.com/unsubscribe-link2
```

---

## Use Cases
- Automate email unsubscriptions for personal or organizational accounts.
- Clean up inboxes to reduce spam and irrelevant emails.

---

## Limitations
- The script currently works only with Gmail.
- Requires app passwords if two-factor authentication is enabled.
- Relies on unsubscribe links being present in the email content.

---

## Future Improvements
- Add support for other email providers (e.g., Yahoo, Outlook).
- Enhance error handling and logging.
- Implement a UI for easier configuration and monitoring.

---

## Contact
For questions or suggestions, contact: benghazighassen12@gmail.com
