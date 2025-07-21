# Business-Document-Processing-Workflow-with-n8n

***Developed by: PHILIP SIMON DEROCK P***

An advanced AI-powered automation workflow built with n8n that automatically processes business documents (PDFs) using Google Drive integration and Mistral models to generate comprehensive document analysis and summaries.

## 🚀 Project Overview

This sophisticated workflow automatically monitors a Google Drive folder for new PDF uploads, extracts and processes the document content through multiple AI analysis agents, and generates a structured summary document with key insights, takeaways, and recommendations.

### Key Features

- **Automated PDF Processing**: Monitors Google Drive folders for new PDF uploads
- **Multi-Agent AI Analysis**: Processes documents through 7 specialized AI agents
- **Comprehensive Document Summaries**: Generates structured analysis including themes, takeaways, gaps, and follow-up questions
- **Google Workspace Integration**: Creates formatted Google Docs with analysis results
- **Intelligent File Management**: Automatically organizes processed files into appropriate folders
- **Batch Processing**: Handles multiple documents simultaneously with loop controls

## 🏗️ Architecture

### Workflow Components

```

Google Drive Trigger → PDF Download → Text Extraction → Multi-Agent AI Processing → Document Generation → File Organization

```

### AI Processing Pipeline

The workflow employs **7 specialized AI agents** that analyze different aspects of the document:

1. **Main Theme Agent**: Identifies primary topics, purpose, and target audience
2. **Document Summary Agent**: Creates section-by-section structured summaries  
3. **Key Takeaways Agent**: Extracts 3-7 most important insights and conclusions
4. **Gaps & Limitations Agent**: Identifies weaknesses, omissions, and assumptions
5. **Follow-Up Questions Agent**: Generates thoughtful questions for deeper exploration
6. **Terminology Clarification Agent**: Explains complex terms and jargon
7. **Structural Analysis Agent**: Evaluates document organization and formatting

## 🛠️ Technical Stack

- **Automation Platform**: n8n (Node-based workflow automation)
- **AI Model**: OpenAI GPT-4.1-mini with structured output parsing
- **Cloud Storage**: Google Drive API integration
- **Document Processing**: Google Docs API for output generation
- **File Processing**: Native PDF text extraction capabilities

## ⚙️ Setup Instructions

### Prerequisites

- n8n instance (self-hosted or cloud)
- Google Drive API credentials
- Google Docs API credentials  
- OpenAI API key
- Administrative access to target Google Drive folders

### Required Credentials

Configure the following credential connections in n8n:

```

Required Credentials:

- googleDriveOAuth2Api: "Google Drive account"
- googleDocsOAuth2Api: "Google Docs account"
- openAiApi: "OpenAI API access"

```

### Google Drive Folder Structure

Set up the following folder hierarchy in Google Drive:

```

📁 PDF Processing System/
├── 📁 PDF_INPUT/ (ID: 1geU5SC7m4AWGGh5HzMYEluOGwrdlJIHA)
├── 📁 PDF Summaries/ (ID: 10fpnPZY65ecHpyYM6jzRW482UXLGc_8w)
└── 📁 Finished Processing PDF Files/ (ID: 1KCeFtVVLJWS_37-sPCNvUvSpxlnRAHbW)

```

### Installation Steps

1. **Import Workflow**
```

Import the pdf_agent.json file into your n8n instance

```

2. **Configure Credentials**
- Add Google Drive OAuth2 credentials
- Add Google Docs OAuth2 credentials
- Add OpenAI API credentials

3. **Update Folder IDs**
- Replace folder IDs in the workflow with your actual Google Drive folder IDs
- Update the `folderToWatch` parameter in the Google Drive trigger

4. **Activate Workflow**
- Enable the workflow in n8n
- Set trigger to monitor the input folder

## 🔧 Configuration

### Google Drive Trigger Settings

```

{
"triggerOn": "specificFolder",
"folderToWatch": "1geU5SC7m4AWGGh5HzMYEluOGwrdlJIHA",
"event": "fileCreated",
"pollTimes": {
"mode": "everyMinute"
}
}

```

### OpenAI Model Configuration

```

{
"model": "gpt-4.1-mini",
"options": {}
}

```

### Document Template Structure

The workflow generates Google Docs with the following sections:

- **Main Theme**: Document purpose and target audience
- **Document Summary**: Section-by-section breakdown
- **Key Takeaways**: Important insights and conclusions
- **Gaps & Limitations**: Identified weaknesses and omissions  
- **Follow-Up Questions**: Suggested areas for deeper investigation
- **Terminology Clarification**: Definitions of complex terms
- **Structural Observations**: Document organization analysis

