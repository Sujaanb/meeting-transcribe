# meeting-transcribe

Project Repository for the meeting transcribe agent - An intelligent platform for transcribing and summarizing meeting content using multiple LLM providers.

## Features

- 🎤 Meeting transcription and content summarization
- 🤖 Support for multiple LLM providers (OpenAI, Mistral AI, Google Gemini, Ollama)
- 🚀 FastAPI-based REST API with automatic documentation
- 📝 Flexible prompt system for content generation
- 🔄 LangChain integration for advanced LLM operations
- 🛡️ CORS enabled for frontend integration

## Prerequisites

- Python 3.8 or higher
- pip package manager
- API keys for your chosen LLM provider (OpenAI, Mistral, or Google)

## Installation

### 1. Clone the repository
```bash
git clone https://github.com/Sujaanb/meeting-transcribe.git
cd meeting-transcribe
```

### 2. Create and activate a virtual environment
```bash
# Using venv
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### 3. Set up environment variables
```bash
# Copy the example environment file
cp .env.example .env

# Edit .env with your API keys and configuration
# nano .env  # or use your preferred editor
```

**Required environment variables:**
- `llm_provider`: Choose from `openai`, `mistral`, or `gemini`
- Corresponding API key for your chosen provider

### 4. Install dependencies
```bash
pip install -r requirements.txt
```

## Running the Application

### Development Mode
```bash
python app.py
```

The API will be available at `http://localhost:8001`
- API Documentation: `http://localhost:8001/docs`
- OpenAPI Schema: `http://localhost:8001/openapi.json`

### Using Uvicorn Directly
```bash
uvicorn app:app --reload --host 0.0.0.0 --port 8001
```

## API Endpoints

### Generate Content Summary
- **POST** `/transcribe/content/v1/generate`
- **Request Body:**
  ```json
  {
    "question": "Your meeting transcript or content here"
  }
  ```
- **Response:**
  ```json
  {
    "status": "success",
    "message": "Content generated successfully",
    "data": "Generated summary here"
  }
  ```

## Configuration

### LLM Providers

#### OpenAI
```
llm_provider=openai
openai_api_key=sk-...
```

#### Mistral AI
```
llm_provider=mistral
mistral_api_key=...
```

#### Google Gemini
```
llm_provider=gemini
gemini_api_key=...
```

#### Local Ollama
```
llm_provider=ollama
local_model_url=http://localhost:11434
```

## Project Structure

```
meeting-transcribe/
├── app.py                 # Main FastAPI application
├── api_services.py        # API route handlers
├── base_requests.py       # Pydantic request/response models
├── config.py              # Configuration settings
├── test_run.py            # Core logic for content generation
├── requirements.txt       # Python dependencies
├── .env.example          # Environment variables template
├── util/
│   ├── llm_factory.py    # LLM provider factory pattern
│   ├── system_prompt.py  # System prompts for LLM
│   ├── utility.py        # Utility functions
│   └── constants.py      # Constants and configurations
└── README.md             # This file
```

## Development

### Code Style
The project uses `black` for code formatting and `ruff` for linting.

```bash
# Format code
black .

# Lint code
ruff check .
```

## Troubleshooting

### Missing API Key Error
Ensure your `.env` file is correctly configured with the appropriate API key for your chosen LLM provider.

### CORS Issues
Update the `BACKEND_CORS_ORIGINS` in `.env` to include your frontend URLs.

### Port Already in Use
Change the `API_PORT` in `.env` or specify a different port when running:
```bash
python app.py --port 8002
```

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For issues and questions, please open an issue on the GitHub repository.
