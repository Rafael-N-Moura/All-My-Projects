# 🚀 Argos - Plataforma de Inteligência Política


<div align="center">
  <img src="https://github.com/user-attachments/assets/239d871a-6d91-4c82-bf50-46b7a75f97cd" alt="Argos Logo" width="200"/>
  
  **Transformando dados de mídia e redes sociais em inteligência geográfica e de sentimento para campanhas políticas regionais**
  
  [![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://www.python.org/)
  [![FastAPI](https://img.shields.io/badge/FastAPI-0.116+-green.svg)](https://fastapi.tiangolo.com/)
  [![React](https://img.shields.io/badge/React-18.3+-blue.svg)](https://reactjs.org/)
  [![TypeScript](https://img.shields.io/badge/TypeScript-5.5+-blue.svg)](https://www.typescriptlang.org/)
  [![SQLite](https://img.shields.io/badge/SQLite-3.x-lightgrey.svg)](https://www.sqlite.org/)
</div>

---

## 📖 Sobre o Projeto

**Argos** é uma plataforma inovadora de inteligência política que utiliza inteligência artificial e análise de dados para transformar informações de mídia hiperlocal e redes sociais em insights estratégicos para campanhas políticas regionais.

### 🎯 Objetivo Principal

Fornecer aos candidatos políticos e suas equipes de campanha uma visão clara e em tempo real sobre:
- **Pautas em destaque** na mídia local
- **Sentimento público** em relação a temas específicos
- **Tendências geográficas** de engajamento
- **Análise estratégica** baseada em dados reais

### 🌍 Foco Geográfico

O projeto está focado inicialmente no **estado de Pernambuco, Brasil**, com cobertura de:
- **Região Metropolitana do Recife**
- **Zona da Mata**
- **Agreste**
- **Sertão**

---

## 🏗️ Arquitetura do Sistema

### **Backend (FastAPI + Python)**
```
backend/
├── app/
│   ├── api/routes/          # Endpoints da API
│   ├── services/            # Lógica de negócio
│   ├── models/              # Modelos SQLAlchemy
│   └── schemas/             # Schemas Pydantic
├── data/                    # Banco de dados SQLite
├── scripts/                 # Scripts de automação
└── logs/                    # Logs de execução
```

### **Frontend (React + TypeScript)**
```
frontend/politico-radar-pernambuco/
├── src/
│   ├── components/          # Componentes React
│   ├── hooks/               # Hooks customizados
│   ├── pages/               # Páginas da aplicação
│   └── lib/                 # Utilitários e configurações
├── public/                  # Assets estáticos
└── package.json             # Dependências
```

### **Pipeline de Dados**
```
1. 📰 Coleta de Dados
   ├── NewsAPI (notícias nacionais)
   ├── Scraping hiperlocal (blogs, sites regionais)
   └── Twitter/X (redes sociais)

2. 🧠 Processamento com IA
   ├── Modelagem de tópicos (LDA)
   ├── Categorização semântica (Gemini API)
   └── Análise de sentimento

3. 💾 Armazenamento
   ├── Banco SQLite estruturado
   ├── Metadados enriquecidos
   └── Histórico temporal

4. 📊 Visualização
   ├── Dashboard interativo
   ├── Gráficos em tempo real
   └── Relatórios exportáveis
```

---

## 🚀 Funcionalidades Principais

### **1. Coleta Inteligente de Dados**
- **NewsAPI Integration**: Coleta de notícias nacionais com filtros geográficos
- **Scraping Hiperlocal**: Monitoramento de blogs e sites regionais
- **Social Media Monitoring**: Análise de tweets e engajamento público
- **Agendamento Automático**: Atualizações programadas de dados

### **2. Análise de Inteligência Artificial**
- **Topic Modeling (LDA)**: Identificação automática de pautas em destaque
- **Categorização Semântica**: Classificação inteligente usando Gemini API
- **Análise de Sentimento**: Classificação de opinião pública (Positivo/Neutro/Negativo)
- **Processamento de Linguagem Natural**: Limpeza e estruturação de texto

### **3. Dashboard Interativo**
- **Seleção de Regiões**: Interface para escolha de áreas geográficas
- **Termômetro de Sentimento**: Visualização intuitiva do clima político
- **Tópicos da Mídia**: Distribuição percentual de pautas por região
- **Lista de Tweets**: Análise detalhada de engajamento social
- **Manchetes de Notícias**: Filtros por tópico e relevância

### **4. API RESTful Completa**
- **Endpoints para Regiões**: Dados geográficos e resumos
- **Análise de Sentimento**: Métricas agregadas e tendências
- **Gerenciamento de Tópicos**: CRUD completo de categorias
- **Relatórios**: Exportação de dados em múltiplos formatos

---

## 🛠️ Tecnologias Utilizadas

### **Backend**
- **Python 3.9+**: Linguagem principal
- **FastAPI**: Framework web moderno e rápido
- **SQLAlchemy**: ORM para banco de dados
- **SQLite**: Banco de dados leve e eficiente
- **spaCy**: Processamento de linguagem natural
- **scikit-learn**: Machine learning (LDA)
- **Google Gemini API**: Categorização semântica avançada
- **Pandas**: Manipulação e análise de dados
- **BeautifulSoup4**: Web scraping
- **Tweepy**: API do Twitter/X

### **Frontend**
- **React 18**: Biblioteca de interface
- **TypeScript**: Tipagem estática
- **Vite**: Build tool moderno
- **Tailwind CSS**: Framework de estilos
- **Radix UI**: Componentes acessíveis
- **React Query**: Gerenciamento de estado e cache
- **Recharts**: Gráficos e visualizações
- **Axios**: Cliente HTTP

### **DevOps & Ferramentas**
- **Git**: Controle de versão
- **Virtual Environment**: Isolamento de dependências
- **Logging**: Sistema de logs estruturado
- **Testing**: Testes automatizados
- **Documentação**: Swagger UI automático

---

## 📊 Estrutura do Banco de Dados

### **Tabelas Principais**

#### **`regions`** - Regiões Geográficas
```sql
- id: Identificador único
- name: Nome da região
- description: Descrição detalhada
- created_at: Timestamp de criação
```

#### **`topics`** - Tópicos Identificados
```sql
- id: Identificador único
- region_id: Referência à região
- title: Título do tópico
- percentage: Percentual de relevância
- palavras_chave: Lista de palavras-chave (JSON)
- categoria: Categoria política inferida
- score_mapeamento: Score de confiança
- tipo_mapeamento: 'direto' ou 'inferido'
```

#### **`news`** - Notícias Coletadas
```sql
- id: Identificador único
- title: Título da notícia
- content: Conteúdo completo
- source: Fonte da notícia
- url: Link para leitura
- cidade: Cidade da notícia
- regiao: Região geográfica
- topic_id: Referência ao tópico
- data_publicacao: Data de publicação
```

#### **`sentiment_analytics`** - Análises de Sentimento
```sql
- id: Identificador único
- region_id: Referência à região
- positive_percentage: Percentual positivo
- neutral_percentage: Percentual neutro
- negative_percentage: Percentual negativo
- total_mentions: Total de menções
- last_updated: Última atualização
```

---

## 🚀 Como Executar o Projeto

### **Pré-requisitos**
- Python 3.9 ou superior
- Node.js 18+ e npm
- Git

### **1. Clone o Repositório**
```bash
git clone <repository-url>
cd Argos
```

### **2. Configuração do Backend**
```bash
# Criar ambiente virtual
python -m venv venv

# Ativar ambiente virtual
# Windows:
venv\Scripts\activate
# macOS/Linux:
source venv/bin/activate

# Instalar dependências
pip install -r requirements.txt

# Configurar variáveis de ambiente
cp config/api_keys.py.example config/api_keys.py
# Editar config/api_keys.py com suas chaves de API

# Executar migração de dados
cd backend
python migrate_data.py

# Iniciar servidor
uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

### **3. Configuração do Frontend**
```bash
cd frontend/politico-radar-pernambuco

# Instalar dependências
npm install

# Iniciar servidor de desenvolvimento
npm run dev
```

### **4. Acessar a Aplicação**
- **Frontend**: http://localhost:5173
- **API Docs**: http://localhost:8000/docs
- **Health Check**: http://localhost:8000/health

---

## 🔑 Configuração de APIs

### **Chaves Necessárias**
```python
# config/api_keys.py
NEWS_API_KEY = "sua_chave_newsapi"
GEMINI_API_KEY = "sua_chave_gemini"
TWITTER_BEARER_TOKEN = "seu_token_twitter"
```

### **Serviços Externos**
- **NewsAPI**: https://newsapi.org/ (plano gratuito disponível)
- **Google Gemini**: https://makersuite.google.com/app/apikey
- **Twitter Developer**: https://developer.twitter.com/

---

## 📈 Status de Implementação

### **✅ Fases Concluídas**
- **Fase 1**: Configuração do ambiente e credenciais
- **Fase 2**: Coleta automatizada de dados
- **Fase 3**: Processamento e análise com IA
- **Fase 4**: Armazenamento em banco de dados
- **Fase 5**: Integração frontend-backend

### **🎯 Funcionalidades Implementadas**
- ✅ Sistema completo de coleta de dados
- ✅ Modelagem de tópicos com LDA
- ✅ Categorização semântica com Gemini API
- ✅ Análise de sentimento
- ✅ API RESTful completa
- ✅ Dashboard interativo
- ✅ Banco de dados estruturado
- ✅ Sistema de logs e monitoramento

---

## 🔍 Casos de Uso

### **Para Candidatos Políticos**
- **Identificar pautas quentes** em cada região
- **Monitorar sentimento público** sobre temas específicos
- **Acompanhar tendências** de engajamento
- **Planejar estratégias** de campanha baseadas em dados

### **Para Equipes de Campanha**
- **Análise geográfica** de oportunidades
- **Relatórios automáticos** de performance
- **Alertas em tempo real** sobre mudanças de sentimento
- **Histórico temporal** para análise de tendências

### **Para Analistas Políticos**
- **Dados estruturados** para pesquisas acadêmicas
- **Métricas quantitativas** de engajamento
- **Análise comparativa** entre regiões
- **Exportação de dados** para análises externas

---

## 📚 Documentação Adicional

- **Metodologia**: `metodologia.md` - Detalhes técnicos da implementação
- **Plano de Implementação**: `PLANO_IMPLEMENTACAO_GEMINI_COMPLETO.md` - Roadmap completo
- **Integração**: `INTEGRACAO_COMPLETA.md` - Status da integração frontend-backend
- **Fase 4**: `FASE4_IMPLEMENTADA.md` - Detalhes da implementação do banco de dados
- **Melhorias**: `MELHORIAS_IMPLEMENTADAS.md` - Histórico de melhorias

---

## 🤝 Contribuição

### **Como Contribuir**
1. Fork o projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

### **Padrões de Código**
- **Python**: PEP 8, type hints
- **TypeScript**: ESLint, Prettier
- **Commits**: Conventional Commits
- **Documentação**: Markdown com exemplos

---

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo `LICENSE` para mais detalhes.

---

## 📞 Contato

- **Projeto**: Argos - Plataforma de Inteligência Política
- **Repositório**: [GitHub](https://github.com/seu-usuario/argos)
- **Issues**: [GitHub Issues](https://github.com/seu-usuario/argos/issues)

---

<div align="center">
  <p><strong>Argos</strong> - Transformando dados em inteligência política</p>
  <p>Construído com ❤️ para democratizar o acesso à inteligência política</p>
</div>
