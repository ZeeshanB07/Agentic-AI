# TripMate AI — Multi-Agent Travel Planner

An AI-powered travel planning application built with **LangGraph, LangChain, and FastAPI** that transforms natural-language travel requests into structured, personalized travel plans. TripMate AI coordinates specialized AI agents to research flights, explore hotel options, and generate day-by-day itineraries through a unified workflow.

## Overview

Planning a trip often involves switching between multiple platforms to research flights, compare accommodations, manage budgets, and organize activities. TripMate AI simplifies this process by bringing these tasks together into an intelligent, multi-agent application.

Powered by LangGraph orchestration and large language models, the application coordinates specialized agents to transform a user's travel preferences into a practical itinerary.

## Key Features

- **Flight Research:** Retrieve flight-related information using the AviationStack API.
- **Hotel Research:** Discover accommodation options using Tavily-powered web search.
- **Multi-Agent Orchestration:** Coordinate specialized agents through a LangGraph workflow.
- **Intelligent Itinerary Planning:** Generate structured, day-by-day travel plans based on user requirements.
- **LLM-Powered Responses:** Use Groq-hosted language models to interpret requests and generate travel recommendations.
- **Conversational State Persistence:** Store conversation state using PostgreSQL.
- **FastAPI Backend:** Expose travel-planning functionality through REST API endpoints.
- **Web-Based Interface:** Interact with the application through a frontend built with HTML, CSS, JavaScript, and Jinja2 templates.

## Architecture and Workflow

TripMate AI follows a multi-agent architecture in which individual agents handle specialized responsibilities.

1. **User Request:** The user submits a natural-language travel request, including the destination, duration, preferences, and budget.
2. **Flight Research Agent:** Gathers flight-related information using AviationStack.
3. **Hotel Research Agent:** Searches for accommodation recommendations using Tavily.
4. **Itinerary Planning Agent:** Organizes the available information into a practical, day-by-day travel plan.
5. **Response Agent:** Consolidates the workflow output into a structured response for the user.
6. **State Persistence:** PostgreSQL supports conversation-state persistence across interactions.

The workflow is orchestrated using LangGraph, enabling coordinated execution across the specialized agents.

## Technology Stack

| Category | Technologies |
|---|---|
| Programming Language | Python 3.10+ |
| Backend Framework | FastAPI |
| Agent Orchestration | LangGraph |
| LLM Integration | LangChain, Groq |
| Flight Research | AviationStack API |
| Web Search | Tavily API |
| Database | PostgreSQL |
| Frontend | HTML, CSS, JavaScript |
| Templating | Jinja2 |

## Project Structure

```text
TripMate-AI/
├── app.py                # FastAPI application entry point
├── backend.py            # LangGraph workflow and agent orchestration
├── requirements.txt      # Python dependencies
├── static/               # CSS, JavaScript, and static assets
├── templates/            # Jinja2 HTML templates
└── tools/                # Flight and web-search integrations
```

## Prerequisites

Before running TripMate AI locally, ensure that you have:

- Python 3.10 or later
- PostgreSQL installed and running
- A Groq API key
- A Tavily API key
- An AviationStack API key
- Git installed on your system

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/ZeeshanB07/Agentic-AI.git
cd Agentic-AI
```

Navigate into the directory containing `app.py` and `requirements.txt` if the project is nested inside the repository.

### 2. Create a Virtual Environment

**Windows — PowerShell**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

**Linux / macOS**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root and configure the required credentials and database connection.

```env
DATABASE_URL=postgresql://user:password@localhost:5432/travel_db
GROQ_API_KEY=your_groq_api_key
AVIATIONSTACK_API_KEY=your_aviationstack_api_key
TAVILY_API_KEY=your_tavily_api_key
DEFAULT_ORIGIN_IATA=DAC
```

Replace the placeholder values with your actual credentials and database details. Ensure that the PostgreSQL database exists and is accessible.

**Security note:** Never commit your `.env` file, API keys, or database credentials to GitHub. Add `.env` to your `.gitignore` file.

### 5. Run the Application

Start the FastAPI application:

```bash
python app.py
```

Once the server is running, open the application in your browser:

```text
http://127.0.0.1:8000/
```

If your application uses a different host or port configuration, use the address specified in your application settings.

## API Reference

### Health Check

**Endpoint:** `GET /health`

Use this endpoint to check the application's health status.

### Generate a Travel Plan

**Endpoint:** `POST /api/travel`

Submit a travel request as a JSON payload.

**Example request:**

```bash
curl -X POST http://127.0.0.1:8000/api/travel \
  -H "Content-Type: application/json" \
  -d '{"message":"Plan a 3-day trip to Tokyo with a budget of $1200"}'
```

The application processes the request through its travel-planning workflow and returns a response based on the implemented API behavior.

## Example Use Case

A user submits the following request:

> Plan a 3-day trip to Tokyo with a budget of $1,200.

TripMate AI coordinates its agents to research flight options, explore accommodation recommendations, and organize a day-by-day itinerary. The final response brings the resulting information together to help the user plan the trip.

*Actual recommendations depend on API availability, search results, model responses, and the application's implementation.*

## Configuration and Security

- Store API keys and credentials in environment variables.
- Keep `.env`, virtual environments, and other sensitive files out of version control.
- Configure PostgreSQL connectivity before starting the application.
- Handle API errors, rate limits, and unavailable external services appropriately.
- Validate user inputs and protect API endpoints according to your deployment requirements.

## Future Enhancements

Potential areas for extending TripMate AI include:

- Real-time flight availability and price comparison.
- Hotel pricing and availability integration.
- Budget-aware itinerary optimization.
- User preferences and personalized recommendations.
- Additional travel agents for attractions, restaurants, and local transportation.
- Streaming responses and interactive itinerary refinement.
- Deployment with containerization and cloud infrastructure.
- Automated testing, monitoring, and evaluation of agent outputs.

These are potential enhancements and should not be interpreted as features already implemented.

## Contributing

Contributions, suggestions, and improvements are welcome.

1. Fork the repository.
2. Create a feature branch.
3. Implement your changes and add relevant tests.
4. Commit your changes with a descriptive message.
5. Open a pull request describing your contribution.

## Acknowledgments

TripMate AI is built using the open-source Python ecosystem and modern AI tooling, including LangGraph, LangChain, FastAPI, and Groq, alongside external travel-data and web-search services.

## License

If you intend to distribute this project as open source, add a `LICENSE` file specifying the license you choose. Until a license is included, the repository should not be assumed to grant standard open-source reuse permissions.

---

**TripMate AI** — Bringing multi-agent AI orchestration into practical travel planning.
