# Salesforce Project Setup Guide

## Overview
This workspace contains a fully configured Salesforce development environment with:
- **MySalesforceProject**: Your main Salesforce DX project
- Salesforce CLI (v2.97.6) installed
- VS Code Salesforce Extension Pack
- Complete development toolchain (ESLint, Prettier, Jest, Husky)

## Project Structure
```
MySalesforceProject/
├── force-app/main/default/
│   ├── lwc/                    # Lightning Web Components
│   │   └── helloWorld/         # Sample LWC component
│   └── classes/                # Apex classes
│       └── HelloWorldController.cls
├── .vscode/                    # VS Code configuration
├── config/                     # Project configuration
├── scripts/                    # Build and deployment scripts
├── eslint.config.js           # ESLint configuration
├── jest.config.js             # Jest testing configuration
├── package.json               # Node.js dependencies
└── sfdx-project.json          # Salesforce project configuration
```

## Connected Org
- **Alias**: MyDevOrg
- **Username**: riddhiman21012004424@agentforce.com
- **Org ID**: 00DgK000006dgFGUAY
- **Status**: Connected ✅

## Development Workflow

### 1. Create Components
```bash
# Create Lightning Web Component
sf lightning generate component --name myComponent --type lwc --output-dir force-app/main/default/lwc/

# Create Apex Class
sf apex generate class --name MyController --output-dir force-app/main/default/classes/

# Create Apex Trigger
sf apex generate trigger --name MyTrigger --sobject Account --output-dir force-app/main/default/triggers/
```

### 2. Run Tests
```bash
# Run LWC unit tests
npm test

# Run Apex tests
sf apex run test --test-level RunLocalTests
```

### 3. Deploy to Org
```bash
# Deploy specific components
sf project deploy start --source-dir force-app/main/default/lwc/helloWorld/

# Deploy all changes
sf project deploy start

# Deploy and run tests
sf project deploy start --test-level RunLocalTests
```

### 4. Retrieve from Org
```bash
# Retrieve specific metadata
sf project retrieve start --metadata ApexClass:HelloWorldController

# Retrieve all changes
sf project retrieve start
```

## Available Commands

### Development
- `npm test` - Run Jest tests
- `npm run test:unit` - Run unit tests
- `npm run test:unit:watch` - Run tests in watch mode
- `npm run test:unit:debug` - Debug tests
- `npm run test:unit:coverage` - Generate coverage report

### Code Quality
- `npm run lint` - Run ESLint
- `npm run prettier` - Format code with Prettier
- `npm run prettier:verify` - Check code formatting

### Salesforce CLI
- `sf org list` - List connected orgs
- `sf project deploy start` - Deploy to default org
- `sf project retrieve start` - Retrieve from default org
- `sf apex run test` - Run Apex tests
- `sf data query --query "SELECT Id, Name FROM Account LIMIT 10"` - Query data

## VS Code Extensions Installed
- **Salesforce Extension Pack** - Complete Salesforce development toolkit
- **Apex Language Support** - Syntax highlighting and IntelliSense for Apex
- **Lightning Web Components** - LWC development support
- **Visualforce** - Visualforce page development
- **XML Language Support** - XML editing support

## Quick Start Guide

1. **Navigate to your project**:
   ```bash
   cd MySalesforceProject
   ```

2. **Verify connection**:
   ```bash
   sf org list
   ```

3. **Create a new component**:
   ```bash
   sf lightning generate component --name myFirstComponent --type lwc --output-dir force-app/main/default/lwc/
   ```

4. **Run tests**:
   ```bash
   npm test
   ```

5. **Deploy to org**:
   ```bash
   sf project deploy start
   ```

## Next Steps
1. Explore the sample `helloWorld` component in `force-app/main/default/lwc/helloWorld/`
2. Review the `HelloWorldController` Apex class in `force-app/main/default/classes/`
3. Start building your custom components and logic
4. Use the VS Code Command Palette (Ctrl+Shift+P) to access Salesforce commands

## Troubleshooting
- If authentication expires, run: `sf org login web --alias MyDevOrg`
- For permission issues, ensure your user has the necessary permissions in the org
- Check the VS Code Output panel for detailed error messages

## Resources
- [Salesforce DX Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.sfdx_dev.meta/sfdx_dev/)
- [Lightning Web Components Documentation](https://developer.salesforce.com/docs/component-library/documentation/en/lwc)
- [Apex Developer Guide](https://developer.salesforce.com/docs/atlas.en-us.apexcode.meta/apexcode/)