# **Farol \- Financial Management App for Drivers**

## **📱 About the Project**

**Farol** is a mobile application developed in Flutter to help app drivers manage their finances simply and efficiently. The app allows for logging rides and expenses, viewing profits in real-time, and gaining insights into the business's profitability.

## **🎯 Objectives**

* **Simplified Financial Management**: Intuitive interface for recording earnings and expenses.  
* **Clear View of Profitability**: Dashboard with daily, weekly, and monthly summaries.  
* **Cost Control**: Categorization of expenses (fuel, maintenance, etc.).  
* **Performance Analysis**: Detailed transaction history.

## **👤 Main Persona**

**Carlos, the Pragmatic Driver**

* 58 years old, app driver.  
* Works to supplement family income.  
* Values simplicity and speed.  
* Needs clarity on his real profitability.

## **🚀 Features**

### **✅ Implemented (MVP)**

1. **Main Dashboard**  
   * Financial summary of the current day.  
   * Weekly and monthly comparison.  
   * Visual cards for earnings, expenses, and profit.  
2. **Transaction Logging**  
   * Add rides with amount, date/time, distance, and duration.  
   * Record expenses with categorization.  
   * Simple and fast interface.  
3. **Transaction History**  
   * Complete list of all transactions.  
   * Filters by type (rides/expenses).  
   * Deletion of records.  
4. **Local Storage**  
   * Data persisted locally on the device.  
   * Automatic backup via SharedPreferences.

### **🔮 Future Features**

1. **AI-Powered Insights**  
   * Automated weekly analysis.  
   * Personalized recommendations.  
   * Identification of profitability patterns.  
2. **API Integration**  
   * Automatic import of rides from 99/Uber.  
   * Synchronization with platform reports.  
3. **Earnings Optimization**  
   * Heatmap of profitable areas.  
   * Suggestions for ideal times.  
   * Cost-per-kilometer analysis.

## **🛠️ Technologies Used**

* **Flutter**: Cross-platform framework  
* **Provider**: State management  
* **SharedPreferences**: Local storage  
* **Intl**: Date and currency formatting  
* **UUID**: Unique identifier generation

## **📱 How to Run**

### **Prerequisites**

* Flutter SDK (version 3.7.2 or higher)  
* Dart SDK  
* Android Studio / VS Code  
* Android/iOS device or emulator

### **Installation**

1. Clone the repository:  
   git clone \[REPOSITORY\_URL\]  
   cd farol

2. Install the dependencies:  
   flutter pub get

3. Run the application:  
   flutter run

## **📊 Project Structure**

lib/  
├── models/  
│   └── transaction.dart          \# Data model for transactions  
├── providers/  
│   └── transaction\_provider.dart \# State management  
├── screens/  
│   ├── dashboard\_screen.dart     \# Main screen  
│   ├── add\_transaction\_screen.dart \# Add transaction  
│   └── transaction\_list\_screen.dart \# Transaction list  
├── services/  
│   └── storage\_service.dart      \# Storage service  
├── utils/  
│   └── formatters.dart           \# Formatting utilities  
├── widgets/  
│   └── dashboard\_card.dart       \# Reusable widget  
└── main.dart                     \# Entry point

## **🎨 Design System**

* **Colors**: Orange as the main color (representing a "lighthouse" or "headlight")  
* **Typography**: Material Design 3  
* **Components**: Cards with subtle gradients  
* **Icons**: Material Icons  
* **Layout**: Responsive and adaptive

## **📈 Success Metrics**

* 15% increase in net revenue per hour worked  
* 10% reduction in cost per kilometer driven  
* Adoption rate: 80% of records made via the app  
* NPS (Net Promoter Score) above 50

## **🔒 Privacy and Security**

* Data stored locally on the device  
* Compliance with LGPD (Brazilian General Data Protection Law)  
* Encryption of sensitive data  
* No collection of unnecessary personal data

**Farol** \- Lighting the way to smarter financial management\! 🚗💡