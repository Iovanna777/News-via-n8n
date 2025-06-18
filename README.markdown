# 🎥 Video Content Automation Workflow with n8n

![n8n Workflow](https://img.shields.io/badge/n8n-Automation-blue) ![License](https://img.shields.io/badge/license-MIT-green) ![Status](https://img.shields.io/badge/status-awesome-orange)

Welcome to my content factory! This n8n workflow grabs trending news, turns them into slick videos with AI avatars and subtitles, and posts them to TikTok and YouTube after a quick human nod in Telegram. Built and tested by me, it’s a real-world project that saves time and makes content creation as easy as scrolling your feed. 😎

## 📖 What Does It Do?

This workflow automates the entire pipeline of creating and publishing video content based on trending news. Here’s the flow:

1. **Fetches News**: Pulls hot posts from Hacker News (e.g., "AI Breakthrough in Robotics").
2. **Generates Text**: Uses OpenAI (ChatGPT) to craft catchy titles, short descriptions (TikTok-friendly), and detailed descriptions (YouTube-ready).
3. **Creates Videos**: Sends text to Heygen for videos with a digital avatar that’s cooler than most influencers.
4. **Adds Subtitles**: Pipes the video to Vizard for stylish, auto-generated subtitles.
5. **Moderates Content**: Sends a preview to a Telegram bot for a quick "Yay or Nay" check.
6. **Publishes**: Uploads approved videos to TikTok (short and snappy) and YouTube (longer and informative).
7. **Logs Everything**: Saves all data (news, texts, video links) to Google Sheets for tracking.

**Result**: 5–7 videos per week with minimal effort, ready to go viral while you sip coffee. ☕

### Example Output
- **News**: "AI Breakthrough in Robotics"
- **Title**: "Robots Are Thinking Now! 🤖 #AI"
- **Short Description**: "New AI tech makes robots smarter than ever!"
- **Video**: [Demo Video (Placeholder)](https://example.com/demo-video.mp4)
- **Logged in Google Sheets**: News URL, title, description, video link, timestamp.

## 🛠️ Connected Services

This workflow is like a digital orchestra, with n8n as the conductor. Here’s what’s plugged in:

- **Hacker News API**: Grabs trending tech news (filtered for 100+ upvotes).
- **OpenAI API (ChatGPT)**: Generates titles (e.g., max 60 chars for TikTok), short descriptions (150 chars), and long descriptions (500 words).
- **Heygen API**: Creates videos with customizable AI avatars (voice, style, background). Outputs MP4 in 1080p, 16:9 (YouTube) or 9:16 (TikTok).
- **Vizard API**: Adds auto-generated subtitles with customizable fonts/colors. Multi-language support optional.
- **Telegram Bot API**: Sends previews (video + text) with buttons like "Publish" or "Tweak".
- **YouTube API**: Uploads videos with titles, descriptions, and tags.
- **TikTok API**: Posts short videos with hashtags for max reach.
- **Google Sheets API**: Logs data for monitoring and debugging.
- **n8n**: The glue that orchestrates everything, handling retries and scheduling.

## 🎯 Why Does It Exist?

Manually creating video content is like solving a puzzle with missing pieces—slow, pricey, and frustrating. This workflow:
- **Saves Time**: Cuts 10–15 hours of weekly work to ~10 minutes of moderation.
- **Scales Content**: Pumps out daily videos without a team of editors.
- **Keeps It Fresh**: Turns news into content in 1–2 hours.
- **Boosts Engagement**: Optimized for TikTok (viral) and YouTube (informative).
- **Saves Money**: Replaces editors ($1,000–$2,000/month) and SMM teams ($1,000–$2,000/month) with a one-time setup.

Perfect for startups, content creators, or HR agencies looking to automate video content (e.g., job ads or company culture videos).

## 🗂️ Repository Structure

```
├── workflows/
│   └── video-automation-workflow.json  # Main n8n workflow configuration
├── scripts/
│   └── preprocess-text.js             # Example script for cleaning OpenAI output
├── docs/
│   └── setup-guide.md                 # Detailed setup instructions
├── .gitignore                         # Ignores sensitive files (e.g., .env)
├── README.md                          # You're reading it!
└── LICENSE                            # MIT License
```

## 🚀 Getting Started

### Prerequisites
- **n8n**: Self-hosted or cloud instance (v0.200.0+ recommended).
- **API Keys** for:
  - Hacker News (public API, no key needed)
  - OpenAI
  - Heygen
  - Vizard
  - Telegram Bot (create via @BotFather)
  - YouTube (Google Cloud Console)
  - TikTok (Developer Portal)
  - Google Sheets (Google Cloud Console)
- **Environment**: Node.js (for scripts), basic JavaScript knowledge.
- **Coffee**: Because automation is cool, but caffeine is cooler.

### Installation
1. **Clone the repo**:
   ```bash
   git clone https://github.com/your-username/video-content-automation.git
   cd video-content-automation
   ```
2. **Set up n8n**:
   - Import `workflows/video-automation-workflow.json` into your n8n instance.
   - Configure credentials for each service in n8n (see `docs/setup-guide.md`).
3. **Add environment variables**:
   Create a `.env` file in your n8n instance:
   ```env
   HACKER_NEWS_API_URL=https://hacker-news.firebaseio.com/v0
   OPENAI_API_KEY=your-openai-key
   HEYGEN_API_KEY=your-heygen-key
   VIZARD_API_KEY=your-vizard-key
   TELEGRAM_BOT_TOKEN=your-telegram-token
   YOUTUBE_API_KEY=your-youtube-key
   TIKTOK_API_KEY=your-tiktok-key
   GOOGLE_SHEETS_CREDENTIALS=your-google-credentials
   ```
4. **Run the workflow**:
   - Activate the workflow in n8n.
   - Schedule it (e.g., daily at 8 AM) or trigger manually.
5. **Test it**:
   - Check Telegram for previews.
   - Verify videos on TikTok/YouTube and logs in Google Sheets.

### Quick Demo
![n8n Workflow Demo](https://example.com/demo.gif)  
*See the workflow in action: news fetched, video generated, and published in ~1 hour!*

## ❓ FAQ

- **What if Heygen API is slow?**  
  Increase the retry timeout in n8n or check your Heygen plan for rate limits.
- **Can I use another news source?**  
  Yes! Swap Hacker News for Reddit, RSS, or Twitter by updating the API node.
- **Why use Telegram for moderation?**  
  It’s fast, mobile-friendly, and lets you approve content on the go.
- **How do I debug errors?**  
  Check Google Sheets logs or n8n’s execution history for details.
- **Can this work for HR marketing?**  
  Absolutely! Adapt it for job ads, company culture videos, or candidate engagement content.

## 🛠️ Customization

- **Change News Source**: Swap Hacker News for Reddit or RSS feeds.
- **Tweak AI Prompts**: Adjust OpenAI prompts for different tones (funny, professional).
- **Add Localization**: Enable Vizard’s multi-language subtitles or OpenAI translations.
- **Enhance Moderation**: Add Telegram buttons (e.g., "Edit title") or integrate with Slack.
- **Analytics**: Pull YouTube/TikTok metrics into Google Sheets for A/B testing.

## ⚠️ Known Limitations
- **API Rate Limits**: Heygen and Vizard may throttle heavy usage (check pricing).
- **Content Quality**: AI-generated text/videos may need occasional tweaks.
- **TikTok API**: Posting requires manual OAuth setup (TikTok’s API is quirky).
- **Error Handling**: Basic retries included; complex edge cases may need custom nodes.

## 🤝 Contributing
Found a bug or have a killer idea? Open an issue or submit a PR! Let’s make this workflow legendary. 🙌

## 📜 License
MIT License. Use it, tweak it, love it—just don’t blame me if your videos go *too* viral. 😜

## 🙋‍♀️ Author
Built with 💖 by [Your Name]. Fresh off a real-world n8n project, I’m ready to automate the world! Ping me on [Your GitHub/Twitter/Telegram] for collabs or coffee chats.