AI-Powered Feedback Analyzer 
This project is an automated workflow built with n8n that captures user 
feedback from a Google Form, analyzes it using the Google Gemini AI, and logs 
the results in a Google Sheet. It's designed to provide instant, actionable 
insights from qualitative feedback without any manual intervention. 
Features 
• Automated Trigger: The workflow starts automatically every time a new 
response is submitted to a Google Form. 
• AI-Powered Analysis: Leverages the Google Gemini API to perform three 
key tasks on the feedback text: 
o Sentiment Analysis: Determines if the feedback is Positive, 
Negative, or Neutral. 
o Summarization: Generates a concise, one-sentence summary of 
the main point. 
o Keyword Extraction: Identifies the most important keywords or 
phrases. 
• Structured Logging: Neatly organizes the original feedback and the AI's 
analysis into a new row in a Google Sheet for easy tracking and 
reporting. 
• Hands-Free Operation: Once activated, the system runs 24/7 in the cloud 
without requiring the n8n window to be open. 
Technology Stack 
• Automation: n8n.io (Cloud Version) 
• AI Model: Google Gemini API 
• Data Input: Google Forms 
• Data Storage: Google Sheets 
• Connector: Google Apps Script 
Workflow Diagram 
The n8n workflow operates in a simple, linear sequence: 
Google Form Submission -> Webhook Node -> Gemini Node -> Code Node -> 
Google Sheets Node 
1. Webhook: Receives the form data from Google Apps Script. 
2. Gemini: Analyzes the feedback text. 
3. Code: Parses the AI's text output into a clean JSON object. 
4. Google Sheets: Appends all the data to the spreadsheet. 
Setup and Installation 
To get this project running, follow these steps: 
1. Prerequisites 
• A Google Account. 
• An n8n.cloud account. 
• A Google AI API Key from Google AI Studio. 
2. Google Setup 
1. Google Form: 
o Create a new Google Form. 
o Add two questions: a "Short answer" question named Name and a 
"Paragraph" question named Your Feedback. 
2. Google Sheet: 
o Create a new Google Sheet. 
o In the first row, create the following headers in columns A through 
F: Timestamp, Name, Feedback, Sentiment, Summary, Keywords. 
3. n8n Workflow Setup 
1. Import Workflow: Download the workflow.json file from this project and 
import it into your n8n canvas. 
2. Configure Credentials: 
o Google Gemini Node: Add your Google AI API Key. 
o Google Sheets Node: Connect your Google Account using OAuth2. 
3. Get Webhook URL: Open the Webhook node. It will have a Test URL. 
Copy this URL for the next step. 
4. Google Apps Script Setup 
1. Open Script Editor: In your Google Form, click the ⋮ menu and select 
Script editor. 
2. Add Code: Delete any placeholder code and paste the code from the 
google-apps-script.js file of this project. 
3. Paste URL: In the script, replace the 
PASTE_YOUR_N8N_WEBHOOK_URL_HERE placeholder with the Test URL 
you copied from the n8n Webhook node. 
4. Save: Save the script project. 
5. Create Trigger: 
o Go to the Triggers section (clock icon). 
o Add a new trigger with the following settings: 
▪ Function to run: onFormSubmit 
▪ Event source: From form 
▪ Event type: On form submit 
o Save the trigger and Allow all permissions when prompted. 
Usage 
1. Testing the Workflow 
1. In n8n, open the Webhook node and click Listen for test event. 
2. Go to your live Google Form and submit a test response. 
3. Verify that the data appears in the n8n Webhook node. 
4. Execute the rest of the nodes one by one to ensure they work correctly 
and that a row is added to your Google Sheet. 
2. Going Live 
1. Activate Workflow: In n8n, click the Inactive toggle to set the workflow 
to Active. 
2. Get Production URL: Copy the new Production URL from the Webhook 
node. 
3. Update Script: Go back to your Google Apps Script and replace the old 
Test URL with the new Production URL. Save the script. 
The system is now fully operational and will process all new form submissions 
automatically. 
USE THIS LINK 
https://docs.google.com/forms/d/e/1FAIpQLScdEkk9oV54tjpAStS5qhhHcHtj1c
 d8aFhj0xaqfo1M5T2T2w/viewform?usp=dialog 
TO FILL INFO IN GOOGLE FORM TO ADD INFO IN GOOGLE SHEET 
