# Magento E-commerce Automation Testing

This project contains end-to-end test automation for the Magento demo website: [https://magento.softwaretestingboard.com](https://magento.softwaretestingboard.com). The goal is to validate shopping cart behavior, checkout process, search results, and basic security validations using Selenium WebDriver and TestNG.

---


## 📌 Project Structure

- **Language**: Java
- **Framework**: TestNG
- **Build Tool**: Maven
- **Automation Tools**: Selenium WebDriver
- **Design Pattern**: Page Object Model (POM)

---

## 📂 Test Cases Covered

| Test Case ID | Description |
|--------------|-------------|
| `TC_SI_01`    | Search with an invalid keyword shows proper validation |
| `TC_ATC_01`   | Adding products to cart calculates the total correctly |
| `TC_COC_01`   | Checkout rejects invalid personal information |
| `XSS_SQL_01`  | Input fields are protected against XSS/SQL injection |

---

## 🚀 How to Run the Tests

1. **Install Java & Maven**
2. **Clone the repo**
3. **Run using Maven:**
   ```bash
   mvn clean test

👨‍💻 Author: Gerges Samer  
📧 Contact: gergessamer511@gmail.com
