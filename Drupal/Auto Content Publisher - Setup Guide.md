# 📝 Auto Content Publisher - Google Sheets to Drupal

## Overview
This workflow automatically reads content from Google Sheets and publishes it to your Drupal site using the REST API. Perfect for content teams who want to manage their editorial calendar in spreadsheets while maintaining automated publishing.

## Features
- **Automated Publishing**: Runs every hour to check for new content
- **Status Tracking**: Updates Google Sheets with publication status
- **Error Handling**: Logs errors and failed publications
- **Slack Notifications**: Notifies team when content is published
- **Flexible Content Types**: Supports any Drupal content type

## Required Google Sheets Structure

### Content_Queue Sheet
| Column | Type | Description | Example |
|--------|------|-------------|---------|
| row_id | Text | Unique identifier | content_001 |
| title | Text | Content title | "How to Use Drupal" |
| body | Text | Main content body | Full HTML content |
| summary | Text | Content summary | Brief description |
| content_type | Text | Drupal content type | article |
| tags | Text | Comma-separated tags | drupal,cms,tutorial |
| featured_image | Number | Media entity ID | 123 |
| publish_status | Text | Publication status | published/draft |
| status | Text | Queue status | ready/published/error |
| drupal_node_id | Number | Created node ID | (auto-filled) |
| drupal_url | URL | Published URL | (auto-filled) |
| published_at | Date | Publication timestamp | (auto-filled) |
| error_message | Text | Error details | (auto-filled) |

## Setup Instructions

### 1. Drupal Configuration

#### Enable Required Modules
```bash
drush en rest restui serialization basic_auth hal jsonapi -y
```

#### Configure REST Resources
1. Go to `/admin/config/services/rest`
2. Enable the Node resource
3. Set methods: GET, POST, PATCH, DELETE
4. Set formats: json
5. Set authentication: basic_auth

#### Create User Account
1. Create a user with appropriate permissions
2. Grant permissions:
   - "Access REST API"
   - "Create content of [your content type]"
   - "Edit own content"
   - "Use REST API for node entities"

### 2. n8n Configuration

#### Required Credentials
1. **Google Sheets OAuth2 API**
2. **Drupal Basic Auth** (username/password)
3. **Slack API** (optional for notifications)

#### Node Configuration
1. Replace `YOUR_GOOGLE_SHEET_ID` with your sheet ID
2. Update Drupal base URL
3. Configure content type mappings
4. Set up field mappings for your content structure

### 3. Field Mapping Customization

The workflow maps common fields, but you can customize for your content type:

```javascript
{
  "type": [{"target_id": $json.content_type}],
  "title": [{"value": $json.title}],
  "body": [{"value": $json.body, "format": "full_html"}],
  "field_custom_field": [{"value": $json.custom_data}],
  // Add your custom fields here
}
```

## Workflow Steps

1. **Schedule Trigger**: Runs every hour
2. **Google Sheets**: Reads content queue
3. **Filter Ready Content**: Only processes items with status "ready"
4. **Map Content**: Transforms data for Drupal API
5. **Create Drupal Node**: Posts to Drupal REST API
6. **Check Response**: Validates creation success
7. **Update Sheet**: Records success/error status
8. **Slack Notification**: Notifies team of publications

## Content Types Support

### Article (Default)
- Title
- Body
- Summary
- Tags
- Featured Image

### Custom Content Types
Modify the mapping section to include your fields:

```javascript
"field_your_custom_field": [{
  "value": $json.your_sheet_column
}]
```

## Status Management

### Content Queue Statuses
- **ready**: Ready for publishing
- **published**: Successfully published
- **error**: Failed to publish
- **draft**: Not ready for publishing

### Workflow Process
1. Add content to Google Sheets with status "ready"
2. Workflow automatically processes every hour
3. Status updates to "published" or "error"
4. Team gets notified via Slack

## Error Handling

### Common Issues
- **Authentication Failed**: Check Drupal credentials
- **Field Validation**: Ensure required fields are populated
- **Permission Denied**: Verify user permissions in Drupal
- **Content Type**: Ensure content type exists

### Error Logging
All errors are logged in the Google Sheet with:
- Error message
- Timestamp
- Failed content details

## Advanced Features

### Image Upload Support
```javascript
// Upload image first, then reference in content
"field_featured_image": [{
  "target_id": uploaded_image_id
}]
```

### Taxonomy Integration
```javascript
// Reference taxonomy terms
"field_category": [{
  "target_id": category_term_id
}]
```

### Scheduling
Modify the schedule trigger for different intervals:
- Every 30 minutes
- Daily at specific time
- Custom cron expression

## Monitoring and Maintenance

### Regular Checks
- Monitor Google Sheets for errors
- Check Drupal logs for API issues
- Verify published content quality
- Update field mappings as needed

### Performance Optimization
- Batch process multiple items
- Implement retry logic for failures
- Cache frequently used data
- Monitor API rate limits

## Use Cases

### Editorial Workflows
- Content calendar management
- Multi-author collaboration
- Approval processes
- Scheduled publishing

### Content Migration
- Bulk content import
- Data transformation
- Content updates
- Site migrations

### Marketing Automation
- Campaign content publishing
- Product announcements
- Blog post automation
- Social media integration

This workflow streamlines content publishing by bridging the gap between spreadsheet-based content management and Drupal's robust CMS capabilities. 