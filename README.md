# HighlighAI - An AI Agentic System for Video Summarizing🎥🚀

A **Streamlit-based application** for analyzing video content and extracting actionable insights using advanced AI models. Powered by **Gemini 2.0 Flash Exp**, this tool enables users to upload video files and receive detailed, user-friendly analysis.

---

## Features

- **AI-Powered Video Analysis**: Leverages Gemini 2.0 Flash Exp for multimodal AI processing.
- **Supplementary Web Research**: Uses DuckDuckGo for additional context and insights.
- **Streamlined User Interface**: Upload video files, ask questions, and get actionable results effortlessly.
- **Supports Popular Formats**: Works with `.mp4`, `.mov`, and `.avi` video files.

---

## Tech Stack

- **Python**: Core programming language.
- **Streamlit**: Interactive UI and deployment.
- **Phidata Library**: For building and managing AI agents.
- **Google Generative AI**: Video file processing and Gemini model integration.
- **DuckDuckGo**: Supplementary web research tool.

---


## Prerequisites

- **Python**: Version 3.8 or higher.
- **Google API Key**: Add your Google API key to a `.env` file in the project directory:
  GOOGLE_API_KEY=your_api_key_here

---

## Installation

1. **Clone the Repository**:  
   git clone https://github.com/your-username/video-ai-summarizer.git  
   cd video-ai-summarizer  

2. **Install Dependencies**:  
   Run the following command to install required Python packages:  
   pip install streamlit phi duckduckgo-python python-dotenv google-generative-ai

---

## Running the App

1. Start the Streamlit app:  
   streamlit run app.py  

2. Access the app in your web browser at:  
   http://localhost:8501

---

## How to Use

1. **Upload a Video**: Upload a file in `.mp4`, `.mov`, or `.avi` format.
2. **Ask a Question**: Provide specific queries about the video content.
3. **Analyze**: Click the "Analyze Video" button to start processing.
4. **View Results**: Detailed insights will be displayed in the app.

---

## Code Highlights

### Agent Initialization:
```python
def initialize_agent():
    return Agent(
        name="Video AI Summarizer",
        model=Gemini(id="gemini-2.0-flash-exp"),
        tools=[DuckDuckGo()],
        markdown=True,
    )
```

### Uploading and processing the video file

```python
processed_video = upload_file(video_path)
while processed_video.state.name == "PROCESSING":
    time.sleep(1)
    processed_video = get_file(processed_video.name)
```

### Generating the prompt and AI analysis

```python
analysis_prompt = (
    f"""
    Analyze the uploaded video for content and context.
    Respond to the following query using video insights and supplementary web research:
    {user_query}

    Provide a detailed, user-friendly, and actionable response.
    """
)

response = multimodal_Agent.run(analysis_prompt, videos=[processed_video])

```

