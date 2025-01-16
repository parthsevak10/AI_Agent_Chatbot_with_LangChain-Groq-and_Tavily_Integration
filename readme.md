Brief Explanation of the Code
1. app.py (FastAPI Backend)
Imports: The code imports necessary libraries such as FastAPI for web app development, Pydantic for structured data validation, and LangGraph, LangChain for working with AI models and agents.
Environment Variables: The code sets API keys for external tools (e.g., Tavily API and Groq API) using environment variables.
Model Names: A predefined list of model names (llama3-70b-8192 and mixtral-8x7b-32768) is created, indicating which models can be used in the chatbot system.
TavilySearchResults Tool: A search tool (TavilySearchResults) is initialized to retrieve relevant search results during the agent's interaction.
FastAPI App: The FastAPI application is set up with a single POST endpoint (/chat), which:
Accepts a request containing the model_name, system_prompt, and messages to interact with the AI model.
Checks if the model_name is valid and then creates a chatbot agent using the selected model and tools.
Sends the message to the agent, which processes it and returns the response.
The response is returned to the client (UI).
Main Function: If the script is executed directly, the FastAPI app runs locally on port 8000 using Uvicorn.
2. ui.py (Streamlit Frontend)
Streamlit Configuration: The code sets up the Streamlit app with a custom page title and a centered layout.
API URL: The Streamlit app is configured to communicate with the FastAPI backend at http://127.0.0.1:8000/chat.
UI Elements:
System Prompt Input: A text area for the user to define the behavior of the AI agent.
Model Selection: A dropdown list for the user to select between two predefined models (llama3-70b-8192 and mixtral-8x7b-32768).
User Message Input: A text area where the user can input their query or message to the chatbot.
Submit Button: A button that, when clicked, sends the user input along with the selected model and system prompt to the FastAPI backend.
Request to FastAPI: Upon clicking the "Submit" button, the user input, system prompt, and selected model are packaged into a JSON payload and sent to the FastAPI endpoint via a POST request.
Response Handling:
The response from FastAPI (AI's response) is displayed on the frontend.
If the API returns an error, it will be shown to the user.
If the response contains the AI's output, it will be shown in the interface.
In Summary:
The FastAPI backend (app.py) serves as the core logic for interacting with an AI model via LangGraph and Groq API. It processes user input, interacts with the agent, and returns responses.
The Streamlit frontend (ui.py) allows users to interact with the backend via a simple web interface, where they can provide a system prompt, select a model, and send messages to the chatbot. The responses are displayed in the UI.