# Deployment Guide

This guide provides step-by-step instructions for deploying the M365 Insider declarative agent to your Microsoft 365 tenant.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Environment Setup](#environment-setup)
- [Project Configuration](#project-configuration)
- [Provisioning](#provisioning)
- [Deployment](#deployment)
- [Testing](#testing)
- [Updating the Agent](#updating-the-agent)
- [Uninstalling](#uninstalling)

## Prerequisites

### Required

1. **Microsoft 365 Copilot License**
   - You must have an active Microsoft 365 Copilot license assigned to your account
   - Government cloud tenants may have limited functionality

2. **Visual Studio Code**
   - Download from [https://code.visualstudio.com/](https://code.visualstudio.com/)
   - Ensure you have the latest stable version

3. **Microsoft 365 Agents Toolkit Extension**
   - Open VS Code
   - Go to Extensions (Ctrl+Shift+X)
   - Search for "Microsoft 365 Agents Toolkit"
   - Install the extension by Microsoft

4. **Node.js** (LTS version)
   - Download from [https://nodejs.org/](https://nodejs.org/)
   - Verify installation: `node --version`

### Optional

- **Microsoft 365 Developer Subscription**: A sandbox environment for testing
- **Teams Toolkit CLI**: For command-line deployments

## Environment Setup

### Step 1: Install Visual Studio Code Extensions

1. Open Visual Studio Code
2. Navigate to the Extensions view (Ctrl+Shift+X or Cmd+Shift+X on Mac)
3. Install the following extensions:
   - **Microsoft 365 Agents Toolkit** (required)
   - **Teams Toolkit** (recommended)

### Step 2: Sign In to Microsoft 365

1. Open the Microsoft 365 Agents Toolkit sidebar in VS Code
2. Click **Sign in to Microsoft 365**
3. Complete the authentication flow in your browser
4. Verify your account shows as connected with Copilot access

### Step 3: Enable Sideloading (if needed)

For development and testing, sideloading must be enabled in your tenant:

1. Go to [Microsoft 365 Admin Center](https://admin.microsoft.com)
2. Navigate to **Settings** > **Org settings** > **Services**
3. Select **Microsoft Teams**
4. Enable **Allow users to upload custom apps**

> **Note**: This step may require tenant admin permissions.

## Project Configuration

### Agent Manifest

The agent is configured through the following files in the `appPackage` directory:

| File | Purpose |
|------|---------|
| `manifest.json` | App metadata, permissions, and configuration |
| `declarativeAgent.json` | Agent-specific settings and capabilities |
| `instruction.txt` | Natural language instructions for the agent |

### Customizing the Agent

To modify the agent's behavior:

1. Edit `appPackage/instruction.txt` to change how the agent responds
2. Update `appPackage/declarativeAgent.json` to modify knowledge sources or actions
3. Adjust `appPackage/manifest.json` for app metadata changes (name, description, icons)

## Provisioning

Provisioning creates the necessary cloud resources for your agent.

### Using VS Code

1. Open this project in Visual Studio Code
2. Open the Microsoft 365 Agents Toolkit sidebar
3. Under **Lifecycle**, click **Provision**
4. Select your target environment (local or dev)
5. Wait for provisioning to complete

### Using CLI (Alternative)

```bash
# Install the CLI globally
npm install -g @microsoft/teamsapp-cli

# Provision resources
teamsapp provision --env dev
```

### Provisioning Output

After successful provisioning, you'll see:
- A confirmation message in the terminal
- Updated environment files with resource IDs
- The agent registered in your Microsoft 365 tenant

## Deployment

Deployment publishes your agent to Microsoft 365 Copilot.

### Using VS Code

1. In the Microsoft 365 Agents Toolkit sidebar
2. Under **Lifecycle**, click **Deploy**
3. Select your target environment
4. Wait for deployment to complete

### Using CLI (Alternative)

```bash
teamsapp deploy --env dev
```

### Verifying Deployment

After deployment:
1. Navigate to [Microsoft 365 Copilot](https://m365.cloud.microsoft/chat)
2. Open the chat drawer (right panel)
3. Look for **M365 Insider** in the list of available agents

## Testing

### Basic Testing

1. Open Microsoft 365 Copilot at https://m365.cloud.microsoft/chat
2. Select the **M365 Insider** agent from the chat drawer
3. Try these sample queries:
   - "What's new in Microsoft Teams?"
   - "Show me upcoming SharePoint features"
   - "What features are rolling out this month?"

### Expected Responses

The agent should:
- Acknowledge your query
- Search the Microsoft 365 Roadmap
- Return relevant feature information
- Provide links to roadmap items when available

### Debugging

If the agent isn't working as expected:

1. **Check the Output Panel**
   - In VS Code, open View > Output
   - Select "Microsoft 365 Agents Toolkit" from the dropdown
   - Look for error messages

2. **Review Logs**
   - Check the Teams Toolkit logs in `.log` files
   - Look for authentication or permission errors

3. **Test Locally**
   - Use the local debug configuration
   - Set breakpoints in your instructions
   - Monitor the debug console

## Updating the Agent

To update a deployed agent:

1. Make your changes to the agent files
2. Run **Deploy** again from the Toolkit
3. The agent will be updated in-place

### Version Management

For significant updates:
1. Update the version number in `manifest.json`
2. Document changes in a changelog
3. Deploy the new version

## Uninstalling

### Remove from Your Account

1. Go to Microsoft 365 Copilot
2. Open the agent drawer
3. Find M365 Insider
4. Click the options menu (...)
5. Select **Remove**

### Remove from Tenant (Admin)

1. Go to [Teams Admin Center](https://admin.teams.microsoft.com)
2. Navigate to **Teams apps** > **Manage apps**
3. Search for "M365 Insider"
4. Delete the app

## Additional Resources

- [Microsoft 365 Copilot Extensibility Documentation](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/)
- [Declarative Agents Overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)
- [Build Declarative Agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents)
- [Microsoft 365 Agents Toolkit Wiki](https://github.com/OfficeDev/microsoft-365-agents-toolkit/wiki)
- [Microsoft 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap)

## Support

If you encounter issues:

1. Check the [Troubleshooting section](README.md#troubleshooting) in the README
2. Search existing [GitHub Issues](https://github.com/alexc-MSFT/m365-insider/issues)
3. Open a new issue with:
   - Your environment details
   - Steps to reproduce
   - Error messages or logs
   - Screenshots if applicable
