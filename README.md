# Digital Reset Coach

**Developer:** Hayrettin Kaan Özsoy  
**Hackathon:** Samsung Innovation Campus – Generative AI Hackathon
#
Digital Reset Coach is a **generative AI-powered digital well-being prototype**
developed for the Samsung Innovation Campus Generative AI Hackathon.

The application analyzes a user's self-reported screen-time habits and generates
a personalized, non-judgmental reflection together with practical suggestions
for healthier digital use.

## Features

- Collects self-reported daily screen time and usage habits
- Supports a structured main usage time window
- Identifies possible digital-use triggers without treating them as confirmed facts
- Generates three personalized recommendations
- Creates a small daily challenge
- Avoids medical or psychological diagnosis
- Includes safeguards for sensitive inputs and prompt injection

## Tech Stack

- Python
- Streamlit
- Google Gemini 3.6 Flash API
- `google-genai`
- `python-dotenv`

## Generative AI Approach

The project uses **Gemini 3.6 Flash** as the core generative AI model.

Several prompting approaches were tested during development:

1. **Zero-shot baseline**
   - A simple prompt was used to generate reflections and recommendations.
   - Testing revealed unsupported assumptions and overconfident claims.

2. **Structured zero-shot prompting**
   - Explicit output sections, grounding rules, uncertainty language, and safety
     constraints were added.
   - This version was selected for the final prototype.

3. **Few-shot prompting**
   - Two example responses were provided to test consistency.
   - Although output consistency improved, some recommendations became too similar
     to the examples.

Additional safety refinements were introduced after testing vulnerable-user and
prompt-injection scenarios.

## Ethical Considerations

The application is designed as a digital well-being tool, not a diagnostic system.

The prompt instructs the model to:

- Avoid diagnosing digital addiction or medical/psychological conditions
- Avoid unsupported psychological, medical, neurological, or biological claims
- Use cautious language when interpreting possible triggers
- Avoid judgmental or shaming language
- Avoid guaranteeing behavioral outcomes
- Treat user-provided text as data rather than instructions
- Suggest appropriate human or professional support when significant distress
  is explicitly reported

Users are also advised not to enter unnecessary sensitive personal information.

## Setup

### 1. Clone the repository

```bash
git clone https://github.com/kaanzsoy/digital-reset-coach.git
cd digital-reset-coach
```

### 2. Create a virtual environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure the Gemini API key
Create a `.env` file:
```bash
GEMINI_API_KEY=your_api_key_here
```

### 5. Run the application
```bash
streamlit run app.py
```

## Example Use Case

### Example input:
- Daily screen time: `7 hours`
- Most used platform: `Instagram`
- Main usage window: `22:00-01:00`
- Main trigger: `Boredom and scrolling before sleep`
- Goal: `Reduce daily screen time to 5 hours`

### The application generates:
- A reflection on the reported digital pattern
- A possible trigger
- Three practical recommendations
- A small challenge for the next day
- A short encouraging message

## Disclaimer
**Digital Reset Coach provides general digital well-being guidance and does not provide medical or psychological diagnoses.**