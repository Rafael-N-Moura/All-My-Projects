# **🏠 FlatTrack**

**FlatTrack** is an application developed in Flutter for the collaborative management of household chores in shared residences. The app facilitates the organization and distribution of responsibilities among residents, promoting a more harmonious and organized environment.

## **📱 About the Project**

FlatTrack was created to solve a common problem in shared residences: the lack of organization and fair distribution of household chores. The application offers a gamified platform where residents can:

* **Create and manage** household chores collaboratively  
* **Compete in a healthy way** through a point-based ranking system  
* **Track** the house's cleaning and organization cycles  
* **Manage** shared finances among residents  
* **Visualize progress** through animated progress bars

## **🎯 Key Features**

### **✅ Task System**

* Creation of tasks with categories (Cleaning, Cooking, Organization, etc.)  
* Point system based on task difficulty  
* Marking tasks as completed  
* Deletion of tasks with confirmation  
* Intuitive interface with slidable cards

### **🏆 Ranking System**

* Ranking based on accumulated points per resident  
* Activity feed showing recent actions  
* Progress visualization during the current cycle  
* Gamification to encourage participation

### **💰 Financial Management**

* Recording of debts between residents  
* Control of amounts owed and receivable  
* Marking debts as settled  
* Visual financial summary

### **🏡 House Management**

* Creation and participation in houses  
* Cycle system for organization  
* Detailed information about the current house

## **🛠️ Technologies Used**

### **Frontend**

* **Flutter** \- Cross-platform framework for mobile development  
* **Dart** \- Main programming language

### **Backend & Database**

* **Supabase** \- Backend-as-a-Service (BaaS) with PostgreSQL  
* **PostgreSQL** \- Relational database

### **Architecture & Patterns**

* **Clean Architecture** \- Clear separation between layers (Data, Domain, Presentation)  
* **Repository Pattern** \- Abstraction of the data layer  
* **Use Cases** \- Isolated business logic  
* **Riverpod** \- Reactive state management

### **Main Libraries**

* supabase\_flutter \- Integration with Supabase  
* riverpod \- State management  
* stylish\_bottom\_bar \- Styled navigation bar  
* flutter\_slidable \- Slidable cards for actions  
* get\_it \- Dependency injection  
* result\_dart \- Result and error handling

### **Design System**

* **Poppins** \- Main font of the application  
* **Material Design** \- Google's design system  
* **Custom colors** \- Vibrant and modern color palette

## **🏗️ Project Architecture**

The project follows the principles of **Clean Architecture**, organizing the code into well-defined layers:  
lib/  
├── core/                    \# Core app features  
│   ├── theme/              \# Design system (colors, typography)  
│   └── ...  
├── features/               \# Feature modules  
│   ├── auth/               \# Authentication  
│   ├── dashboard/          \# Main dashboard  
│   ├── tasks/              \# Task system  
│   ├── ranking/            \# Ranking system  
│   ├── finances/           \# Financial management  
│   ├── houses/             \# House management  
│   └── ...  
└── routes/                 \# Route configuration

### **Feature Structure**

Each feature follows the same structure:  
feature/  
├── data/                   \# Data layer  
│   ├── datasources/        \# Data sources (Supabase)  
│   ├── models/             \# Data models  
│   └── repositories/       \# Repository implementation  
├── domain/                 \# Domain layer  
│   ├── entities/           \# Business entities  
│   ├── repositories/       \# Repository interfaces  
│   └── usecases/           \# Use cases  
└── presentation/           \# Presentation layer  
    ├── controllers/        \# Controllers (Riverpod)  
    ├── pages/              \# Pages/Views  
    └── widgets/            \# Reusable components

## **🚀 How to Run the Project**

### **Prerequisites**

* Flutter SDK (version 3.7.2 or higher)  
* Dart SDK  
* Android Studio / VS Code  
* Supabase account

### **Installation**

1. **Clone the repository**  
   git clone \<repository-url\>  
   cd flat\_track

2. **Install the dependencies**  
   flutter pub get

3. **Configure Supabase**  
   * Create a project on [Supabase](https://supabase.com)  
   * Set up the necessary tables  
   * Add the credentials to the project  
4. **Run the application**  
   flutter run

## **📊 Database**

The project uses Supabase with PostgreSQL. The main tables include:

* **users** \- User data  
* **houses** \- House information  
* **tasks** \- Household chores  
* **task\_completions** \- Task completion history  
* **cycles** \- Organization cycles  
* **rankings** \- Ranking data

## **🎨 Design System**

### **Colors**

* **Primary**: \#3366FF (Vibrant Blue)  
* **Secondary**: \#FFCC00 (Vibrant Yellow)  
* **Background**: White  
* **Text Primary**: \#333333 (Dark Gray)  
* **Text Secondary**: \#666666 (Medium Gray)  
* **Error**: \#FF4444 (Red)  
* **Success**: \#44CC66 (Green)

### **Typography**

* **Font**: Poppins  
* **Weights**: Regular (400), Medium (500), Bold (700)

## **🔄 Main Flow**

1. **Authentication** \- User login/registration  
2. **House Selection** \- Choosing or creating a house  
3. **Dashboard** \- Access to main features  
4. **Task Management** \- Creation, completion, and deletion  
5. **Ranking** \- Viewing scores and activities  
6. **Finances** \- Managing debts between residents

## **🚧 Development Status**

### **✅ Implemented**

* Authentication system  
* Complete task management  
* Ranking and points system  
* Dashboard with navigation  
* House and cycle management  
* Responsive and modern interface

### **🔄 In Development**

* Finance system (partially implemented)  
* Push notifications  
* User settings

### **📋 Upcoming Features**

* Productivity reports  
* Calendar integration  
* Reminder system  
* Data export

**FlatTrack** \- Turning shared houses into organized homes\! 🏠✨