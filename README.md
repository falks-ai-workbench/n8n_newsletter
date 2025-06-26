## n8n Newsletter Project

This project automates the process of collecting, rating, and sending newsletter articles using n8n. It integrates RSS feeds, AI-based article rating and summarization, and automated email delivery.

### **Workflow Overview**

The workflow is divided into three main sections:

#### 1. Set Your RSS Feed and Interests

- **Configure RSS Feed:** Set up your RSS feed in the RSS Feed node. Double-check settings to ensure all needed columns are included.
- **User Preferences:** Adjust your interests in the "Set Userprompt" node.
- **Database Setup:** The workflow automatically creates the database and schema if they do not exist.
- **Word Count:** Counts the number of words in each article.
- **Compare Datasets:** Checks if an article has already been used in previous newsletters to avoid duplicates.


#### 2. Rate Articles, Summarize, and Filter

- **AI Rating:** Articles are rated and tagged using an AI model (e.g., QWEN 14B-s4).
- **Filter by Score:** Only articles with a rating of 7 or higher are kept for the newsletter.
- **Summarization:** High-rated articles are summarized using a language model (e.g., Gemma3 4B).
- **Data Merging:** Summarized articles are merged with RSS data for final processing.


#### 3. Prepare and Send Newsletter

- **Insert Records:** Articles are inserted into the database, separated by those below and above the rating threshold.
- **Email Formatting:** High-rated articles are formatted into an HTML email.
- **Send Newsletter:** The formatted newsletter is sent via Gmail using OAuth2 credentials.

### **Installation Instruction**
- **Install n8n via Docker:** https://www.youtube.com/watch?v=dC2Q_cyzgjg&t=331s
- **Install Ollama (via Docker):** https://github.com/ollama/ollama
- **Download & Upload Newsletter_Automation.json:** Or create a new workflow in n8n and copy&paste the json file.

### **Setup Instructions**

1. **Clone or Import the Workflow:**
Import this workflow into your n8n instance.
2. **Configure Credentials:**
    - Set up your Postgres credentials.
    - Add your Google OAuth2 credentials for Gmail.
3. **Set RSS Feed and Preferences:**
    - Enter your desired RSS feed URL.
    - Adjust user preferences as needed in the workflow.
4. **Run the Workflow:**
Click "Execute workflow" in n8n to start the process.

### **Customization**

- **AI Models:**
You can swap out the default AI models (QWEN 14B-s4, Gemma3 4B) for your own local or cloud models if desired.
- **Email Address:**
Change the recipient email address in the final email node.


### **Notes**

- Only articles rated 7 or higher are included in the newsletter.
- The workflow avoids sending duplicate articles by checking against previous records.
- Make sure to update all credentials and configuration nodes before running.
