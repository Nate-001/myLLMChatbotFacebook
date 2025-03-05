# myLLMChatbotFacebook

This project is a chatbot application that uses a **BlenderBot model** (from Facebook's `blenderbot-400M-distill`) to simulate conversations. The chatbot is built using **Flask** for the backend and **JavaScript/HTML/CSS** for the frontend, allowing users to interact with the AI model in a conversational interface. The application is containerized using Docker for easy deployment.

---

## Features

1. **Interactive Chat Interface**:
   - Users can input messages and receive responses from the AI chatbot.
   - Includes loading animations for better user experience.

2. **AI-Powered Conversations**:
   - Uses Facebook's `blenderbot-400M-distill` model from Hugging Face Transformers for generating responses.

3. **Conversation History**:
   - Maintains a conversation history to provide context to the model for better responses.

4. **Flask Backend**:
   - Handles requests and integrates with the AI model to process user input and return responses.

5. **Dockerized Deployment**:
   - Includes a Dockerfile for easy setup and deployment in containerized environments.

---

## Prerequisites

Before running this project, ensure you have the following installed:

- Python 3.8 or higher
- Node.js (for frontend dependency management, if needed)
- Docker (optional, for containerized deployment)

---

## Installation and Setup

### 1. Clone the Repository
```bash
git clone https://github.com/Nate-001/myLLMChatbotFacebook.git
cd myLLMChatbotFacebook
```

### 2. Install Python Dependencies
Create a virtual environment (optional but recommended) and install the required Python libraries:
```bash
python3 -m venv venv
source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
pip install -r requirements.txt
```

### 3. Install Frontend Dependencies (Optional)
If you need to modify or rebuild the frontend, ensure Node.js is installed and run:
```bash
npm install
```

### 4. Run Locally
Start the Flask server:
```bash
python app.py
```
The application will be available at `http://127.0.0.1:5000`.

---

## Using Docker

### Build Docker Image
To containerize the application, build the Docker image:
```bash
docker build -t llm-chatbot .
```

### Run Docker Container
Run the containerized application:
```bash
docker run -p 5000:5000 llm-chatbot
```
The application will be accessible at `http://localhost:5000`.

---

## Project Structure

```
LLM_application_chatbot/
├── static/                     # Static assets (images, CSS, etc.)
│   ├── user.jpeg               # User profile image for chat messages
│   ├── Bot_logo.png            # Bot profile image for chat messages
│   └── Error.png               # Error icon image
├── templates/
│   └── index.html              # Frontend HTML file for the chatbot interface
├── app.py                      # Flask backend application
├── Dockerfile                  # Dockerfile for containerization
├── requirements.txt            # Python dependencies list
└── README.md                   # Documentation (this file)
```

---

## How It Works

1. **Frontend**:
   - The user interacts with an HTML form (`index.html`) to send messages.
   - JavaScript (`addMessage` and `sendMessage` functions) handles message display, loading animations, and API calls to the backend.

2. **Backend**:
   - Flask serves as the backend framework.
   - The `/chatbot` endpoint receives POST requests containing user input.
   - The BlenderBot model processes the input (along with conversation history) and generates a response.
   - The response is sent back to the frontend and displayed in the chat window.

3. **Model**:
   - The `facebook/blenderbot-400M-distill` model is loaded using Hugging Face Transformers.
   - Conversation history is maintained in memory to provide context for responses.

---

## Limitations

1. **Conversation History Growth**:
   - As conversation history grows, it may exceed the token limit of the BlenderBot model, causing crashes or degraded performance.
   - A solution would involve truncating older parts of the conversation or limiting history length.

2. **Error Handling**:
   - Error handling is basic; improvements could include more detailed error messages or recovery mechanisms.

3. **Scalability**:
   - This implementation is suitable for small-scale use but may require optimization for production environments.

---

## Future Improvements

1. Implement token truncation logic to handle long conversation histories.
2. Add authentication or user management features.
3. Enhance UI/UX with more styling and interactive components.
4. Deploy on cloud platforms like AWS or Azure for scalability.
5. Add support for multiple languages or additional AI models.

---

## License

This project is licensed under [MIT License](LICENSE).

---

## Acknowledgments

- [Hugging Face Transformers](https://huggingface.co/docs/transformers/index) for providing pre-trained models.
- [Flask](https://flask.palletsprojects.com/) for its lightweight web framework.
- [Docker](https://www.docker.com/) for containerization support.

Enjoy building your chatbot! 🚀
