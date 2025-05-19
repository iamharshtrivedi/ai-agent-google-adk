# Agent Development Kit (ADK) Sample

<img src="https://github.com/google/adk-docs/blob/main/docs/assets/agent-development-kit.png" alt="Agent Development Kit Logo" width="150">

Welcome to the Sample Agent repository! This collection provides a ready-to-use agent built on top of the [Agent Development Kit](https://github.com/google/adk-python), designed to accelerate your development process.  This agent covers a range of common use cases and complexities, from simple conversational bots to complex multi-agent workflows.

## ✨ What are Sample Agent?

A Sample Agent is a functional starting point for a foundational agent designed for common application scenarios. It comes pre-packaged with core logic (like different agent using different tools, evaluation, human in the loop) relevant to a specific use case or industry. While functional, a Sample Agent typically requires customization (e.g., adjusting specific responses or integrating with external systems) to be fully operational. Each agent includes instructions on how it can be customized.

## 🚀 Getting Started

Follow these steps to set up and run the sample agent:

1.  **Prerequisites:**
    *   **Install the ADK Samples:** Ensure you have the Agent Development Kit installed and configured. Follow the [ADK Installation Guide](https://google.github.io/adk-docs/get-started/installation/).
    *   **Set Up Environment Variables:** Each agent example relies on a `.env` file for configuration (like API keys, Google Cloud project IDs, and location). This keeps secrets out of the code.
        *   You will need to create a `.env` file in each agent's directory you wish to run (usually by copying the provided `.env.example`).
        *   Setting up these variables, especially obtaining Google Cloud credentials, requires careful steps. Refer to the **Environment Setup** section in the [ADK Installation Guide](https://google.github.io/adk-docs/get-started/installation/) for detailed instructions.
    *   **Google Cloud Project (Recommended):** While some agents might run locally with just an API key, most leverage Google Cloud services like Vertex AI and BigQuery. A configured Google Cloud project is highly recommended. See the [ADK Quickstart](https://google.github.io/adk-docs/get-started/quickstart/) for setup details.


2.  **Clone this repository:**
You can install the ADK samples via cloning it from the public repository by
    ```bash
    git clone https://github.com/iamharshtrivedi/ai-agent-google-adk.git
    ```
 
```bash
**Create multi_tool_agent/__init__.py **
```
```bash
from . import agent
```
**Create multi_tool_agent/agent.py**
```bash
import datetime
from zoneinfo import ZoneInfo
from google.adk.agents import Agent

def get_weather(city: str) -> dict:
    """Retrieves the current weather report for a specified city.

    Args:
        city (str): The name of the city for which to retrieve the weather report.

    Returns:
        dict: status and result or error msg.
    """
    if city.lower() == "new york":
        return {
            "status": "success",
            "report": (
                "The weather in New York is sunny with a temperature of 25 degrees"
                " Celsius (77 degrees Fahrenheit)."
            ),
        }
    else:
        return {
            "status": "error",
            "error_message": f"Weather information for '{city}' is not available.",
        }


def get_current_time(city: str) -> dict:
    """Returns the current time in a specified city.

    Args:
        city (str): The name of the city for which to retrieve the current time.

    Returns:
        dict: status and result or error msg.
    """

    if city.lower() == "new york":
        tz_identifier = "America/New_York"
    else:
        return {
            "status": "error",
            "error_message": (
                f"Sorry, I don't have timezone information for {city}."
            ),
        }

    tz = ZoneInfo(tz_identifier)
    now = datetime.datetime.now(tz)
    report = (
        f'The current time in {city} is {now.strftime("%Y-%m-%d %H:%M:%S %Z%z")}'
    )
    return {"status": "success", "report": report}


root_agent = Agent(
    name="weather_time_agent",
    model="gemini-2.0-flash",
    description=(
        "Agent to answer questions about the time and weather in a city."
    ),
    instruction=(
        "You are a helpful agent who can answer user questions about the time and weather in a city."
    ),
    tools=[get_weather, get_current_time],
)
```
3.  **Explore the Agent:**
   ```bash
    cd multi_tool_agents/agent.py
   ```
*   Navigate to the `multi_tool_agents/` directory.
*   The `multi_tool_agents/README.md` provides an overview and categorization of the available agent.
*   Browse the subdirectories. Each contains a specific sample agent with its own `README.md`.

4.  **Run an Agent:**
    *   Navigate into that agent's parent directory (e.g., `cd ai-agent-google-adk/`).
    *   Run `adk web` and run the agent.

**Notes:**
* These agent have been built and tested using [Google models](https://cloud.google.com/vertex-ai/generative-ai/docs/learn/models) on Vertex AI. You can test these samples with other models as well. Please refer to [ADK Tutorials](https://google.github.io/adk-docs/agents/models/) to use other models for these samples. 

## 🧱 Repository Structure
```bash
.parent_folder/
    multi_tool_agent/
        __init__.py
        agent.py
        .env
```

## ℹ️ Getting help

If you have any questions or if you found any problems with this repository, please report through [GitHub issues]( https://github.com/iamharshtrivedi/AIAgent/issues).

