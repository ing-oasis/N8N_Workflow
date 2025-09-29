## Automated Data Analysis Reporting Workflow

This n8n workflow automates the entire process of generating insightful data analysis reports from raw marketing and subscriber datasets, transforming a labor-intensive, multi-step analytical process into a scalable, automated pipeline. The solution leverages AI to handle tasks from strategic brainstorming to generating and visualizing key performance indicators (KPIs) and actionable insights.

### 📝 **Workflow Overview**

This workflow is divided into three key phases:

1.  **Question Generation:** The workflow dynamically fetches database table schemas and uses an AI Agent to act as a "strategic brainstormer." The AI automatically generates the most valuable business questions a marketing executive would ask based on the available data.
2.  **Question Analysis:** Each generated question is processed individually. A second AI Agent, acting as a "senior marketing data analyst," takes the question and the full datasets as context. It then performs a comprehensive analysis, calculates key metrics, identifies trends, and provides recommendations in a structured JSON format.
3.  **Document Process:** The structured JSON output is parsed by a `Code` node. It extracts the analysis, chart specifications, and descriptions. The workflow then dynamically creates a visual chart using a service like QuickChart and compiles the entire report into a formatted markdown file for easy sharing and viewing. The workflow also includes a conditional check (`If` node) to handle analysis with low confidence levels by asking the AI to re-evaluate the question.

### ✨ **Key Features**

* **Dynamic Data Fetching:** Automatically connects to a database to retrieve table schemas and data.
* **AI-Powered Brainstorming:** Eliminates manual brainstorming by using an AI agent to generate strategic business questions.
* **Automated Analytical Reporting:** Generates detailed reports, complete with insights and recommendations, for each question.
* **Visual Reporting:** Automatically creates charts and visualisations based on AI-generated specifications.
* **Structured Output:** Generates all analysis in a consistent JSON format for reliable parsing and use.
* **Analysis Improvement:** Includes a feedback loop to re-analyze questions if the initial confidence level is low, ensuring high-quality outputs.

---

### ⚙️ **Setup & Prerequisites**

To run this workflow, you will need:

* **n8n Instance:** A running instance of the n8n automation platform.
* **Google Gemini API Key:** This workflow uses Google Gemini for its AI capabilities. You'll need credentials to authenticate the `Google Gemini Chat Model` nodes.
* **NocoDB Instance & API Token:** The workflow connects to a NocoDB database to fetch campaign and subscriber data. Ensure you have the NocoDB API token and the correct workspace/project IDs configured in the `NocoDB` nodes.
* **File System:** The `Read/Write Files from Disk` node saves the final reports. Ensure n8n has the necessary permissions to write to the specified directory.

---

### ▶️ **How to Use**

1.  **Import the Workflow:** Import the `Data_Analyst.json` file into your n8n instance.
2.  **Update Credentials:** Open the workflow and update the credentials for the `Google Gemini` and `NocoDB` nodes with your personal API keys.
3.  **Execute the Workflow:** Click the "Execute Workflow" button to trigger the process. The workflow will automatically proceed through the steps of question generation, analysis, and report creation, saving the final markdown files to your disk.

---

### **Acknowledgements**

This workflow was built using the following tools and services:
* n8n
* Google Gemini
* NocoDB
* QuickChart
