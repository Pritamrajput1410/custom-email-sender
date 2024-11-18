CustomEmailSender
A comprehensive email-sending and tracking system that integrates with SendGrid to provide features like scheduling, real-time analytics, and delivery tracking via a dashboard.

Features
Email Sending: Schedule and send emails with support for throttling.
Analytics Dashboard: View email statuses (Sent, Scheduled, Pending, Failed) and delivery tracking (Delivered, Opened, Bounced).
Integration with SendGrid: Track email delivery, opens, bounces, and failures using the SendGrid API and webhooks.
Real-Time Dashboard: Frontend interface to visualize email statuses and analytics.
File Structure
plaintext
Copy code
CustomEmailSender/
│
├── main.py                # Main script for execution
├── data/                  
│   ├── __init__.py        # Empty init file
│   ├── data_loader.py     # File for loading data (CSV or Google Sheets)
├── email/
│   ├── __init__.py        # Empty init file
│   ├── email_integration.py  # Email connection and sending functionality
├── llm/
│   ├── __init__.py        # Empty init file
│   ├── llm_api.py         # Interface with Groq API for content generation
├── scheduler/
│   ├── __init__.py        # Empty init file
│   ├── email_scheduler.py # Email scheduling and throttling
├── analytics_dashboard.py # Provides real-time email analytics
├── analytics_db.py        # Database operations for email analytics
├── ESP/
│   ├── models.py          # Defines database models for SendGrid events
│   ├── webhook.py         # Handles webhook events from SendGrid
│   ├── app.py             # API server for frontend
├── templates/
│   ├── index.html         # Email status dashboard (Frontend)
├── static/
│   ├── style.css          # Basic CSS for the dashboard
├── venv/                  # Virtual environment (auto-created)
├── .env                   # Stores environment variables
├── requirements.txt       # Dependencies for the project
Setup Instructions
1. Clone the Repository
bash
Copy code
git clone https://github.com/your-username/CustomEmailSender.git
cd CustomEmailSender
2. Set Up a Virtual Environment
bash
Copy code
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
3. Install Dependencies
bash
Copy code
pip install -r requirements.txt
4. Create a .env File
Add the following environment variables to a .env file:

env
Copy code
SENDGRID_API_KEY=your_sendgrid_api_key
DATABASE_URL=sqlite:///email_tracking.db
FLASK_ENV=development
5. Initialize the Database
Run the following commands to set up the database:

bash
Copy code
python analytics_db.py  # Initializes analytics database
python ESP/models.py    # Initializes SendGrid event tracking database
6. Run the Application
Start the main application:

bash
Copy code
python main.py
Usage
1. Sending Emails
Emails are scheduled using the email_scheduler.py script.
Ensure that the .csv or Google Sheets file is correctly loaded via data_loader.py.
2. Tracking Emails
The SendGrid webhook receives real-time updates about email delivery statuses.
These updates are processed and stored in the database for visualization.
3. Access the Dashboard
Open http://127.0.0.1:5000 in your browser.
The dashboard provides real-time insights into:
Email Sending Status: Sent, Scheduled, Pending, Failed.
Delivery Metrics: Delivered, Opened, Bounced.
Technologies Used
Python: Core application logic.
Flask: Backend server for dashboard.
SQLite: Database for analytics and event tracking.
SendGrid API: Email delivery tracking and webhook integration.
HTML/CSS: Frontend dashboard for real-time analytics.
Contributing
Feel free to fork this repository and submit pull requests. Contributions are welcome!

License
This project is licensed under the MIT License.

