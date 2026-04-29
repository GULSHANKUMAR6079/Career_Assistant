# 🚀 GenAI Career Assistant Agent

**Your Ultimate Guide to a Career in Generative AI!**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/19lYWHVgRSSyY84HW3WkwJ9OFAA25T8KW?usp=sharing)

---

## 📋 Overview

Meet the **GenAI Career Assistant** — an AI-powered mentor designed to simplify and support your journey in Generative AI learning, resume preparation, interview assistance, and job hunting.

Built with a multi-agent architecture using **LangChain**, **LangGraph**, **Google Gemini LLM**, and **DuckDuckGoSearchResults**, this assistant provides a comprehensive, personalized experience for aspiring GenAI professionals.

---

## 💡 Motivation

As GenAI rapidly evolves, more people are eager to learn it for career advancement or transition. However, navigating the vast resources on the internet and platforms like YouTube can be overwhelming — long videos, scattered content, and outdated materials make it hard to know where to begin.

Even using ChatGPT for coding help often yields deprecated code, as GenAI packages and methods (LangChain, LlamaIndex, Hugging Face) are updated frequently. This assistant solves that problem by providing **up-to-date, personalized guidance** powered by real-time web search.

![Workflow Graph](https://drive.google.com/uc?export=view&id=1kw2oOWtV4rynXjHjiZbrUdTJgJbQzm-Y)

---

## ✨ Key Features

### 1. 📚 Learning & Content Creation
- Offers tailored learning pathways in GenAI, covering key topics and skills
- Assists users in creating tutorials, blogs, and posts based on their interests or queries

### 2. ❓ Q&A Support
- Provides on-demand Q&A sessions for users needing guidance on concepts or coding issues

### 3. 📝 Resume Building & Review
- One-on-one resume consultations and guidance
- Crafts personalized, market-relevant resumes optimized for current job trends

### 4. 🎤 Interview Preparation
- Hosts Q&A sessions on common and technical interview questions
- Simulates real interview scenarios and conducts mock interviews with evaluation feedback

### 5. 🔍 Job Search Assistance
- Guides users through the job search process, offering tailored insights and support
- Finds real job listings using web search

---

## 🛠️ Tech Stack

All tools used are **free and open source**:

| Technology | Purpose |
|---|---|
| **LangChain** | Framework for building LLM-powered applications |
| **LangGraph** | State graph workflow management |
| **Google Gemini LLM** | AI model for text generation |
| **DuckDuckGoSearchResults** | Real-time web search for up-to-date information |
| **Python** | Core programming language |
| **python-dotenv** | Environment variable management |

---

## 🏗️ Architecture

### Workflow Graph

The agent uses a **LangGraph StateGraph** with conditional routing to direct queries to the appropriate handler:

```
START → categorize
         ├── handle_learning_resource
         │     ├── tutorial_agent → END
         │     └── ask_query_bot → END
         ├── handle_resume_making → END
         ├── handle_interview_preparation
         │     ├── interview_topics_questions → END
         │     └── mock_interview → END
         └── job_search → END
```

### Key Components

1. **State Management**: Using `TypedDict` to define and manage the state of each interaction
2. **Query Categorization**: Classifying user queries into Learning, Resume Preparation, Interview, or Job Search
3. **Sub-Categorization**: Learning → (Tutorial, Q&A) | Interview → (Interview Prep, Mock Interview)
4. **Response Generation**: Creating appropriate responses based on the query category, generating `.md` files for tutorials, resumes, mock interviews, etc.
5. **Workflow Graph**: Utilizing LangGraph to create a flexible and extensible workflow

### Method Details

1. **Initialization**: Set up the environment and import necessary libraries
2. **State Definition**: Create a structure to hold query information, category, sub-category, and response
3. **Node Functions**: Implement separate functions for categorization and response generation
4. **Graph Construction**: Use StateGraph to define the workflow, adding nodes and edges
5. **Conditional Routing**: Implement logic to route queries based on their category and sub-category
6. **Workflow Compilation**: Compile the graph into an executable application
7. **Execution**: Process user queries through the workflow and retrieve results

---

## 📁 Project Structure

```
genai-career-assistant/
├── main.py                          # Main entry point
├── requirements.txt                 # Python dependencies
├── .env.example                     # Environment variable template
├── README.md                        # This file
├── agent_hackathon_genAI_career_assistant.ipynb  # Original notebook
├── src/
│   ├── __init__.py                  # Package init
│   ├── state.py                     # State TypedDict definition
│   ├── utils.py                     # Utility functions (trim, save, display)
│   ├── nodes.py                     # Node functions & routing logic
│   ├── workflow.py                  # LangGraph workflow construction
│   └── agents/
│       ├── __init__.py              # Agents package init
│       ├── learning_agent.py        # Learning Resource Agent (Tutorial & Q&A)
│       ├── interview_agent.py       # Interview Agent (Questions & Mock)
│       ├── resume_agent.py          # Resume Maker Agent
│       └── job_search_agent.py      # Job Search Agent
└── Agent_output/                    # Generated output files (auto-created)
```

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- A Google API Key ([Get one here](https://aistudio.google.com/app/apikey))

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd genai-career-assistant
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Set up environment variables:**
   ```bash
   cp .env.example .env
   ```
   Then edit `.env` and add your Google API key:
   ```
   GOOGLE_API_KEY=your_actual_api_key_here
   ```

4. **Run the assistant:**
   ```bash
   python main.py
   ```

### Using the Notebook

You can also run the original Jupyter notebook:
```bash
jupyter notebook agent_hackathon_genAI_career_assistant.ipynb
```

Or open it directly in [Google Colab](https://colab.research.google.com/drive/19lYWHVgRSSyY84HW3WkwJ9OFAA25T8KW?usp=sharing).

---

## 📖 Usage Examples

### Test Case 1: Creating Tutorials
```python
query = "I want to learn Langchain and langgraph. With usage and concept. Also give coding example implementation for both. Create tutorial for this."
result = run_user_query(app, query)
```

### Test Case 2: Q&A Session for Doubts
```python
query = "I am confused between Langgraph and CrewAI when to use what for Agent Creation?"
result = run_user_query(app, query)
```

### Test Case 3: Interview Question Discussion
```python
query = "I want to discussion Interview question for Gen AI job roles."
result = run_user_query(app, query)
```

### Test Case 4: Mock Interview with Evaluation
```python
query = "I need mock interview to practice."
result = run_user_query(app, query)
```

### Test Case 5: Resume Modification
```python
query = "Can you help me to modify my resume based on job description"
result = run_user_query(app, query)
```

### Test Case 6: Resume Making
```python
query = "I want to make resume for Gen AI roles job."
result = run_user_query(app, query)
```

### Test Case 7: Job Search
```python
query = "I want to search jobs."
result = run_user_query(app, query)
# Follow-up: "Find jobs in GenAI, AI Engineer roles, Location USA"
```

---

## 🔧 Configuration

### Environment Variables

| Variable | Required | Description |
|---|---|---|
| `GOOGLE_API_KEY` | ✅ Yes | Your Google Generative AI API key |

### Models Used

| Model | Used For |
|---|---|
| `gemini-1.5-flash` | Query categorization, interview handling |
| `gemini-1.5-pro` | Tutorial generation, resume creation, job search |

---

## 📝 Output Files

All generated content is saved as timestamped Markdown files in the `Agent_output/` directory:

| File Pattern | Description |
|---|---|
| `Tutorial_YYYYMMDDHHMMSS.md` | Generated tutorial blogs |
| `Q&A_Doubt_Session_YYYYMMDDHHMMSS.md` | Q&A session transcripts |
| `Interview_questions_YYYYMMDDHHMMSS.md` | Curated interview questions |
| `Mock_Interview_YYYYMMDDHHMMSS.md` | Mock interview transcripts with evaluation |
| `Resume_YYYYMMDDHHMMSS.md` | Generated resumes |
| `Job_search_YYYYMMDDHHMMSS.md` | Job search results |

---

## 🔮 Future Enhancements

- **Knowledge Base**: Incorporate a resource-rich library with curated links to courses, tutorials, and articles for comprehensive learning support
- **Multi-Domain Customization**: Expand beyond Generative AI, allowing users to tailor the assistant to any career path, creating a versatile "Dream Job Assistant"
- **Advanced Job Search Tools**: Include an automated job application tracker, enhanced networking features, and guidance on global job opportunities and visas

---

## 🎯 Conclusion

The GenAI Career Assistant is more than just a tool; it's a comprehensive, personalized mentor designed to help you thrive in the rapidly evolving field of Generative AI. From mastering key concepts and building a strong resume to preparing for interviews and navigating the job market, this assistant equips you with everything you need to achieve your career goals.

With the GenAI Career Assistant by your side, your path to a successful Generative AI career becomes clearer, more manageable, and achievable. **Embrace the future of AI with confidence and step into your dream role!**

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
