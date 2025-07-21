# Business-Document-Processing-Workflow-with-n8n

***Developed by: PHILIP SIMON DEROCK P***

An advanced Mistral-powered automation workflow built with n8n that automatically processes business documents (PDFs) using Google Drive integration and Mistral models to generate comprehensive document analysis and summaries.

## 🚀 Project Overview

This sophisticated workflow automatically monitors a Google Drive folder for new PDF uploads, extracts and processes the document content through multiple Mistral-based analysis agents, and generates a structured summary document with key insights, takeaways, and recommendations.

### Key Features

- **Automated PDF Processing**: Monitors Google Drive folders for new PDF uploads  
- **Multi-Agent Mistral Analysis**: Processes documents through 7 specialized Mistral agents  
- **Comprehensive Document Summaries**: Generates structured analysis including themes, takeaways, gaps, and follow-up questions  
- **Google Workspace Integration**: Creates formatted Google Docs with analysis results  
- **Intelligent File Management**: Automatically organizes processed files into appropriate folders  
- **Batch Processing**: Handles multiple documents simultaneously with loop controls  

## 🏗️ Architecture

### Workflow Components

Google Drive Trigger → PDF Download → Text Extraction → Multi-Agent Mistral Processing → Document Generation → File Organization

### Mistral Processing Pipeline

The workflow employs **7 specialized Mistral agents** that analyze different aspects of the document:

1. **Main Theme Agent**
2. **Document Summary Agent**
3. **Key Takeaways Agent**
4. **Gaps & Limitations Agent**
5. **Follow-Up Questions Agent**
6. **Terminology Clarification Agent**
7. **Structural Analysis Agent**

## 🛠️ Technical Stack

- **Automation Platform**: n8n  
- **Language Model**: Mistral API  
- **Cloud Storage**: Google Drive API  
- **Document Processing**: Google Docs API  
- **File Processing**: PDF text extraction  

## ⚙️ Setup Instructions

### Prerequisites

- n8n instance  
- Google API credentials  
- Mistral API key  
- Google Drive access  

### Required Credentials

- googleDriveOAuth2Api  
- googleDocsOAuth2Api  
- mistralApi  

### Google Drive Folder Structure

📁 PDF Processing System/  
├── 📁 PDF_INPUT/  
├── 📁 PDF Summaries/  
└── 📁 Finished Processing PDF Files/  

### Installation Steps

1. Import the workflow  
2. Configure credentials  
3. Update folder IDs  
4. Activate the workflow  

## 🔧 Configuration

### Trigger and Model Settings

Drive trigger: everyMinute on new file  
Model: mistral-7b-instruct

## 🚀 Usage

1. Upload PDF  
2. Auto processing  
3. Summary generation  
4. File organization  

## 📊 Output Format

Includes sections like:

- Main Theme  
- Summary  
- Key Takeaways  
- Gaps & Limitations  
- Follow-Up Questions  
- Terminology  
- Observations  

## 🔍 Monitoring & Debugging

Use n8n's execution history, node outputs, and error logs.

## 🛡️ Security

- Secure API keys  
- Limit folder access  
- Monitor API usage  

## 🔧 Customization

Modify prompts and output schema for agents. Extend via Slack, email, database.

## 📈 Optimization

Batch loops, timeout settings, memory monitoring.

## 🤝 Contributing

- Fork, branch, test, and submit PR  
- Use descriptive node names  
- Include error handling and documentation  

## 📝 License

MIT License

## 🆘 Support

Use GitHub issues, n8n docs, community, and API docs.

## 📊 Changelog

v1.0.0 - Initial release with full workflow
