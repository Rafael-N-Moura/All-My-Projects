# 🚀 Argos - Political Intelligence Platform

<div align="center">
  <img src="https://github.com/user-attachments/assets/239d871a-6d91-4c82-bf50-46b7a75f97cd" alt="Argos Logo" width="200"/>

**Turning hyperlocal media and social media data into geographic and sentiment intelligence for regional political campaigns**

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.116+-green.svg)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/React-18.3+-blue.svg)](https://reactjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.5+-blue.svg)](https://www.typescriptlang.org/)
[![SQLite](https://img.shields.io/badge/SQLite-3.x-lightgrey.svg)](https://www.sqlite.org/)

</div>

---

## 📖 About the Project

**Argos** is an innovative political intelligence platform that uses artificial intelligence and data analysis to transform hyperlocal media and social media information into strategic insights for regional political campaigns.

### 🎯 Main Objective

Provide political candidates and their campaign teams with a clear, real-time view of:

* **Top issues** in local media
* **Public sentiment** regarding specific topics
* **Geographic engagement trends**
* **Strategic analysis** based on real data

### 🌍 Geographic Focus

The project initially focuses on the **state of Pernambuco, Brazil**, covering:

* **Metropolitan Region of Recife (Região Metropolitana do Recife)**
* **Zona da Mata**
* **Agreste**
* **Sertão**

---

## 🏗️ System Architecture

### **Backend (FastAPI + Python)**

```
backend/
├── app/
│   ├── api/routes/          # API endpoints
│   ├── services/            # Business logic
│   ├── models/              # SQLAlchemy models
│   └── schemas/             # Pydantic schemas
├── data/                    # SQLite database
├── scripts/                 # Automation scripts
└── logs/                    # Execution logs
```

### **Frontend (React + TypeScript)**

```
frontend/politico-radar-pernambuco/
├── src/
│   ├── components/          # React components
│   ├── hooks/               # Custom hooks
│   ├── pages/               # Application pages
│   └── lib/                 # Utilities and configurations
├── public/                  # Static assets
└── package.json             # Dependencies
```

### **Data Pipeline**

```
1. 📰 Data Collection
   ├── NewsAPI (national news)
   ├── Hyperlocal scraping (blogs, regional sites)
   └── Twitter/X (social media)

2. 🧠 AI Processing
   ├── Topic modeling (LDA)
   ├── Semantic categorization (Gemini API)
   └── Sentiment analysis

3. 💾 Storage
   ├── Structured SQLite database
   ├── Enriched metadata
   └── Time series history

4. 📊 Visualization
   ├── Interactive dashboard
   ├── Real-time charts
   └── Exportable reports
```

---

## 🚀 Main Features

### **1. Smart Data Collection**

* **NewsAPI Integration**: Collect national news with geographic filters
* **Hyperlocal Scraping**: Monitor blogs and regional websites
* **Social Media Monitoring**: Analyze tweets and public engagement
* **Automated Scheduling**: Periodic data updates

### **2. Artificial Intelligence Analysis**

* **Topic Modeling (LDA)**: Automatic identification of prominent issues
* **Semantic Categorization**: Intelligent classification using the Gemini API
* **Sentiment Analysis**: Public opinion classification (Positive/Neutral/Negative)
* **Natural Language Processing**: Text cleaning and structuring

### **3. Interactive Dashboard**

* **Region Selection**: Interface to choose geographic areas
* **Sentiment Gauge**: Intuitive view of the political climate
* **Media Topics**: Percentage distribution of issues by region
* **Tweet List**: Detailed analysis of social engagement
* **News Headlines**: Filters by topic and relevance

### **4. Full RESTful API**

* **Region Endpoints**: Geographic data and summaries
* **Sentiment Analysis**: Aggregated metrics and trends
* **Topic Management**: Full CRUD for categories
* **Reports**: Export data in multiple formats

---

## 🛠️ Technologies Used

### **Backend**

* **Python 3.9+**: Primary language
* **FastAPI**: Modern, fast web framework
* **SQLAlchemy**: ORM for the database
* **SQLite**: Lightweight, efficient database
* **spaCy**: Natural language processing
* **scikit-learn**: Machine learning (LDA)
* **Google Gemini API**: Advanced semantic categorization
* **Pandas**: Data manipulation and analysis
* **BeautifulSoup4**: Web scraping
* **Tweepy**: Twitter/X API client

### **Frontend**

* **React 18**: UI library
* **TypeScript**: Static typing
* **Vite**: Modern build tool
* **Tailwind CSS**: Styling framework
* **Radix UI**: Accessible components
* **React Query**: State and cache management
* **Recharts**: Charts and visualizations
* **Axios**: HTTP client

### **DevOps & Tools**

* **Git**: Version control
* **Virtual Environment**: Dependency isolation
* **Logging**: Structured logging system
* **Testing**: Automated tests
* **Documentation**: Automatic Swagger UI

---

## 📊 Database Structure

### **Main Tables**

#### **`regions`** - Geographic Regions

```sql
- id: Unique identifier
- name: Region name
- description: Detailed description
- created_at: Creation timestamp
```

#### **`topics`** - Identified Topics

```sql
- id: Unique identifier
- region_id: Reference to the region
- title: Topic title
- percentage: Relevance percentage
- palavras_chave: List of keywords (JSON)
- categoria: Inferred political category
- score_mapeamento: Confidence mapping score
- tipo_mapeamento: 'direct' or 'inferred'
```

> Note: `palavras_chave`, `categoria`, `score_mapeamento`, and `tipo_mapeamento` keep original field names where appropriate; consider renaming to English equivalents (`keywords`, `category`, `mapping_score`, `mapping_type`) if you prefer full English schema.

#### **`news`** - Collected News

```sql
- id: Unique identifier
- title: News title
- content: Full content
- source: News source
- url: Link to read
- cidade: City of the news item
- regiao: Geographic region
- topic_id: Reference to topic
- data_publicacao: Publication date
```

#### **`sentiment_analytics`** - Sentiment Analyses

```sql
- id: Unique identifier
- region_id: Reference to the region
- positive_percentage: Positive percentage
- neutral_percentage: Neutral percentage
- negative_percentage: Negative percentage
- total_mentions: Total mentions
- last_updated: Last update timestamp
```

---

## 🚀 How to Run the Project

### **Prerequisites**

* Python 3.9 or newer
* Node.js 18+ and npm
* Git

### **1. Clone the Repository**

```bash
git clone <repository-url>
cd Argos
```

### **2. Backend Setup**

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp config/api_keys.py.example config/api_keys.py
# Edit config/api_keys.py with your API keys

# Run data migration
cd backend
python migrate_data.py

# Start server
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### **3. Frontend Setup**

```bash
cd frontend/politico-radar-pernambuco

# Install dependencies
npm install

# Start development server
npm run dev
```

### **4. Access the Application**

* **Frontend**: [http://localhost:5173](http://localhost:5173)
* **API Docs**: [http://localhost:8000/docs](http://localhost:8000/docs)
* **Health Check**: [http://localhost:8000/health](http://localhost:8000/health)

---

## 🔑 API Configuration

### **Required Keys**

```python
# config/api_keys.py
NEWS_API_KEY = "your_newsapi_key"
GEMINI_API_KEY = "your_gemini_key"
TWITTER_BEARER_TOKEN = "your_twitter_token"
```

### **External Services**

* **NewsAPI**: [https://newsapi.org/](https://newsapi.org/) (free tier available)
* **Google Gemini**: [https://makersuite.google.com/app/apikey](https://makersuite.google.com/app/apikey)
* **Twitter Developer**: [https://developer.twitter.com/](https://developer.twitter.com/)

---

## 📈 Implementation Status

### **✅ Completed Phases**

* **Phase 1**: Environment and credentials setup
* **Phase 2**: Automated data collection
* **Phase 3**: AI processing and analysis
* **Phase 4**: Database storage
* **Phase 5**: Frontend-backend integration

### **🎯 Implemented Features**

* ✅ Complete data collection system
* ✅ Topic modeling with LDA
* ✅ Semantic categorization with Gemini API
* ✅ Sentiment analysis
* ✅ Full RESTful API
* ✅ Interactive dashboard
* ✅ Structured database
* ✅ Logging and monitoring system

---

## 🔍 Use Cases

### **For Political Candidates**

* **Identify hot topics** in each region
* **Monitor public sentiment** on specific issues
* **Track engagement trends**
* **Plan campaign strategies** based on data

### **For Campaign Teams**

* **Geographic analysis** of opportunities
* **Automated performance reports**
* **Real-time alerts** on sentiment shifts
* **Time series history** for trend analysis

### **For Political Analysts**

* **Structured data** for academic research
* **Quantitative engagement metrics**
* **Comparative analysis** between regions
* **Export data** for external analysis

---

## 📚 Additional Documentation

* **Methodology**: `metodologia.md` - Technical implementation details
* **Implementation Plan**: `PLANO_IMPLEMENTACAO_GEMINI_COMPLETO.md` - Complete roadmap
* **Integration**: `INTEGRACAO_COMPLETA.md` - Frontend-backend integration status
* **Phase 4**: `FASE4_IMPLEMENTADA.md` - Database implementation details
* **Improvements**: `MELHORIAS_IMPLEMENTADAS.md` - History of improvements

---

## 🤝 Contributing

### **How to Contribute**

1. Fork the project
2. Create a branch for your feature (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### **Code Standards**

* **Python**: PEP 8, type hints
* **TypeScript**: ESLint, Prettier
* **Commits**: Conventional Commits
* **Documentation**: Markdown with examples

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## 📞 Contact

* **Project**: Argos - Political Intelligence Platform
* **Repository**: [GitHub](https://github.com/seu-usuario/argos)
* **Issues**: [GitHub Issues](https://github.com/seu-usuario/argos/issues)

---

<div align="center">
  <p><strong>Argos</strong> - Turning data into political intelligence</p>
  <p>Built with ❤️ to democratize access to political intelligence</p>
</div>
