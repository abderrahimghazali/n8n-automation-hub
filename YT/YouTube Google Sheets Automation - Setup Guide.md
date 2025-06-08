# YouTube Google Sheets Automation - Full Video Creation and Publishing

## Overview
This comprehensive n8n workflow automates the entire YouTube video creation and publishing process using Google Sheets as the central management system. It handles everything from topic processing to final video upload.

## Workflow Components

### INPUT: Video Topic and Prompts
- **Schedule Trigger**: Runs every 2 hours to check for new video topics
- **Google Sheets**: Reads video topics, styles, and audience data from your spreadsheet
- **Prompts**: Processes and structures the input data for AI processing
- **OpenAI Chat Model**: Generates video scripts, titles, descriptions, and tags using GPT-4
- **Structured Output Parser**: Ensures consistent output format with proper schema

### Get Music and Intro Video
- **Get Music**: Retrieves background music from your Music Library sheet
- Randomly selects appropriate music based on video style and mood

### Generate Full Video
- **Create Video**: Uses JSON2Video API to generate the complete video
- **Wait**: Allows processing time for video generation
- Combines script, visuals, and background music into final video

### Handle Errors
- **Switch**: Monitors video generation status (Done/Error/Running)
- **Wait1**: Provides additional processing time for error handling
- **Error Log**: Records any errors to Google Sheets for tracking and debugging

### OUTPUT: Final Video and Publishing
- **Add Video URL**: Updates spreadsheet with generated video URL
- **Get Video File**: Downloads the completed video file
- **YouTube**: Uploads video to YouTube with generated metadata
- **Mark as Done**: Updates spreadsheet with YouTube URL and published status

## Required Google Sheets Structure

### Video_Queue Sheet
| Column | Type | Description |
|--------|------|-------------|
| topic | Text | Video topic/subject |
| style | Text | Video style (educational, entertaining, etc) |
| audience | Text | Target audience description |
| status | Text | Current status (Pending/Processing/Published/Error) |
| video_url | URL | Generated video URL |
| youtube_url | URL | YouTube video ID |
| error_message | Text | Error details if applicable |
| created_at | Date | Entry creation timestamp |
| updated_at | Date | Last update timestamp |
| published_at | Date | YouTube publish timestamp |

### Music_Library Sheet
| Column | Type | Description |
|--------|------|-------------|
| name | Text | Music track name |
| url | URL | Direct download URL |
| genre | Text | Music genre |
| mood | Text | Track mood (upbeat, calm, dramatic) |
| duration | Number | Track length in seconds |

## Setup Instructions

### 1. Prerequisites
- n8n instance (cloud or self-hosted)
- Google Sheets with proper structure
- OpenAI API key
- JSON2Video account and API key
- YouTube API credentials

### 2. Required Credentials
- **Google Sheets OAuth2 API**: For spreadsheet access
- **OpenAI API**: For script generation
- **JSON2Video API**: For video creation
- **YouTube OAuth2 API**: For video uploading

### 3. Configuration Steps

1. **Create Google Sheets**:
   - Set up Video_Queue sheet with required columns
   - Create Music_Library sheet with your music tracks
   - Note your Google Sheet ID from the URL

2. **Configure Credentials**:
   - Add all required API credentials in n8n
   - Test each connection to ensure proper access

3. **Update Node Parameters**:
   - Replace `YOUR_GOOGLE_SHEET_ID` with your actual sheet ID
   - Update credential references in all nodes
   - Customize the OpenAI prompt for your specific needs

4. **Test the Workflow**:
   - Add a test entry to your Video_Queue sheet
   - Trigger the workflow manually
   - Monitor each step for proper execution

## Customization Options

### Video Script Generation
Modify the OpenAI prompt to:
- Change video structure and format
- Adjust tone and style
- Add specific requirements or constraints
- Include brand-specific messaging

### Error Handling
- Customize error notification methods
- Add retry logic for failed operations
- Implement different error handling strategies

### Music Selection
- Add logic for mood-based music selection
- Implement duration matching
- Create genre-specific playlists

## Monitoring and Maintenance

### Regular Checks
- Monitor error logs in Google Sheets
- Review video generation success rates
- Check API usage and limits
- Update music library regularly

### Troubleshooting
- Verify all API credentials are valid
- Check Google Sheets permissions
- Monitor n8n execution logs
- Validate JSON2Video template settings

## Benefits
- **Fully Automated**: Complete hands-off video creation
- **Scalable**: Handle multiple video topics simultaneously
- **Trackable**: Full audit trail in Google Sheets
- **Flexible**: Easy customization for different content types
- **Reliable**: Built-in error handling and retry logic

## Use Cases
- Educational content creation
- Marketing video automation
- Social media content generation
- Product demonstration videos
- Regular content series automation

This workflow transforms your video ideas into published YouTube content with minimal manual intervention, making it perfect for content creators, marketers, and businesses looking to scale their video production. 