   # Farol - App de Gestão Financeira para Motoristas

   ## 📱 Sobre o Projeto

   O **Farol** é um aplicativo móvel desenvolvido em Flutter para ajudar motoristas de aplicativo a gerenciar suas finanças de forma simples e eficiente. O app permite registrar corridas e despesas, visualizar lucros em tempo real e obter insights sobre a rentabilidade do negócio.

   ## 🎯 Objetivos

   - **Gestão Financeira Simplificada**: Interface intuitiva para registrar ganhos e gastos
   - **Visão Clara da Lucratividade**: Dashboard com resumos diários, semanais e mensais
   - **Controle de Custos**: Categorização de despesas (combustível, manutenção, etc.)
   - **Análise de Performance**: Histórico detalhado de transações

   ## 👤 Persona Principal

   **Carlos, o Motorista Pragmático**
   - 58 anos, motorista de aplicativo
   - Trabalha para complementar a renda familiar
   - Valoriza simplicidade e rapidez
   - Precisa de clareza sobre sua lucratividade real

   ## 🚀 Funcionalidades

   ### ✅ Implementadas (MVP)

   1. **Dashboard Principal**
      - Resumo financeiro do dia atual
      - Comparativo semanal e mensal
      - Cards visuais para ganhos, gastos e lucro

   2. **Registro de Transações**
      - Adicionar corridas com valor, data/hora, distância e duração
      - Registrar despesas com categorização
      - Interface simples e rápida

   3. **Histórico de Transações**
      - Lista completa de todas as transações
      - Filtros por tipo (corridas/despesas)
      - Exclusão de registros

   4. **Armazenamento Local**
      - Dados persistidos localmente no dispositivo
      - Backup automático via SharedPreferences

   ### 🔮 Funcionalidades Futuras

   1. **Insights com IA**
      - Análise semanal automatizada
      - Recomendações personalizadas
      - Identificação de padrões de lucratividade

   2. **Integração com APIs**
      - Importação automática de corridas da 99/Uber
      - Sincronização com relatórios das plataformas

   3. **Otimização de Ganhos**
      - Mapa de calor de áreas lucrativas
      - Sugestões de horários ideais
      - Análise de custo por quilômetro

   ## 🛠️ Tecnologias Utilizadas

   - **Flutter**: Framework multiplataforma
   - **Provider**: Gerenciamento de estado
   - **SharedPreferences**: Armazenamento local
   - **Intl**: Formatação de datas e moedas
   - **UUID**: Geração de identificadores únicos

   ## 📱 Como Executar

   ### Pré-requisitos

   - Flutter SDK (versão 3.7.2 ou superior)
   - Dart SDK
   - Android Studio / VS Code
   - Dispositivo Android/iOS ou emulador

   ### Instalação

   1. Clone o repositório:
   ```bash
   git clone [URL_DO_REPOSITORIO]
   cd farol
   ```

   2. Instale as dependências:
   ```bash
   flutter pub get
   ```

   3. Execute o aplicativo:
   ```bash
   flutter run
   ```

   ## 📊 Estrutura do Projeto

   ```
   lib/
   ├── models/
   │   └── transaction.dart          # Modelo de dados para transações
   ├── providers/
   │   └── transaction_provider.dart # Gerenciamento de estado
   ├── screens/
   │   ├── dashboard_screen.dart     # Tela principal
   │   ├── add_transaction_screen.dart # Adicionar transação
   │   └── transaction_list_screen.dart # Lista de transações
   ├── services/
   │   └── storage_service.dart      # Serviço de armazenamento
   ├── utils/
   │   └── formatters.dart           # Utilitários de formatação
   ├── widgets/
   │   └── dashboard_card.dart       # Widget reutilizável
   └── main.dart                     # Ponto de entrada
   ```

   ## 🎨 Design System

   - **Cores**: Laranja como cor principal (representando o "farol")
   - **Tipografia**: Material Design 3
   - **Componentes**: Cards com gradientes sutis
   - **Ícones**: Material Icons
   - **Layout**: Responsivo e adaptável

   ## 📈 Métricas de Sucesso

   - Aumento de 15% na receita líquida por hora trabalhada
   - Redução de 10% no custo por quilômetro rodado
   - Taxa de adoção: 80% dos registros feitos via app
   - NPS (Net Promoter Score) acima de 50

   ## 🔒 Privacidade e Segurança

   - Dados armazenados localmente no dispositivo
   - Conformidade com LGPD
   - Criptografia de dados sensíveis
   - Sem coleta de dados pessoais desnecessários


   ---

   **Farol** - Iluminando o caminho para uma gestão financeira mais inteligente! 🚗💡
