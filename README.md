# ItemRadarAI 🔍

![Google Gemini](https://img.shields.io/badge/google%20gemini-8E75B2?style=for-the-badge&logo=google%20gemini&logoColor=white)
<a href="https://developers.google.com/adk" target="_blank" style="text-decoration: none;">
  <span style="
    display: inline-flex;
    align-items: center;
    background-color:rgb(0, 0, 0);
    color: white;
    font-family: 'Segoe UI', sans-serif;
    font-weight: bold;
    font-size: 12px;
    padding: 4px 10px;
  ">
    <img src="assets/google-adk-logo.png" alt="Google ADK" style="height:20px; margin-right:8px;">
    Google ADK
  </span>
</a>
![Google Cloud](https://img.shields.io/badge/GoogleCloud-%234285F4.svg?style=for-the-badge&logo=google-cloud&logoColor=white)
![Firebase](https://img.shields.io/badge/firebase-a08021?style=for-the-badge&logo=firebase&logoColor=ffcd34)
<a href="https://https://firebase.studio/" target="_blank" style="text-decoration: none;">
  <span style="
    display: inline-flex;
    align-items: center;
    background-color:rgb(216, 109, 37);
    color: white;
    font-family: 'Segoe UI', sans-serif;
    font-weight: bold;
    font-size: 12px;
    padding: 4px 10px;
  ">
    <img src="assets/Firebase_Studio_icon.svg" alt="Firebase Studio" style="height:20px; margin-right:8px;">
    Firebase Studio
  </span>
</a>
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![TypeScript](https://img.shields.io/badge/typescript-%23007ACC.svg?style=for-the-badge&logo=typescript&logoColor=white)
![React](https://img.shields.io/badge/react-%2320232a.svg?style=for-the-badge&logo=react&logoColor=%2361DAFB)

## Publications

### Medium post
[![Read on Medium](https://img.shields.io/badge/Read_on-Medium-black?logo=medium&logoColor=white&style=for-the-badge)](https://medium.com/@igelcru/lost-something-let-our-ai-agents-find-it-a512f8d610de)

### Youtube Video

[![Watch on YouTube](https://img.shields.io/badge/YouTube-▶️-FF0000?style=flat-square&logo=youtube&logoColor=white)](https://www.youtube.com/watch?v=i0bIskqgsB8)


**Connecting People with Lost Belongings**

A citizen network that reunites people with their lost belongings in minutes using AI-powered multi-agent technology.

## Overview

ItemRadarAI is an innovative platform designed to connect residents of any city with individuals who find lost items, streamlining the recovery process and providing valuable insights into loss patterns across urban environments.

### Key Features

- **For Lost Item Owners**: Conversational chatbot accessible via WhatsApp, web, or mobile app that matches descriptions or photos with found items in seconds
- **For Item Finders**: Simple photo capture with GPS location upload to instantly add items to the database

## How It Works

ItemRadarAI operates through a sophisticated multi-agent AI system:

### 1. **Lens Agent** (For Finders)
- Captures photo, geolocation, and timestamp
- Extracts detailed descriptions using Gemini Vision
- Generates embeddings and stores in Firestore with Vertex AI Vector Search

### 2. **Chatbot Agent** (For Owners)
- Engages in natural dialogue to understand the lost item
- Generates accurate descriptions and corresponding embeddings
- Publishes description-ready events to the system

### 3. **ItemMatcher Agent**
- Queries Vertex AI Vector Search to retrieve top matching candidates
- Returns ranked results based on similarity scores

### 4. **Reducer Agent**
- Handles multiple matches by generating discriminative questions
- Examples: "Does it have handles?", "What color is the strap?"

### 5. **Filter**
- Applies user responses to refine candidate lists
- Iterates until reaching either one match or no matches

### 6. **Results**
- **Single Match**: Notifies both users with pickup instructions
- **No Match**: Informs user and offers optional future notifications

## Technology Stack

### Core Infrastructure
- **ADK (Python)**: Primary development framework
- **Firestore**: Data storage

### AI & Machine Learning
- **Gemini Embeddings & Vision**: Item description and image processing
- **Vertex AI Vector Search**: Fast, accurate matching (< 500ms)
- **Gemini**: Powers conversational chatbot

### User Interface & Analytics
- **Firebase UI**: Found item intake interface

## Getting Started

### Prerequisites
- Google Cloud Platform account with enabled APIs
- Python 3.8+ environment
- ADK framework installation

### Quick Start

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ItemRadar
   ```

2. **Install requirements**
   ```bash
   pip install -r requirements.txt
   ```
   
3. **Google application Credentials**

- Windows 

   ```powershell
   $env:GOOGLE_APPLICATION_CREDENTIALS="route to your service-account.json"
   ```

-  Linux

   ```bash
   export GOOGLE_APPLICATION_CREDENTIALS"route to your service-account.json"
   ```


4. **Set up environment variables**
   ```bash
   cp env.template .env
   # Edit .env with your actual API keys and configuration
   ```
   
4. **Run the program**
   ```bash
   cd multiagent
   adk web
   ```

### Configuration

1. Set up Firestore database
2. Configure Vertex AI Vector Search index
3. Enable required Google Cloud APIs
4. Set environment variables for API keys and endpoints

## API Integration

The system now includes a FastAPI server that connects the frontend with the multiagent system:

- **Lost Item Reports**: Connect to `chatbot_manager` agent for search workflow
- **Found Item Reports**: Connect to `lens_agent` for geocoding and registration
- **Search Status**: Track ongoing lost item searches

See [API_INTEGRATION.md](API_INTEGRATION.md) for detailed documentation.

## Testing

Run the API integration tests:

```bash
cd api
python test.py
```

### Key Files
- `api/main.py`: FastAPI server with endpoints
- `frontend/src/app/actions.ts`: Frontend API calls
- `multiAgent/chatbot_manager/agent.py`: Lost item processing
- `multiAgent/lens_agent/agent.py`: Found item processing

## License

This project is licensed under the MIT License - see the LICENSE file for details.

