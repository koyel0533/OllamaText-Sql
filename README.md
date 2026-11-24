<div align="center">

# 📊 Talk to Your Database (Local Text-to-SQL App)
### *Privacy-First Natural Language-to-SQL Assistant powered by LangChain, Ollama (Llama 3) & Streamlit*

![Python](https://shields.io)
![LangChain](https://shields.io)
![Ollama](https://shields.io)
![Streamlit](https://shields.io)
![SQLite](https://shields.io)

<p>
  A 100% local, zero-API-cost <b>Text-to-SQL web application</b> that translates plain English questions into executable SQL queries using <b>Llama 3</b> via <b>Ollama</b> and <b>LangChain Expression Language (LCEL)</b>.
</p>

</div>

---

## ✨ Key Features

* **100% Local & Private:** Runs completely offline using **Ollama (`llama3`)**—no API keys, cloud costs, or data privacy risks.
* **Schema-Aware SQL Generation:** Dynamically inspects `student_grades.db` (`db.get_table_info()`) and enforces strict prompt rules so Llama 3 outputs pure, executable SQL without conversational filler.
* **Transparent SQL Preview:** Displays the exact generated SQL query in a syntax-highlighted code block (`st.code`) right above the query results.
* **Deterministic Output:** Configured with `temperature=0` to ensure consistent and accurate query synthesis.

---

## 🛠️ Tech Stack

| Layer | Technology | Role |
| :--- | :--- | :--- |
| **Frontend UI** | **Streamlit** | Clean user input interface, SQL syntax viewer (`st.code`), and result display. |
| **AI Orchestration** | **LangChain Core & Community** | LCEL runnable pipeline (`ChatPromptTemplate`, `StrOutputParser`) and `SQLDatabase` wrapper. |
| **Local LLM Engine** | **Ollama (`llama3`)** | Runs Meta's Llama 3 model locally with `temperature=0` for accurate SQL generation. |
| **Database** | **SQLite3** | Relational database (`student_grades.db`) storing student grade records. |
| **Data Handling** | **Pandas** | Tabular data formatting (`pd.DataFrame`) for query results. |

---

## 📂 Project Structure

```text
local-text-to-sql-ollama/
│
├── app.py                  # Main Streamlit application & LangChain LCEL pipeline
├── student_grades.db       # SQLite database containing student grades
├── requirements.txt        # Python dependencies
└── README.md               # Project documentation
```

---

## ⚙️ Prerequisites & Setup

### 1. Install Ollama & Pull Llama 3
Download and install [Ollama](https://ollama.com), then pull the **Llama 3** model in your terminal:
```bash
ollama pull llama3
```
*(Ensure the Ollama background service is running before launching the app.)*

### 2. Clone the Repository
```bash
git clone https://github.com<your-username>/local-text-to-sql-ollama.git
cd local-text-to-sql-ollama
```

### 3. Create & Activate a Virtual Environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS / Linux
source venv/bin/activate
```

### 4. Install Python Dependencies
```bash
pip install streamlit langchain-community langchain-ollama langchain-core pandas
```

### 5. Run the Application
```bash
streamlit run app.py
```

---

## 💬 Example Prompts

Try asking questions in plain English:
* *"Who scored the highest marks in Math?"*
* *"Show the average grade for each subject."*
* *"List all students who scored above 85."*
* *"How many total students are in the database?"*

---

## 🔮 Future Enhancements

* [ ] **Clean Markdown Fences:** Strip accidental ````sql` markdown backticks from Llama 3 output before execution.
* [ ] **Read-Only Guardrails:** Block destructive SQL keywords (`DROP`, `DELETE`, `UPDATE`, `ALTER`) prior to execution.
* [ ] **Proper DataFrame Conversion:** Use `db._execute(sql_query, fetch="all")` so `pd.DataFrame` renders structured tables reliably.
* [ ] **Schema Viewer Sidebar:** Display table schemas and sample rows in a collapsible Streamlit sidebar.

---

<div align="center">

### 👩‍💻 Author
**Koyel Saha**  
<sub>Aspiring AI / Python Developer</sub>

*Powered by LangChain 1.x • Ollama • Llama 3 • Streamlit*

</div>
