# 🤖 AI Content Repurposing Engine

## 📌 Project Overview

The **AI Content Repurposing Engine** is an AI-powered Natural Language Processing (NLP) application that automatically transforms YouTube video content into platform-specific social media posts.

The system accepts a YouTube video URL, extracts relevant video metadata, analyzes the content, generates an AI-powered summary, identifies important keywords, and creates customized social media posts for **LinkedIn, Facebook, and Twitter**.

The project demonstrates the integration of **Natural Language Processing, Transformer-based language models, YouTube metadata extraction, keyword extraction, content classification, prompt-based text generation, and an interactive Gradio interface** into a complete end-to-end AI application.

---

## 🎯 Project Objectives

The main objectives of this project are to:

- Automatically analyze YouTube video information.
- Extract useful metadata from YouTube videos.
- Classify videos into predefined content categories.
- Generate concise AI-powered summaries.
- Extract relevant keywords from video content.
- Automatically generate hashtags.
- Create platform-specific social media posts.
- Adapt generated content according to the selected writing tone.
- Provide an interactive and user-friendly web interface.
- Demonstrate an end-to-end practical application of NLP and Generative AI.

---

## ✨ Key Features

### 🎬 YouTube Video Analysis

The application accepts different YouTube URL formats and normalizes them into a standard format.

Supported formats include:

- `youtube.com/watch`
- `youtu.be`
- YouTube embedded links

Using **yt-dlp**, the system extracts:

- Video title
- Video description
- Channel name
- Video duration
- View count
- Like count
- Video thumbnail

---

### 🧠 AI-Powered Content Classification

The system analyzes the video title and description and categorizes the content into predefined categories.

The supported categories are:

- 📚 Educational
- 🎓 Tutorial
- 🎙️ Podcast
- 🎬 Entertainment
- 📰 News
- 🎮 Gaming
- 🎥 Vlog
- ⭐ Review
- 👨‍🍳 Cooking
- 🎯 General Content

The classification is performed using keyword-based content analysis.

---

### 🤖 AI-Powered Summarization

The project uses Google's **Flan-T5-Base** transformer model to generate concise summaries from the available video information.

The generation pipeline uses:

- Model: `google/flan-t5-base`
- Maximum generation length: 200 tokens
- Temperature: 0.7
- Repetition penalty: 2.5
- Sampling: Enabled

The system attempts to generate a concise **three-sentence summary** containing the main topic and a key takeaway.

A fallback summary mechanism is also implemented if AI generation fails.

---

## 🏷️ Keyword Extraction

The system automatically identifies important keywords from the video title, generated summary, and description.

The keyword extraction process includes:

1. Text normalization
2. Removal of non-alphanumeric characters
3. Lowercase conversion
4. Stopword removal using NLTK
5. Word-frequency analysis
6. Selection of the most frequent relevant terms
7. Conversion of selected keywords into hashtag-friendly terms

The system generates up to **8 relevant keywords**.

---

# 📱 Platform-Specific Content Generation

One of the main features of the project is the generation of different posts for different social media platforms.

## 💼 LinkedIn

The LinkedIn post is designed around a:

- Professional tone
- Informative structure
- Industry-oriented presentation
- Professional hashtags
- Engagement-oriented question

---

## 📘 Facebook

The Facebook post focuses on:

- Friendly communication
- Community engagement
- Conversational presentation
- Sharing-oriented language
- Community hashtags

---

## 🐦 Twitter

The Twitter post is designed for:

- Concise communication
- Short-form content
- Quick information delivery
- Hashtag integration
- Link placement

The implementation limits the displayed video title and summary components to maintain a concise format.

---

# 🗣️ Tone Customization

Users can select the desired content-generation tone from the Gradio interface.

Available tones are:

- **Professional**
- **Friendly**
- **Casual**
- **Academic**

The selected tone is incorporated into the AI summarization prompt.

---

# 🏗️ System Architecture

The overall processing pipeline is:

```text
                 YouTube URL
                      │
                      ▼
              URL Validation
                      │
                      ▼
            Metadata Extraction
                  (yt-dlp)
                      │
                      ▼
             Content Analysis
                      │
          ┌───────────┴───────────┐
          ▼                       ▼
   Content Classification    AI Summarization
                                  │
                                  ▼
                         Keyword Extraction
                                  │
                                  ▼
                    Platform-Specific Generation
                  ┌─────────┬──────────┬─────────┐
                  ▼         ▼          ▼
              LinkedIn   Facebook   Twitter
                  │         │          │
                  └─────────┼──────────┘
                            ▼
                     Gradio Interface
