# 🧭 Multi-Agent Travel  Planner
### Built with **LangGraph**, **Python**, **Groq/OpenAI**, and **Gradio**

This project is an end-to-end **multi-agent travel planning system** that automatically generates a personalized travel itinerary based on user inputs such as the destination city and interests (temples, beaches, nature, nightlife, etc.).

It leverages **LangGraph** to orchestrate multiple AI agents working together in a stateful workflow, enabling a deterministic, production-style AI application.

---

## 🚀 Features

- 🧠 **Multi-Agent Architecture (LangGraph)**
- 🎯 **City Extraction Agent**
- 🎨 **Interest Analysis Agent**
- 🗺️ **Itinerary Generation Agent**
- 📝 **Custom Prompts + System Roles**
- 🔄 **Stateful workflow using PlannerState**
- ⚙️ **Graph-based orchestration (nodes + edges)**
- ⚡ **Real-time execution with graph.stream**  
- 🌐 **Interactive UI powered by Gradio**
- 🗂️ **Structured itinerary output (day plan)**

---

## 🧱 Tech Stack

| Component | Tools Used |
|----------|------------|
| Agent Orchestration | **LangGraph** |
| LLMs | **Groq Llama 3.3 Versatile**, **OpenAI GPT** |
| Backend | **Python, LangChain Core** |
| Frontend/UI | **Gradio** |
| Workflow Logic | **StateGraph, Nodes, Edges, PlannerState** |

---

## 🗺️ Architecture (High-Level Workflow)
       
       ┌────────────────┐
       │   User Input   │
       │ (City, Interests)
       └───────┬────────┘
               │
         (LangGraph Start)
               │
    ┌──────────▼──────────┐
    │   City Agent Node   │
    │ Extracts destination │
    └──────────┬──────────┘
               │
    ┌──────────▼──────────┐
    │ Interest Agent Node │
    │  Parses preferences │
    └──────────┬──────────┘
               │
    ┌──────────▼───────────┐
    │ Itinerary Agent Node │
    │  LLM-generated plan  │
    └──────────┬───────────┘
               │
       (Workflow End)
               │
       ┌───────▼──────────┐
       │   Final Output   │
       │  Day-wise plan   │
       └──────────────────┘



---

## 📌 Project Workflow

### **1️⃣ City Agent**
- Reads user-provided city.
- Validates or corrects it (LLM if needed).
- Stores city in shared memory (**PlannerState**).

### **2️⃣ Interest Agent**
- Takes comma-separated list of interests.
- Cleans, normalizes, and categorizes them.
- Stores them in the state graph.

### **3️⃣ Itinerary Agent**
- Reads city + interest list from state.
- Generates a structured itinerary:
  - Places to visit  
  - Time breakdown  
  - Local suggestions  
  - Alternative options  

---

## 🎨 Gradio UI

The app includes a clean and minimal UI:
- City input box  
- Interest list input  
- Submit button  
- Output area (generated itinerary)  
- Custom theme from HuggingFace  

---
<img width="1895" height="594" alt="Screenshot 2025-11-16 195851" src="https://github.com/user-attachments/assets/db1d3fac-b452-46e6-a2d8-fbc909767a23" />

## ▶️ How to Run

```bash
pip install -r requirements.txt
python app.py



📍 Destination: Jaipur  
🎯 Interests: Culture, Food, Forts

🗓️ 1-Day Itinerary:
- 8:00 AM → Hawa Mahal (Photos + Market Walk)
- 10:00 AM → Amber Fort (Sheesh Mahal Tour)
- 1:00 PM → Local Rajasthani Thali (Chokhi Dhani)
- 3:00 PM → City Palace + Museum
- 6:00 PM → Nahargarh Fort Sunset Point
- 8:00 PM → Johari Bazaar shopping
