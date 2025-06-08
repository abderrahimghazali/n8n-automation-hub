# YouTube Automation Workflows

This folder contains powerful n8n automation workflows for YouTube content creation, management, and optimization.

## 🎬 Complete YouTube Automation - Video Ideas to Upload with AI

The ultimate end-to-end YouTube automation workflow that:

- **📋 Pulls video ideas** from Google Sheets with titles, topics, and target audience
- **🤖 Generates 10-scene scripts** using GPT-4o with engaging voiceovers and visual prompts
- **🎨 Creates cinematic visuals** automatically via JSON2Video with transitions and effects
- **🗣️ Converts scripts to natural voice** using ElevenLabs (no microphone needed)
- **🎞️ Renders complete videos** with subtitles and professional quality
- **📺 Uploads to YouTube** automatically with optimized titles and descriptions
- **📊 Tracks status in Google Sheets** for complete workflow visibility
- **🔄 Handles errors and retries** automatically for reliability

**Triggers:** Manual or scheduled (Mon/Wed/Fri at 9 AM)

## 📊 YouTube Analytics Dashboard & Content Strategy

Weekly analytics automation that provides insights and content recommendations:

- **📈 Fetches YouTube Analytics** data (views, likes, subscribers, watch time)
- **🧠 AI-powered performance analysis** with actionable insights
- **💡 Generates content ideas** based on performance data and trends
- **📋 Updates Google Sheets** with weekly performance reports
- **📊 Creates Notion dashboard** with visual analytics
- **📱 Sends Slack reports** with key metrics and recommendations

**Triggers:** Weekly (Mondays at 8 AM)

## 🎥 YouTube Shorts from Long-Form Videos

Automatically creates engaging YouTube Shorts from existing videos:

- **🎬 Analyzes video transcripts** to identify highlight moments
- **✂️ Extracts 60-second segments** with highest engagement potential
- **📱 Reformats for vertical display** (1080x1920 resolution)
- **📝 Adds auto-generated captions** with professional styling
- **🎯 Creates click-worthy titles** and descriptions
- **🏷️ Suggests relevant hashtags** for maximum reach
- **📊 Tracks generated Shorts** in dedicated Google Sheet

**Triggers:** Webhook when new video is uploaded

## 🎤 Podcast to YouTube Video Converter

Transforms podcast episodes into engaging YouTube videos:

- **📡 Monitors RSS feeds** for new podcast episodes
- **🎵 Downloads and transcribes** audio using Whisper AI
- **📚 Creates video chapters** with timestamps and descriptions
- **🎨 Generates chapter visuals** and thumbnails using AI
- **🎬 Produces full video** with podcast audio and visual elements
- **📺 Uploads with chapters** and optimized YouTube descriptions
- **📊 Tracks conversions** in Google Sheets

**Triggers:** RSS feed monitoring for new episodes

## Setup Requirements

### Environment Variables
```
GOOGLE_SHEET_ID=your_video_ideas_sheet_id
ANALYTICS_SHEET_ID=your_analytics_tracking_sheet
SHORTS_TRACKING_SHEET_ID=your_shorts_tracking_sheet
PODCAST_TRACKING_SHEET_ID=your_podcast_tracking_sheet
YOUTUBE_API_KEY=your_youtube_api_key
YOUTUBE_CHANNEL_ID=your_channel_id
ELEVENLABS_VOICE_ID=your_preferred_voice_id
NOTION_TOKEN=your_notion_integration_token
NOTION_DATABASE_ID=your_notion_database_id
PODCAST_RSS_FEED=your_podcast_rss_url
```

### Required Integrations
- Google Sheets API
- YouTube Data API v3
- OpenAI API (GPT-4o, Whisper, DALL-E)
- ElevenLabs API
- JSON2Video API
- Rev.ai (for captions)
- Slack (for notifications)
- Notion API (optional, for dashboards)

### Google Sheets Structure

**Video Ideas Sheet:**
| Video Title | Target Audience | Tone | Status | YouTube Link | Row Number |

**Analytics Sheet:**
| Date | Total Views | Total Likes | New Subscribers | Watch Time | Avg View Duration | AI Insights |

**Shorts Tracking Sheet:**
| Date Created | Original Video | Short Title | YouTube Short ID | YouTube Short URL | Priority | Hashtags | Status |

**Podcast Tracking Sheet:**
| Date Converted | Original Podcast Title | YouTube Title | YouTube Video ID | YouTube URL | Original Podcast URL | Chapter Count | Duration | Status |

## Features

✅ **Fully Automated** - Set and forget workflows  
✅ **AI-Powered** - GPT-4o for scripts, ElevenLabs for voice, AI for visuals  
✅ **Error Handling** - Automatic retries and error notifications  
✅ **Status Tracking** - Complete visibility in Google Sheets  
✅ **Scalable** - Handle multiple videos and channels  
✅ **Professional Quality** - Cinema-grade video production  
✅ **Multi-Format** - Long-form, Shorts, and podcast conversions  
✅ **Analytics-Driven** - Data-informed content strategy  

## Usage Tips

1. **Start with the Analytics workflow** to understand your current performance
2. **Use the Complete Automation** for regular content creation
3. **Enable Shorts generation** to maximize content from existing videos
4. **Set up podcast conversion** if you have audio content
5. **Monitor Google Sheets** for workflow status and performance data
6. **Customize AI prompts** based on your brand voice and style

These workflows will transform your YouTube content creation process, saving hours of manual work while maintaining professional quality and consistency. 


---

## YouTube Google Sheets Automation - Full Video Creation and Publishing

Complete automation for YouTube video creation and publishing using Google Sheets as the central management system.

**Files:**
- [Setup Guide](YouTube%20Google%20Sheets%20Automation%20-%20Setup%20Guide.md) - Complete setup instructions and configuration
- [Workflow](YouTube%20Google%20Sheets%20Automation%20-%20Workflow.txt) - n8n workflow JSON for import

**Features:**
- Automated video script generation using GPT-4
- Background music integration from Google Sheets library
- Professional video creation via JSON2Video API
- Direct YouTube publishing with metadata
- Error handling and status tracking

This workflow transforms your video ideas into published YouTube content with minimal manual intervention.

 