## 🚀 Usage

### Basic Operation

1. **Upload PDF**: Drop any PDF file into the monitored Google Drive folder
2. **Automatic Processing**: Workflow triggers automatically and processes the document
3. **Analysis Generation**: AI agents analyze different aspects of the document
4. **Summary Creation**: Comprehensive Google Doc summary is generated
5. **File Organization**: Original PDF is moved to "Finished Processing" folder

### Advanced Features

- **Batch Processing**: Handles multiple PDFs uploaded simultaneously via loop controls
- **Error Handling**: Includes dual-loop architecture for reliability
- **Structured Output**: All AI responses use JSON schema validation
- **File Naming**: Generated summaries maintain original filename with "PDF Summary" suffix

## 📊 Output Format

### Generated Summary Structure

Each processed document produces a Google Doc containing:

```


# [Original Filename]

## Main Theme

[AI-generated theme analysis]

## Document Summary

📌 Section 1: [Content summary]
📌 Section 2: [Content summary]

## Key Takeaways

- Point 1: [Context and explanation]
- Point 2: [Context and explanation]


## Gaps \& Limitations

- Issue 1: [Significance explanation]
- Issue 2: [Significance explanation]


## Follow-Up Questions

?? Question 1
?? Question 2

## Terminology To Clarify

- Term 1: [Definition]
- Term 2: [Definition]


## Document Structural Observations

- Observation 1
- Observation 2

```

## 🔍 Monitoring & Debugging

### Workflow Execution

Monitor workflow execution through n8n's interface:

- **Execution History**: Track successful and failed runs
- **Node Outputs**: Inspect data flow between nodes
- **Error Logs**: Identify and resolve processing issues

### Common Issues

| Issue | Cause | Solution |
|-------|--------|----------|
| Trigger not firing | Incorrect folder permissions | Verify Google Drive folder access |
| PDF extraction fails | Corrupted or password-protected PDF | Ensure PDFs are accessible and not encrypted |
| AI processing errors | API rate limits or invalid responses | Check OpenAI API quotas and response formats |
| Google Doc creation fails | Insufficient permissions | Verify Google Docs API access and folder permissions |

## 🛡️ Security Considerations

- **API Keys**: Store all API credentials securely in n8n's credential manager
- **Folder Permissions**: Restrict Google Drive folder access to authorized users only  
- **Data Privacy**: Consider data residency requirements for sensitive documents
- **Access Logging**: Monitor API usage and document access patterns

## 🔧 Customization Options

### AI Agent Modifications

Each AI agent can be customized by modifying the `systemMessage` parameter:

- **Adjust Analysis Depth**: Modify prompts for more detailed or concise analysis
- **Domain Specialization**: Tailor agents for specific document types (legal, technical, financial)
- **Output Format Changes**: Modify JSON schemas for different output structures

### Integration Extensions

- **Slack Notifications**: Add Slack webhook for processing completion alerts
- **Email Reports**: Integrate email nodes for summary distribution
- **Database Storage**: Store analysis results in databases for reporting
- **Custom Workflows**: Extend processing based on document classification

## 📈 Performance Optimization

### Batch Processing Configuration

The workflow includes two loop controls:
- **Loop Over Items**: Primary batch processing loop
- **2nd Loop Over Items**: Secondary processing loop for reliability

### Resource Management

- **Concurrent Executions**: Limit simultaneous workflow runs to prevent API throttling
- **Timeout Settings**: Configure appropriate timeouts for long document processing
- **Memory Management**: Monitor n8n instance resources during large file processing

## 🤝 Contributing

### Development Setup

1. Fork the repository
2. Create feature branch: `git checkout -b feature/amazing-feature`
3. Import workflow into development n8n instance
4. Test changes thoroughly
5. Submit pull request with detailed description

### Code Standards

- **Node Naming**: Use descriptive names for all workflow nodes
- **Error Handling**: Implement proper error handling and recovery
- **Documentation**: Update README for any configuration changes
- **Testing**: Test with various PDF types and sizes

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

For support and questions:

- **Issues**: Create GitHub issue with detailed description
- **Documentation**: Refer to n8n official documentation
- **Community**: Join n8n community forums
- **API Support**: Consult OpenAI and Google API documentation

## 📊 Changelog

### Version 1.0.0
- Initial release with full PDF processing pipeline
- Multi-agent AI analysis implementation
- Google Drive and Docs integration
- Automated file organization system
- Dual-loop batch processing architecture

---

