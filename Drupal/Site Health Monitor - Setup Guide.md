# 🔍 Site Health Monitor - Uptime and Performance

## Overview
This workflow continuously monitors your Drupal sites for uptime, performance, and health status. It checks multiple sites every 5 minutes and sends alerts when issues are detected.

## Features
- **Multi-Site Monitoring**: Monitor multiple Drupal sites simultaneously
- **Performance Tracking**: Measure response times and site speed
- **Health Status Checks**: Verify Drupal-specific functionality
- **Real-time Alerts**: Instant notifications via Slack and email
- **Historical Logging**: Track performance trends in Google Sheets
- **Customizable Thresholds**: Set different limits for each site

## Monitoring Capabilities

### Uptime Monitoring
- HTTP status code verification
- Response time measurement
- Connection timeout detection
- SSL certificate validation

### Drupal-Specific Checks
- Admin panel accessibility
- Database connectivity
- Module status verification
- Cache performance

### Performance Metrics
- Page load times
- Server response times
- Resource loading speeds
- Performance thresholds

## Setup Instructions

### 1. Site Configuration
Update the "Configure Sites" node with your sites:

```javascript
[
  {
    "name": "Production Site",
    "url": "https://your-drupal-site.com",
    "expected_status": 200,
    "max_response_time": 3000
  },
  {
    "name": "Staging Site", 
    "url": "https://staging.your-drupal-site.com",
    "expected_status": 200,
    "max_response_time": 5000
  }
]
```

### 2. Google Sheets Setup

#### Site_Health_Log Sheet Structure
| Column | Type | Description |
|--------|------|-------------|
| timestamp | DateTime | Check timestamp |
| site_name | Text | Site identifier |
| site_url | URL | Site URL |
| status_code | Number | HTTP status code |
| response_time | Number | Response time in ms |
| is_up | Boolean | Site availability |
| is_healthy | Boolean | Overall health status |
| drupal_status | Text | Drupal-specific status |

### 3. Alert Configuration

#### Slack Notifications
- Configure Slack channel for alerts
- Customize alert message format
- Set up different channels for different severity levels

#### Email Alerts
- Configure SMTP settings
- Set recipient email addresses
- Customize email templates

### 4. Required Credentials
- **Google Sheets OAuth2 API**
- **Drupal Basic Auth** (for admin checks)
- **Slack API** (for notifications)
- **SMTP** (for email alerts)

## Monitoring Schedule

### Default Schedule
- **Frequency**: Every 5 minutes
- **Timeout**: 10 seconds per check
- **Batch Processing**: One site at a time

### Custom Schedules
Modify the Schedule Trigger for different intervals:
- **High Frequency**: Every 1-2 minutes for critical sites
- **Standard**: Every 5-10 minutes for regular monitoring
- **Low Frequency**: Every 15-30 minutes for less critical sites

## Health Criteria

### Site is Healthy When:
- HTTP status code is 200-299
- Response time is under threshold
- Drupal admin panel is accessible
- No critical errors detected

### Alert Triggers
- **Site Down**: Non-200 status codes
- **Slow Performance**: Response time exceeds threshold
- **Drupal Issues**: Admin panel inaccessible
- **Timeout**: No response within timeout period

## Advanced Monitoring

### Security Checks
```javascript
// Add security header checks
"security_headers": {
  "x_frame_options": $json.headers['x-frame-options'],
  "x_content_type_options": $json.headers['x-content-type-options'],
  "strict_transport_security": $json.headers['strict-transport-security']
}
```

### Database Monitoring
```javascript
// Check database status via Drupal API
"database_status": {
  "connection": "healthy",
  "query_time": response_time_ms,
  "active_connections": connection_count
}
```

### Module Status Checks
```javascript
// Monitor critical Drupal modules
"module_status": {
  "core_modules": "enabled",
  "security_updates": "current",
  "custom_modules": "functional"
}
```

## Alert Escalation

### Severity Levels
1. **Info**: Performance slightly degraded
2. **Warning**: Performance significantly impacted
3. **Error**: Site partially unavailable
4. **Critical**: Site completely down

### Escalation Rules
- **1 failure**: Log only
- **2 consecutive failures**: Slack notification
- **3 consecutive failures**: Email alert
- **5 consecutive failures**: Phone/SMS alert (custom)

## Performance Analytics

### Trend Analysis
- Average response times over time
- Uptime percentage calculations
- Performance degradation patterns
- Peak usage impact analysis

### Reporting
- Daily performance summaries
- Weekly uptime reports
- Monthly trend analysis
- Comparative site performance

## Troubleshooting

### Common Issues
- **False Positives**: Adjust timeout values
- **Network Issues**: Check n8n server connectivity
- **Authentication**: Verify Drupal credentials
- **Rate Limiting**: Adjust monitoring frequency

### Debugging
- Enable detailed logging in n8n
- Check Drupal error logs
- Monitor network latency
- Verify SSL certificates

## Custom Extensions

### Additional Checks
- Content freshness verification
- Search functionality testing
- Form submission testing
- API endpoint monitoring

### Integration Options
- **PagerDuty**: For incident management
- **DataDog**: For advanced metrics
- **New Relic**: For application monitoring
- **Pingdom**: For additional uptime checks

## Use Cases

### Production Monitoring
- Critical business sites
- E-commerce platforms
- High-traffic applications
- Customer-facing portals

### Development Monitoring
- Staging environments
- Development sites
- Testing platforms
- CI/CD pipelines

### Multi-Client Management
- Agency client sites
- Managed hosting services
- Enterprise site portfolios
- Distributed applications

This monitoring workflow ensures your Drupal sites maintain optimal performance and availability while providing immediate alerts when issues arise. 