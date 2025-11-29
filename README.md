# Agno Five: The 5 Levels of AI Agents

![Agno Five Banner](https://placehold.co/1200x300?text=Agno+Five)

An interactive educational project demonstrating the 5 levels of AI agent architecture based on [Ashpreet Bedi](https://twitter.com/ashpreetbedi)'s framework. This project provides working demos for each level of agent complexity using the [Agno](https://agno.com) framework.

**The 5 Levels of AI Agents**

Lets explore the 5 levels of AI Agents, from simple to complex. Always start with level 1 and add complexity as needed.

**Level 1**: Agent with tools and instructions. When people say agents are just LLM + tool calls in a loop, this is what they mean (this also tells you their level of understanding).

Instructions "teach" the Agent how to achieve its task and tools let Agents interact with external environments to push or pull data.

**Level 2**: Agent with knowledge and storage. Rarely does a model have all the information it needs to achieve its task and we obviously can't jam everything in the context, so we give the Agent knowledge that it searches at runtime (i.e Agentic RAG or Dynamic few-shot). 

Knowledge search needs to be hybrid (full-text and semantic). Hybrid search + reranking is the best out-of-the-box Agentic Search strategy you can use.

Storage saves the Agent's state in a database. LLM calls are "stateless" and storage makes Agents "stateful" by storing messages in a database and adding them to the current call as needed. 

**Level 3**: Agent with memory and reasoning. Memory let's an Agent remember details about a user and personalize its responses across sessions. This is a fairly new concept that everyone is still exploring. The part of memory im the most excited about is "self-learning", more on this soon. 

Reasoning is a key feature that every agent builder should know when and how to use. It not only improves cognitive reasoning (understanding of data and instructions) but also improves the success rate of each step.

**Level 4**: Multi Agent Teams. Agents work best when they have a narrow scope (i.e. specialized to a domain) and a reasonably small set of tools (<10 ish). By putting agents together in a team, we can increase the overall capabilities and solve broader, more complex problems. 

Remember to add reasoning, otherwise the Team leader struggles to work on complex tasks. My current (2025) belief is that autonomous multi-agent teams don't work. They work <1/2 the time and thats no good. 

Agno comes with an industry leading multi-agent architecture that supports 3 modes of execution: coordinate, route and collaborate with the ability to automatically manage agentic memory and context.

**Level 5**: Agentic Systems. APIs (i.e. servers) that take in a request, asynchronously complete the task and stream back the result. These are hard, very hard - when the request comes in we need to save the state in a database, trigger an async job and stream the results back as they're ready. Websockets can work here, but they are not an each tech to work with. 

Agentic systems is where the $ is and what everyone is trying to build. We've put out the Agent API, Agent UI and detailed documentation on how to build them. I hope to write more on this to help AI engineers build better systems.

## 📚 Overview

This project demonstrates the progressive complexity of AI agents, from simple instruction-following tools to complete agentic systems. As Ashpreet Bedi notes: **"Always start with level 1 and add complexity as needed."**

Each level builds upon the previous one:

1. **Level 1:** Agent with tools and instructions
2. **Level 2:** Agent with knowledge and storage
3. **Level 3:** Agent with memory and reasoning
4. **Level 4:** Multi-agent teams
5. **Level 5:** Agentic systems

## 🛠️ Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/jmedia65/agno-five.git
   cd agno-five
   ```

2. Create a virtual environment:

   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Create a `.env` file with your API keys:
   ```
   OPENAI_API_KEY=your_key_here
   ```

## 📋 Usage

Run the Streamlit app:

```bash
streamlit run app.py
```

Navigate through the different levels using the sidebar. Each level includes:

- An explanation of the concept
- A live chat demo showing the agent in action
- Code examples that you can expand to see how it's implemented

## 🧩 Project Structure

```
agno-five/
├── app.py            # Main Streamlit application
├── views/            # Individual level views
│   ├── intro.py      # Introduction and overview
│   ├── agno1.py      # Level 1: Agent with tools and instructions
│   ├── agno1b.py     # Level 1B: Enhanced agent with additional tools
│   ├── agno2.py      # Level 2: Agent with knowledge and storage
│   ├── agno3.py      # Level 3: Agent with memory and reasoning
│   ├── agno4.py      # Level 4: Multi-agent teams
│   └── agno5.py      # Level 5: Agentic systems
└── tmp/              # Storage for databases (not tracked in git)
```

## 💻 Development

- This project uses Streamlit for the UI
- The agents are built using the Agno framework
- Local file-based databases (SQLite and LanceDB) are used for storage and vector search

## 🌐 Deployment

This project can be deployed using Docker and Render:

### Local Docker Deployment

1. Build and run the Docker container locally:

   ```bash
   # Build and start the container
   docker-compose up --build
   ```

2. Access the application at http://localhost:8501

### Render Deployment with Persistent Storage

1. Create a Render account and connect your GitHub repository

2. Create a new Web Service:

   - Select "Docker" as the environment
   - Name your service (e.g., "agno-five")
   - Keep all other default Docker settings

3. Add environment variables:

   - Add `OPENAI_API_KEY` with your API key value

4. Create a disk for persistent storage:

   - In the "Disks" section, create a new disk
   - Set mount path to `/app/tmp`
   - Choose an appropriate size (start with 1GB)
   - This ensures your database files persist between deployments

5. Deploy your service:
   - Render will build and deploy your Docker container
   - Once complete, you'll get a URL to access your application

Note: For production deployment, consider:

- Creating API keys with usage limits
- Monitoring your disk usage as the vector database grows
- Adding proper error handling for API limits

## 🙏 Acknowledgments

- [Ashpreet Bedi](https://twitter.com/ashpreetbedi), CEO of Agno, for the "5 Levels of AI Agents" concept
- [Agno](https://agno.com) for their powerful agent framework
- All contributors to the open-source libraries used in this project

## 📄 License

MIT License

Copyright (c) 2025 [Max Braglia]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

Built with ❤️ by [Max Braglia](https://hiremax.now/)
