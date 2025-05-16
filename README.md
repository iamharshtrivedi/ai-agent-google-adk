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

3.  **Explore the Agent:**
   ```bash
    cd multi_tool_agents
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

