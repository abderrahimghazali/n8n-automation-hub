# 🌐 Drupal Automation Workflows

This folder contains n8n automation workflows specifically designed for Drupal sites. These workflows help automate content publishing, site monitoring, user management, and maintenance tasks.

## 📋 Available Workflows

### Content Management
- **📝 Auto Content Publisher** ([Setup Guide](📝%20Auto%20Content%20Publisher%20-%20Setup%20Guide.md) | [Workflow](📝%20Auto%20Content%20Publisher%20-%20Google%20Sheets%20to%20Drupal.txt)) - Automatically publish content from Google Sheets to Drupal

### Site Monitoring & Maintenance
- **🔍 Site Health Monitor** ([Setup Guide](🔍%20Site%20Health%20Monitor%20-%20Setup%20Guide.md) | [Workflow](🔍%20Site%20Health%20Monitor%20-%20Uptime%20and%20Performance.txt)) - Monitor site uptime, performance, and security
- **🛡️ Security Scanner** ([Setup Guide](🛡️%20Security%20Scanner%20-%20Setup%20Guide.md) | [Workflow](🛡️%20Security%20Scanner%20-%20Vulnerability%20Detection.txt)) - Automated security checks and vulnerability alerts

## 🚀 Getting Started

### Prerequisites
- n8n instance (cloud or self-hosted)
- Drupal site with REST API enabled
- Appropriate API keys and credentials
- Basic understanding of Drupal content types and fields

### Authentication Setup
Most workflows require Drupal REST API authentication. You'll need:
1. **Basic Auth**: Username and password
2. **OAuth2**: For more secure implementations
3. **API Token**: Custom authentication tokens

### Common Configuration
1. **Base URL**: Your Drupal site's base URL
2. **Content Types**: Configure your Drupal content types
3. **Field Mappings**: Map fields between external sources and Drupal
4. **User Permissions**: Ensure proper API permissions

## 📖 Workflow Documentation

Each workflow file contains:
- Complete n8n workflow JSON
- Detailed setup instructions
- Configuration examples
- Troubleshooting guides
- Use case scenarios

## 🔧 Customization

All workflows are designed to be easily customizable for your specific:
- Content types and fields
- User roles and permissions
- Site structure and taxonomy
- Custom modules and functionality

## 📞 Support

For questions about these workflows:
- Check individual workflow documentation
- Review Drupal REST API documentation
- Test workflows in a development environment first

---
*These workflows are provided as starting points and may need customization for your specific Drupal setup and requirements.* 