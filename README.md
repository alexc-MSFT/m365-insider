# M365 Insider

A declarative agent for Microsoft 365 Copilot that searches and returns information from the Microsoft 365 Roadmap. This agent helps users stay informed about upcoming features, recent updates, and planned changes across Microsoft 365 services.

## Overview

M365 Insider is a [declarative agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent) for Microsoft 365 Copilot. Unlike traditional code-based agents, declarative agents are configured through instructions and knowledge sources, making them easy to customize and maintain.

This agent enables users to:
- Search the Microsoft 365 Roadmap for specific features or updates
- Get information about planned, in-development, and released features
- Query by product, timeline, or feature category
- Stay up-to-date with the latest Microsoft 365 announcements

## Features

- **Roadmap Search**: Query the Microsoft 365 Roadmap for features and updates
- **Product Filtering**: Filter roadmap items by specific Microsoft 365 products (Teams, SharePoint, Outlook, etc.)
- **Timeline Awareness**: Find features by their release status (rolling out, in development, launched)
- **Natural Language Queries**: Ask questions in plain English about upcoming Microsoft 365 features

## Prerequisites

Before deploying this agent, ensure you have:

1. **Microsoft 365 Copilot License**: A valid Microsoft 365 Copilot license in your tenant
2. **Visual Studio Code**: [Download VS Code](https://code.visualstudio.com/)
3. **Microsoft 365 Agents Toolkit**: Install the [Microsoft 365 Agents Toolkit extension](https://marketplace.visualstudio.com/items?itemName=OfficeDev.m365-agents-toolkit) for VS Code
4. **Node.js**: LTS version recommended for development tooling
5. **Microsoft 365 Developer Account** (optional): For testing in a sandbox environment

## Quick Start

1. Clone this repository:
   ```bash
   git clone https://github.com/alexc-MSFT/m365-insider.git
   cd m365-insider
   ```

2. Open the project in Visual Studio Code

3. Follow the [Deployment Guide](DEPLOYMENT.md) for detailed setup and deployment instructions

## Usage

Once deployed, you can interact with the M365 Insider agent in Microsoft Copilot:

1. Open Microsoft 365 Copilot at https://m365.cloud.microsoft/chat
2. Access the chat drawer and select the **M365 Insider** agent
3. Ask questions like:
   - "What new features are coming to Microsoft Teams?"
   - "Show me SharePoint updates planned for this quarter"
   - "What's the status of Loop components?"
   - "Find roadmap items related to AI in Outlook"

## Project Structure

```
m365-insider/
├── README.md                 # This file
├── DEPLOYMENT.md             # Detailed deployment instructions
├── LICENSE                   # MIT License
└── appPackage/               # Agent package files (when created)
    ├── manifest.json         # App manifest
    ├── declarativeAgent.json # Agent configuration
    └── instruction.txt       # Agent instructions
```

## Documentation

- [Deployment Guide](DEPLOYMENT.md) - Step-by-step deployment instructions
- [Microsoft 365 Copilot Extensibility](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/) - Official documentation
- [Declarative Agents Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent) - Learn about declarative agents

## Troubleshooting

### Common Issues

**Agent not appearing in Copilot**
- Ensure you have a valid Microsoft 365 Copilot license
- Verify the agent was successfully provisioned and deployed
- Check that sideloading is enabled in your tenant

**Deployment fails**
- Confirm you're signed in with an account that has Copilot access
- Verify all prerequisites are installed
- Check the Teams Toolkit output panel for detailed error messages

**Agent not returning roadmap results**
- The agent queries the public Microsoft 365 Roadmap
- Ensure your network allows access to Microsoft services
- Try rephrasing your query for better results

### Getting Help

If you encounter issues not covered here:
1. Check the [Microsoft 365 Copilot documentation](https://learn.microsoft.com/en-us/microsoft-365-copilot/)
2. Open an issue in this repository
3. Visit the [Microsoft 365 Developer Community](https://developer.microsoft.com/en-us/microsoft-365/)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. For major changes, please open an issue first to discuss what you would like to change.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- [Microsoft 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap) - The data source for this agent
- [Microsoft 365 Copilot Team](https://learn.microsoft.com/en-us/microsoft-365-copilot/) - For the extensibility platform
- [Teams Toolkit](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/teams-toolkit-fundamentals) - For development tooling
