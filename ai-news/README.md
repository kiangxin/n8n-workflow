# AI News Aggregator Workflow

An n8n workflow that automatically aggregates AI news from RSS feeds, uses AI to generate summaries, and maintains a curated database in Notion.

## Prerequisites

- n8n installed and running
- Notion account with admin access
- OpenRouter API key (or other AI service)
- RSS feed URLs for AI news sources

## Setup Instructions

### 1. Notion Setup
1. Create a new Notion database for storing news articles
2. Create an integration in Notion settings
3. Get the integration token
4. Share your database with the integration

### 2. AI Service Setup
1. Get your AI service API key (e.g., OpenRouter)
2. Keep the API key handy for n8n configuration

### 3. n8n Workflow Configuration
1. Import `ai-news-workflow.json`
2. Configure the following nodes:
   - RSS Feed nodes with your preferred news sources
   - AI Processing node with your API key
   - Notion node with integration token and database ID

## Workflow Overview

1. Periodically fetches new articles from configured RSS feeds
2. Processes each article through AI for:
   - Content summarization
3. Saves processed information to Notion database with:
   - Article title and source
   - AI-generated summary
   - Original link
   - Publication date