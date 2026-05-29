AI Shopping Assistant

An intelligent conversational shopping assistant powered by **LangChain**, **Groq LLMs**, and **Streamlit**.
The assistant enables users to search products using natural language or images, apply smart filters, and place orders through an interactive chat interface.

Features

* Natural Language Product Search
  Search products conversationally using queries like:

  > *“organic honey under $15 with 4+ star ratings”*

* Image-Based Product Discovery
  Upload a product image and the assistant identifies it using a vision model and recommends similar products.

* Smart Filtering
  Filter products by:

  * Price
  * Ratings
  * Organic certification

* Live Rating Integration
  Retrieves customer ratings dynamically from the reviews database.

* Conversational Checkout
  Place orders directly through chat interactions.

* Modern Streamlit Interface
  Clean and responsive chat-based UI with image upload support.
Project Architecture

```text
User Input (Text / Image)
        │
        ▼
   Streamlit Frontend
        │
        ▼
   LangChain Shopping Agent
   ├── Image Understanding Tool
   ├── Product Search Tool
   ├── Reviews & Ratings Tool
   └── Checkout Tool
        │
        ▼
     SQLite Database
```



Project Structure

```bash
shopping-agent/
│
├── app.py                 # Streamlit frontend
├── shopping_agent.py      # LangChain agent setup & tools
├── reviews_api.py         # Review & rating utilities
├── setup_db.py            # Database initialization & sample data
├── store.db               # SQLite database
├── requirements.txt
└── .env                   # Environment variables
```


Tech Stack

| Layer           | Technology         |
| --------------- | ------------------ |
| Frontend        | Streamlit          |
| Agent Framework | LangChain          |
| LLM             | Qwen3-32B via Groq |
| Vision Model    | Llama 4 Scout 17B  |
| Database        | SQLite             |
| Language        | Python 3.10+       |

---

Getting Started

1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/shopping-agent.git
cd shopping-agent
```

---

2. Create a Virtual Environment

Windows

```bash
python -m venv venv
venv\Scripts\activate
```

macOS/Linux

```bash
python3 -m venv venv
source venv/bin/activate
```

3. Install Dependencies

```bash
pip install -r requirements.txt
```

---

4. Configure Environment Variables

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_groq_api_key_here
```

Get your free API key from:

https://console.groq.com

---

5. Initialize the Database

```bash
python setup_db.py
```

This will create:

* `products` table
* `reviews` table
* `orders` table

with pre-seeded sample data.

---

6. Run the Application

```bash
streamlit run app.py
```

Open your browser at:

```text
http://localhost:8501
```

---

Example Queries

| User Prompt                      | Assistant Action                      |
| -------------------------------- | ------------------------------------- |
| `I want organic honey under $15` | Searches and filters products         |
| `Show me nuts with 4.5+ stars`   | Retrieves highly rated products       |
| `Order the first one`            | Places an order                       |
| *(Upload product image)*         | Identifies and finds similar products |

---

Database Schema

Products Table

```sql
id
name
category
price
description
is_organic
```

Reviews Table

```sql
id
product_id
rating
reviewer_name
review_text
```

Orders Table

```sql
id
product_id
product_name
price
ordered_at
```

---

Product Categories

The demo database includes products across multiple categories:

* Honey
* Oils
* Nuts
* Seeds
* Grains
* Tea
* Coffee
* Snacks
* Dairy Alternatives

---

Environment Variables

| Variable       | Description                 | Required |
| -------------- | --------------------------- | -------- |
| `GROQ_API_KEY` | API key for Groq LLM access | Yes      |

---

Contributing

Contributions are welcome.

Steps to contribute:

1. Fork the repository
2. Create a feature branch

```bash
git checkout -b feature-name
```

3. Commit your changes

```bash
git commit -m "Add feature"
```

4. Push to GitHub

```bash
git push origin feature-name
```

5. Open a Pull Request

---

License

This project is licensed under the **MIT License**.

---

Future Improvements

* User authentication
* Personalized recommendations
* Vector search for semantic product matching
* Order tracking system
* Multi-vendor marketplace support
* Voice-based shopping assistant

---

Author

Developed using:

* LangChain
* Groq LLMs
* Streamlit
* Python

If you found this project useful, consider giving it a star on GitHub.
