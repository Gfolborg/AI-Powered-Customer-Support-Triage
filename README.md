<p align="center">
<img src="https://i.imgur.com/vt44gaX.png" height="40%" width="40%" alt="AI Automation Project Logo"/>
</p>

<h1>AI-Powered Customer Support Triage</h1>
<p>
This is a mission-critical Intelligent Automation (IA) workflow designed for Customer Support Teams to replace manual ticket handling. The system uses scheduled AI Triage to read and classify unstructured customer complaints, ensuring $100\%$ accuracy in routing and instant notification to the appropriate internal teams via Slack, significantly improving response times.
</p>

<h2>Environments and Technologies Used</h2>

<ul>
    <li>n8n (Workflow Automation)</li>
    <li>Miro (Workflow Design)</li>
    <li>Google Sheets (Data Source/Logging)</li>
    <li>Gemini AI (Triage and Classification)</li>
    <li>Slack API (Conditional Routing and Notification)</li>
</ul>

<h2>High-Level Deployment and Configuration Steps</h2>

<ul>
    <li>Design the end-to-end workflow using Miro to map logic and integration points.</li>
    <li>Configure the scheduled Customer Complaint Generator (Customer Simulation).</li>
    <li>Establish the AI Triage Agent with data integrity filters.</li>
    <li>Integrate Gemini AI for real-time, cognitive complaint classification.</li>
    <li>Set up conditional routing to department-specific Slack channels.</li>
</ul>

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/sbuskG7.png" height="80%" width="80%" alt="Miro Workflow Design Diagram"/>
</p>
<p>
The project began with a detailed workflow design using Miro to establish clear logic, data pathways, and integration modules before implementation in n8n.
</p>
<br />


<h3>Step 1: Configure Simulated Complaint Generator (Scheduled Trigger)</h3>
<p>
<img src="https://i.imgur.com/rwLUOr8.png" height="80%" width="80%" alt="n8n Customer Simulation AI Agent"/>
</p>
<p>
A recurring 15-minute scheduled trigger was set up to simulate real-world traffic. The first Gemini module generated a new Google Sheet row with all customer details (Name, Email, Phone, Complaint), leaving the Issue Type field intentionally blank for the triage agent to classify.
</p>
<br />

<h3>Step 2: Establish Triage Agent Polling and Data Integrity Filters</h3>
<p>
<img src="https://i.imgur.com/a1uzJRI.png" height="100%" width="100%" alt="Triage Agent Polling and Filters"/>
</p>
<p>
A separate, scheduled AI Support Triage Agent was created to poll the Google Sheet for new entries. Critical filters were applied to ensure data integrity and prevent reprocessing:
</p>
<ul>
    <li>The entry form must be complete (all fields filled).</li>
    <li>The Issue Type column must be empty.</li>
</ul>
<br />

<h3>Step 3: Real-Time AI Triage and Classification</h3>
<p>
<img src="https://i.imgur.com/f8kG2F6.png" height="60%" width="60%" alt="Gemini AI Triage and Classification"/>
</p>
<p>
A second Gemini AI module received the new complaint entry. This module was prompted to perform the cognitive task of Issue Triage, accurately classifying the complaint into one of four categories: Billing Issue, Technical Issue, Spam, or Feature Request. The output was structured and validated using a Parse JSON module.
</p>
<br />

<h3>Step 4: Update Google Sheets and Conditional Slack Routing</h3>
<p>
<img src="https://i.imgur.com/oiLhcPC.png, https://i.imgur.com/54K1RMf.png"  height="60%" width="60%" alt="Google Sheets example"/> 
</p>
<p>
<img src="https://i.imgur.com/54K1RMf.png" height="60%" width="60%" alt="Slack messaging example"/>
</p>
<p>
The classified Issue Type was written back to the corresponding row in the Google Sheet. Conditional logic was then applied to route the ticket to the correct, department-specific Slack channel (#billing-issue, #technical-issue, etc.). Each Slack message included a concise, AI-generated summary of the complaint to ensure immediate context and actionability for the receiving team.
</p>
<br />
