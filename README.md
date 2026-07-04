# 🚀 Enterprise B2B Lead Scoring & Enrichment Pipeline (n8n + AI)

An automated, fault-tolerant n8n architecture designed to scrape, clean, and qualify B2B leads using Large Language Models (LLMs). 

## 📌 The Business Problem
Managing large-scale B2B datasets—such as parsing and filtering contact databases of 5,800+ coffee shops and HoReCa businesses across regional markets like St. Petersburg—reveals a critical bottleneck: **qualification**. Raw scraped data is full of dead links, poorly formatted phone numbers, and irrelevant businesses (e.g., massive chains instead of independent specialty shops). Manual verification takes weeks of monotonous work, and using standard per-task SaaS automation platforms scales poorly and becomes prohibitively expensive[cite: 1].

## 💡 The Solution
This n8n workflow completely automates the qualification process. It takes a raw JSON/CSV feed of businesses, normalizes the contact data, scrapes the target company's website, and utilizes an AI Agent (Google Gemini / Anthropic Claude / OpenAI) to semantically evaluate the business based on a custom prompt[cite: 1].

### ⚙️ Key Architecture Features:
* **Data Cleaning & Regex Normalization:** Custom TypeScript/JavaScript nodes sanitize inputs, removing irrelevant entries and converting phone numbers to strict international formats.
* **Fault-Tolerant Scraping:** The `HTTP Request` node is configured to handle 404s and timeouts gracefully. If a lead's website is dead, the pipeline continues processing the rest of the batch without failing.
* **Semantic HTML Extraction:** Strips heavy, token-consuming HTML tags to pass only clean, readable text to the LLM, significantly reducing API costs.
* **AI-Driven Decision Making:** The LLM strictly outputs a parsed JSON object containing a qualification score (1-10), a logical justification, and chain-status flags[cite: 1].
* **Automated Routing:** A final conditional logic node (`If/Switch`) instantly routes highly qualified, independent leads to a "Hot" branch (ready for CRM insertion) and discards low-quality leads.

## 🛠️ How to Use
1. Clone this repository or download the `Lead_Scoring_Workflow.json` file.
2. Open your self-hosted n8n instance.
3. Click **Import from File** in the top-right menu and select the JSON file.
4. Add your API credentials for the LLM node (Gemini/OpenAI).
5. Execute the workflow to see the mock London coffee shop data processed in real-time.

## 👨‍💻 About the Developer
**Andrew Komovkin**  
*Enterprise n8n Architect & Backend Developer*

I specialize in transitioning B2B businesses from expensive, manual processes to self-hosted, scalable automation ecosystems. My focus is on fault-tolerant workflow architecture, complex API integrations, and deploying Private LLMs and AI Agents directly into business logic[cite: 1].

**Need complex enterprise integration, custom middleware, or a self-hosted n8n deployment?**  
📬 Contact me at: andrykom4@gmail.com
