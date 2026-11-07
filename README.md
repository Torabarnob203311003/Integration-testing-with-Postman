# Integration Testing with Postman & Newman

### **Batch No:** 20  
### **Topic:** Assignment on API Testing (Integration Testing with Postman)  

---

## 📌 Project Overview
This repository contains an automated API integration test suite for the **DMoney Transaction API** using **Postman** and **Newman**. The tests validate an end-to-end fintech workflow involving Admin, System, Agent, Customer, and Merchant account roles, covering positive and negative test scenarios with assertions on balance, service fees, and commission calculations.

---

## 🔗 Important Links
- **Published Postman API Documentation:**  
  👉 [Postman API Documentation](https://documenter.getpostman.com/view/49804126/2sBYHYuJ15)
- **Test Case Scenarios & Test Matrix Document:**  
  👉 [Google Sheets / Drive Test Cases](https://docs.google.com/spreadsheets/d/1BxiMVs0XRA5nFMdKvBdBZjgmUUqptlbs74OgvE2upms/edit?usp=sharing) *(Replace with your Google Sheet link if applicable)*

---

## ⚙️ Business Workflow Tested
1. **User Creation:**
   - Create 2 Customers, 1 Agent, and 1 Merchant using dynamic data (unique phone numbers, emails, and NIDs).
2. **User Activation:**
   - Admin activates all newly created accounts (`Customer-1`, `Customer-2`, `Agent`, `Merchant`).
3. **System Deposit:**
   - System user (`system@dmoney.com`) deposits **5,000 TK** into the Agent account.
4. **Agent Deposit to Customer:**
   - Agent deposits **2,000 TK** to Customer-1.
   - Assert deposit commission is received by Agent.
5. **Send Money (Customer to Customer):**
   - Customer-1 sends **1,000 TK** to Customer-2.
   - Assert service fee deduction (5 TK).
6. **Cashout (Customer to Agent):**
   - Customer-2 cashes out **500 TK** through the Agent.
   - Assert cashout service fee deduction.
7. **Merchant Payment:**
   - Customer-2 pays **400 TK** to Merchant.
8. **Negative Test Cases:**
   - Admin login with wrong password (401 Unauthorized).
   - Create user without NID (400 Bad Request).
   - Deposit negative amount (validation error).
   - Send money exceeding available balance.
   - Payment without bearer token (Unauthorized).

---

## 📁 Repository Structure
```text
├── .gitignore               # Ignores node_modules, Reports, and .env
├── package.json             # NPM dependencies and runner scripts
├── README.md                # Project documentation and links
├── screenshots/
│   └── newman_report_summary.png  # Execution report screenshot
└── collection/
    ├── dmoney_api_collection.json   # Exported Postman collection
    └── dmoney_environment.json      # Postman environment variables
```

---

## 🚀 Prerequisites & Local Setup
1. **Node.js** (v18 or higher recommended)
2. **DMoney Transaction Backend API** running locally on `http://localhost:4000`:
   ```bash
   cd dmoney-transaction-api
   npm install
   npm run dev
   ```

---

## 🧪 How to Run Tests via Newman

### 1. Install Dependencies
```bash
npm install
```

### 2. Run Test Collection via CLI
```bash
npm test
```

### 3. Generate HTML Execution Report
```bash
npm run report
```
*(The generated HTML report will be saved inside the `Reports/` directory, which is ignored by `.gitignore` as per assignment instructions).*

---

## 📊 Test Execution Summary Screenshot
Below is the execution result summary from Postman / Newman:

![Test Execution Summary](./screenshots/newman_report_summary.png)

---

## 🛡️ Git Ignore Verification
As per assignment requirements, the `.gitignore` explicitly excludes:
- `node_modules/`
- `Reports/`
- `.env`
