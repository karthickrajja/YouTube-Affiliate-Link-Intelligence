YouTube Affiliate Link Intelligence
Overview

YouTube Affiliate Link Intelligence is a data analysis project that identifies and analyzes Amazon affiliate links embedded in YouTube video descriptions.

The project uses the YouTube Data API v3 to collect video metadata from a YouTube channel and then processes the descriptions to identify Amazon links.

The initial analysis focuses on understanding how frequently a creator uses Amazon links across their video content and what types of Amazon links are being used.

Objective

The goal of this project is to answer questions such as:

How many videos contain Amazon links?
What percentage of a channel's videos contain Amazon links?
What types of Amazon links are used?
How does Amazon-link usage change over time?
Which types of content are more likely to contain Amazon links?
Data Pipeline
YouTube Channel ID
        ↓
YouTube Data API
        ↓
Upload Playlist ID
        ↓
All Video IDs
        ↓
Video Metadata
        ↓
Video Descriptions
        ↓
Amazon URL Extraction
        ↓
Amazon Link Analysis
        ↓
DataFrame
        ↓
Insights & Visualization
API Workflow

The project uses three main YouTube Data API endpoints.

1. channels.list

Used to retrieve the channel's upload playlist ID.

Channel ID → Upload Playlist ID
2. playlistItems.list

Used to retrieve all video IDs from the channel's upload playlist.

Pagination is implemented using nextPageToken to retrieve videos beyond the first 50 results.

Upload Playlist ID → All Video IDs
3. videos.list

Used to retrieve metadata for the collected video IDs.

The current project collects:

Video ID
Published date
Channel ID
Video title
Video description
Channel title
Category ID
Video IDs → Video Metadata
Amazon Link Extraction

Regular expressions are used to identify Amazon URLs within YouTube video descriptions.

Examples of Amazon URLs include:

https://www.amazon.in/dp/XXXXXXXXXX
https://www.amazon.in/gp/product/XXXXXXXXXX
https://www.amazon.in/shop/creator

Amazon URLs are currently classified into different types, such as:

Product URLs
Amazon Storefront URLs
Other Amazon URLs
Important Limitation

Not every Amazon URL contains an ASIN.

For example:

https://www.amazon.in/shop/creator

is an Amazon storefront URL and does not directly identify an individual product.

Therefore, the current version focuses on Amazon-link presence and classification, rather than claiming that every promoted product has been identified.

Technology Stack
Python
Requests — API requests
Pandas — data processing and analysis
Regular Expressions (re) — Amazon URL extraction
YouTube Data API v3 — YouTube data collection
Jupyter Notebook / VS Code — development and analy
