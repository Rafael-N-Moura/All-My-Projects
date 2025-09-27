# 🏠 FlatTrack

**FlatTrack** é um aplicativo desenvolvido em Flutter para gerenciamento colaborativo de tarefas domésticas em residências compartilhadas. O app facilita a organização e distribuição de responsabilidades entre moradores, promovendo um ambiente mais harmonioso e organizado.

## 📱 Sobre o Projeto

FlatTrack foi criado para resolver um problema comum em residências compartilhadas: a falta de organização e distribuição justa das tarefas domésticas. O aplicativo oferece uma plataforma gamificada onde moradores podem:

- **Criar e gerenciar tarefas** domésticas de forma colaborativa
- **Competir de forma saudável** através de um sistema de ranking baseado em pontos
- **Acompanhar ciclos** de limpeza e organização da casa
- **Gerenciar finanças** compartilhadas entre moradores
- **Visualizar progresso** através de barras de progresso animadas

## 🎯 Principais Funcionalidades

### ✅ Sistema de Tarefas
- Criação de tarefas com categorias (Limpeza, Cozinha, Organização, etc.)
- Sistema de pontos baseado na dificuldade das tarefas
- Marcação de tarefas como concluídas
- Exclusão de tarefas com confirmação
- Interface intuitiva com cards deslizáveis

### 🏆 Sistema de Ranking
- Ranking baseado em pontos acumulados por morador
- Feed de atividades mostrando ações recentes
- Visualização de progresso durante o ciclo atual
- Gamificação para incentivar participação

### 💰 Gestão Financeira
- Registro de dívidas entre moradores
- Controle de valores devidos e a receber
- Marcação de dívidas como quitadas
- Resumo financeiro visual

### 🏡 Gestão de Casas
- Criação e participação em casas
- Sistema de ciclos para organização
- Informações detalhadas sobre a casa atual

## 🛠️ Tecnologias Utilizadas

### Frontend
- **Flutter** - Framework multiplataforma para desenvolvimento mobile
- **Dart** - Linguagem de programação principal

### Backend & Banco de Dados
- **Supabase** - Backend-as-a-Service (BaaS) com PostgreSQL
- **PostgreSQL** - Banco de dados relacional

### Arquitetura & Padrões
- **Clean Architecture** - Separação clara entre camadas (Data, Domain, Presentation)
- **Repository Pattern** - Abstração da camada de dados
- **Use Cases** - Lógica de negócio isolada
- **Riverpod** - Gerenciamento de estado reativo

### Bibliotecas Principais
- `supabase_flutter` - Integração com Supabase
- `riverpod` - Gerenciamento de estado
- `stylish_bottom_bar` - Barra de navegação estilizada
- `flutter_slidable` - Cards deslizáveis para ações
- `get_it` - Injeção de dependências
- `result_dart` - Tratamento de resultados e erros

### Design System
- **Poppins** - Fonte principal do aplicativo
- **Material Design** - Design system do Google
- **Cores personalizadas** - Paleta de cores vibrante e moderna

## 🏗️ Arquitetura do Projeto

O projeto segue os princípios da **Clean Architecture**, organizando o código em camadas bem definidas:

```
lib/
├── core/                    # Funcionalidades core do app
│   ├── theme/              # Sistema de design (cores, tipografia)
│   └── ...
├── features/               # Módulos de funcionalidades
│   ├── auth/               # Autenticação
│   ├── dashboard/          # Dashboard principal
│   ├── tasks/              # Sistema de tarefas
│   ├── ranking/            # Sistema de ranking
│   ├── finances/           # Gestão financeira
│   ├── houses/             # Gestão de casas
│   └── ...
└── routes/                 # Configuração de rotas
```

### Estrutura de Features
Cada feature segue a mesma estrutura:

```
feature/
├── data/                   # Camada de dados
│   ├── datasources/        # Fontes de dados (Supabase)
│   ├── models/             # Modelos de dados
│   └── repositories/       # Implementação dos repositórios
├── domain/                 # Camada de domínio
│   ├── entities/           # Entidades de negócio
│   ├── repositories/       # Interfaces dos repositórios
│   └── usecases/           # Casos de uso
└── presentation/           # Camada de apresentação
    ├── controllers/        # Controladores (Riverpod)
    ├── pages/              # Páginas/Views
    └── widgets/            # Componentes reutilizáveis
```

## 🚀 Como Executar o Projeto

### Pré-requisitos
- Flutter SDK (versão 3.7.2 ou superior)
- Dart SDK
- Android Studio / VS Code
- Conta no Supabase

### Instalação

1. **Clone o repositório**
   ```bash
   git clone <url-do-repositorio>
   cd flat_track
   ```

2. **Instale as dependências**
   ```bash
   flutter pub get
   ```

3. **Configure o Supabase**
   - Crie um projeto no [Supabase](https://supabase.com)
   - Configure as tabelas necessárias
   - Adicione as credenciais no projeto

4. **Execute o aplicativo**
   ```bash
   flutter run
   ```

## 📊 Banco de Dados

O projeto utiliza Supabase com PostgreSQL. As principais tabelas incluem:

- **users** - Dados dos usuários
- **houses** - Informações das casas
- **tasks** - Tarefas domésticas
- **task_completions** - Histórico de conclusão de tarefas
- **cycles** - Ciclos de organização
- **rankings** - Dados de ranking

## 🎨 Design System

### Cores
- **Primary**: `#3366FF` (Azul vibrante)
- **Secondary**: `#FFCC00` (Amarelo vibrante)
- **Background**: Branco
- **Text Primary**: `#333333` (Cinza escuro)
- **Text Secondary**: `#666666` (Cinza médio)
- **Error**: `#FF4444` (Vermelho)
- **Success**: `#44CC66` (Verde)

### Tipografia
- **Fonte**: Poppins
- **Pesos**: Regular (400), Medium (500), Bold (700)

## 🔄 Fluxo Principal

1. **Autenticação** - Login/cadastro do usuário
2. **Seleção de Casa** - Escolha ou criação de uma casa
3. **Dashboard** - Acesso às funcionalidades principais
4. **Gestão de Tarefas** - Criação, conclusão e exclusão
5. **Ranking** - Visualização de pontuação e atividades
6. **Finanças** - Controle de dívidas entre moradores

## 🚧 Status do Desenvolvimento

### ✅ Implementado
- Sistema de autenticação
- Gestão de tarefas completa
- Sistema de ranking e pontos
- Dashboard com navegação
- Gestão de casas e ciclos
- Interface responsiva e moderna

### 🔄 Em Desenvolvimento
- Sistema de finanças (parcialmente implementado)
- Notificações push
- Configurações do usuário

### 📋 Próximas Funcionalidades
- Relatórios de produtividade
- Integração com calendário
- Sistema de lembretes
- Exportação de dados



**FlatTrack** - Transformando casas compartilhadas em lares organizados! 🏠✨