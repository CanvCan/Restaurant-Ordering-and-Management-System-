# 🍽️ Restaurant Ordering and Management System

## 📑 Table of Contents

1. [Introduction](#1-introduction)
2. [Identification of Viewpoints](#2-identification-of-viewpoints)
   - [Principal Viewpoints](#-principal-viewpoints)
   - [Viewpoint Hierarchy Diagram](#-viewpoint-hierarchy-diagram)
   - [Description of Each Viewpoint](#-description-of-each-viewpoint)
3. [Requirements Definition and Classification](#3-requirements-definition-and-classification)
4. [Requirements Prioritization and Negotiation](#4-requirements-prioritization-and-negotiation)
5. [Requirements Traceability Matrix](#5-requirements-traceability-matrix)
   - [Use-Case Version](#-use-case-version)
   - [Relation-Design Version](#-relation-design-version)
6. [Use Cases of the Main Scenarios](#6-use-cases-of-the-main-scenarios)
   - [Use Case 1: Place Order](#-use-case-1-place-order)
   - [Use Case 2: Prepare Order](#-use-case-2-prepare-order)
   - [Use Case 3: Process Payment](#-use-case-3-process-payment)
7. [Domain Model as a UML Diagram](#7-domain-model-as-a-uml-diagram)
8. [Conclusion](#8-conclusion)

---

## 1. Introduction

This document outlines the requirements analysis for the development of a **Restaurant Ordering and Management System**. The system aims to:

- Enhance customer experience
- Streamline staff operations
- Enable digital ordering
- Support real-time kitchen display
- Ensure secure and fast payments
- Maintain regulatory compliance

---

## 2. Identification of Viewpoints

### 🔷 Principal Viewpoints

- **Customer Viewpoint**
- **Restaurant Staff Viewpoint**
  - Server/Wait Staff
  - Kitchen Staff
  - Manager
- **Business Operation Viewpoint**
  - Finance
  - HR
  - Marketing
- **External Systems Viewpoint**
  - POS
  - Inventory
  - Payment Gateway
- **Regulatory Compliance Viewpoint**
  - PCI-DSS
  - Data Protection
  - Food Safety


### 🗂️ Viewpoint Hierarchy Diagram

![Viewpoint Hierarchy Diagram](viewpoint_hierarchy_diagram.png)

### 📋 Description of Each Viewpoint

1. **Customer Viewpoint:** Primary receivers of the restaurant ordering service who browse the menu, place orders, and make payments.
2. **Server/Wait Staff Viewpoint:** Both providers and receivers who deliver service to customers and input payment information.
3. **Kitchen Staff Viewpoint:** Providers who prepare food items based on system orders and update order statuses.
4. **Management Viewpoint:** Both providers and receivers who configure the system (menu items, prices) and consume system outputs (reports, analytics).
5. **Payment Processing System Viewpoint:** External system handling credit card and digital payments.
6. **Inventory Management System Viewpoint:** Interacts with the ordering system to track ingredient usage and stock levels.
7. **POS Terminal System Viewpoint:** Hardware that interfaces with the ordering system for payment processing.
8. **Food Safety Regulation Viewpoint:** Requirements for allergen information, ingredient tracking, and food safety compliance.
9. **Payment Security Standards Viewpoint:** PCI-DSS compliance and secure transaction processing requirements.
10. **Data Protection Viewpoint:** Requirements for handling customer data in compliance with privacy regulations.
11. **Marketing Team Viewpoint:** Requirements for promotional features, customer data collection, and campaign management.
12. **Financial Management Viewpoint:** Requirements for accounting integration, revenue tracking, and financial reporting.
13. **Human Resources Viewpoint:** Staff scheduling, role management, and performance tracking.

---

## 3. Requirements Definition and Classification

| ID  | Viewpoint           | Definition of Requirement                                                                 | Functionality    | Lifetime |
| --- | ------------------- | ------------------------------------------------------------------------------------------- | ---------------- | -------- |
| R01 | Customer            | The system shall allow customers to browse a digital menu with accurate pricing, descriptions, and photos of menu items. | Functional       | Enduring |
| R02 | Customer            | The system shall enable customers to place orders without requiring account creation.      | Functional       | Enduring |
| R03 | Customer            | The system shall provide customers with estimated preparation and delivery times for their orders. | Functional       | Enduring |
| R04 | Customer            | The system shall support multiple payment methods including credit cards, digital wallets, and cash. | Functional       | Enduring |
| R05 | Customer            | The system shall allow customers to customize menu items and specify dietary restrictions or allergies. | Functional       | Enduring |
| R06 | Customer            | The system shall support customers to place multiple orders during a meal.                | Functional       | Enduring |
| R07 | Staff-Server        | The system shall allow servers to modify existing orders based on customer requests.       | Functional       | Enduring |
| R08 | Staff-Server        | The system shall enable servers to process payments tableside.                            | Functional       | Enduring |
| R09 | Staff-Kitchen       | The system shall display incoming orders on kitchen displays in order of priority.        | Functional       | Enduring |
| R10 | Staff-Kitchen       | The system shall enable kitchen staff to update order status (received, in preparation, ready). | Functional       | Enduring |
| R11 | Staff-Kitchen       | The system shall alert kitchen staff about special requests or allergen information.       | Functional       | Enduring |
| R12 | Staff-Manager       | The system shall allow managers to add, modify, or remove menu items and their allergen labels in real-time. | Functional       | Enduring |
| R13 | Staff-Manager       | The system shall generate daily, weekly, and monthly sales reports.                       | Functional       | Enduring |
| R14 | Staff-Manager       | The system shall provide analytics on popular items, peak ordering times, and average order values. | Functional       | Enduring |
| R15 | Business-Finance    | The system shall calculate and report tax liabilities accurately.                         | Functional       | Enduring |
| R16 | Business-Marketing  | The system shall support digital promotions including time-limited discounts and loyalty programs.|Functional|Volatile|
| R17 | Business-Marketing  | The system shall collect anonymized customer preference data for marketing analysis.|Functional|Enduring|
| R18 | Business-HR         | The system shall track employee logins and activities for performance evaluation.|Functional|Enduring|
| R19 | Business-HR         | The system shall support role-based permissions aligned with staff responsibilities.|Functional|Enduring|
| R20 | Business-HR         | The system shall assign schedules to employees.|Functional|Enduring|
| R21 | External-Payment    | The system shall securely integrate with payment processors using encrypted API connections.|Functional|Enduring|
| R22 | External-Payment    | The system shall handle payment failures gracefully with clear error messages.|Functional|Enduring|
| R23 | External-Inventory  | The system shall update inventory levels in real-time as orders are processed.|Functional|Enduring|
| R24 | External-Inventory  | The system shall alert management when ingredients reach low stock levels.|Functional|Enduring|
| R25 | External-POS        | The system shall synchronize with POS terminals to ensure consistent pricing across all ordering channels.|Functional|Enduring|
| R26 | External-POS        | The system shall process card transactions within 5 seconds of authorization.|Non- functional|Volatile|
| R27 | Regulatory-Food     | The system shall display allergen information for all menu items.|Functional|Enduring|
| R28 | Regulatory-Food     | The system shall provide allergen information labels when adding new products to menu by managers for food safety.|Functional|Enduring|
| R29 | Regulatory-Payment  | The system shall comply with PCI-DSS requirements for handling payment information.|Domain|Volatile|
| R30 | Regulatory-Payment  | The system shall not store complete credit card numbers in the database.|Domain|Enduring|
| R31 | Regulatory-Data     | The system shall encrypt all personal customer data at rest and in transit.|Non- functional|Enduring|
| R32 | Regulatory-Data     | The system shall implement data retention policies compliant with regional privacy laws.|Domain|Volatile|

---

## 4. Requirements Prioritization and Negotiation

| Priority Level | Description                                  | Requirements                                                         |
| -------------- | -------------------------------------------- | -------------------------------------------------------------------- |
| High           | Critical requirements essential for the system to function | R01, R02, R04, R05, R06, R07, R09, R10, R11, R12, R21, R22, R23, R24, R27, R28, R29, R30 |
| Medium         | Important requirements that should be included if possible | R03, R08, R13, R15, R19, R20, R24, R25, R32                           |
| Low            | Desirable requirements that would enhance the system | R14, R16, R17, R18, R26, R31                                         |

---

## 5. Requirements Traceability Matrix

### 📌 Use-Case Version

# 📋 Detailed Requirement Mapping

| Requirement ID | Requirement Description                                                                                   | Use Case 1: Place Order | Use Case 2: Prepare Order | Use Case 3: Process Payment |
|----------------|------------------------------------------------------------------------------------------------------------|--------------------------|----------------------------|------------------------------|
| R01 | The system shall allow customers to browse a digital menu with accurate pricing, descriptions, and photos of menu items. | ✔                        |                            |                              |
| R02 | The system shall enable customers to place orders without requiring account creation.                                  | ✔                        |                            |                              |
| R03 | The system shall provide customers with estimated preparation and delivery times for their orders.                     | ✔                        | ✔                          |                              |
| R04 | The system shall support multiple payment methods including credit cards, digital wallets, and cash.                   |                          |                            | ✔                            |
| R05 | The system shall allow customers to customize menu items and specify dietary restrictions or allergies.                | ✔                        | ✔                          |                              |
| R06 | The system shall support customers to place multiple orders during a meal.                                             | ✔                        |                            |                              |
| R07 | The system shall allow servers to modify existing orders based on customer requests.                                   | ✔                        | ✔                          |                              |
| R08 | The system shall enable servers to process payments tableside.                                                         |                          |                            | ✔                            |
| R09 | The system shall display incoming orders on kitchen displays in order of priority.                                     |                          | ✔                          |                              |
| R10 | The system shall enable kitchen staff to update order status (received, in preparation, ready).                        |                          | ✔                          |                              |
| R11 | The system shall alert kitchen staff about special requests or allergen information.                                   | ✔                        | ✔                          |                              |
| R12 | The system shall allow managers to add, modify, or remove menu items and their allergen labels in real-time.           |                          | ✔                          |                              |
| R13 | The system shall generate daily, weekly, and monthly sales reports.                                                    |                          |                            | ✔                            |
| R14 | The system shall provide analytics on popular items, peak ordering times, and average order values.                    |                          | ✔                          | ✔                            |
| R15 | The system shall calculate and report tax liabilities accurately.                                                      |                          |                            | ✔                            |
| R16 | The system shall support digital promotions including time-limited discounts and loyalty programs.                     | ✔                        |                            | ✔                            |
| R17 | The system shall collect anonymized customer preference data for marketing analysis.                                   | ✔                        |                            |                              |
| R18 | The system shall track employee logins and activities for performance evaluation.                                      |                          | ✔                          |                              |
| R19 | The system shall support role-based permissions aligned with staff responsibilities.                                   |                          | ✔                          | ✔                            |
| R20 | The system shall assign schedules to employees.                                                                        |                          | ✔                          |                              |
| R21 | The system shall securely integrate with payment processors using encrypted API connections.                           |                          |                            | ✔                            |
| R22 | The system shall handle payment failures gracefully with clear error messages.                                         |                          |                            | ✔                            |
| R23 | The system shall update inventory levels in real-time as orders are processed.                                         | ✔                        | ✔                          |                              |
| R24 | The system shall alert management when ingredients reach low stock levels.                                             |                          | ✔                          |                              |
| R25 | The system shall synchronize with POS terminals to ensure consistent pricing across all ordering channels.             |                          |                            | ✔                            |
| R26 | The system shall process card transactions within 5 seconds of authorization.                                          |                          |                            | ✔                            |
| R27 | The system shall display allergen information for all menu items.                                                      | ✔                        |                            |                              |
| R28 | The system shall provide allergen information labels when adding new products to menu by managers for food safety.     |                          | ✔                          |                              |
| R29 | The system shall comply with PCI-DSS requirements for handling payment information.                                    |                          |                            | ✔                            |
| R30 | The system shall not store complete credit card numbers in the database.                                               |                          |                            | ✔                            |
| R31 | The system shall encrypt all personal customer data at rest and in transit.                                            | ✔                        |                            | ✔                            |
| R32 | The system shall implement data retention policies compliant with regional privacy laws.                               | ✔                        |                            | ✔                            |

---

### 📌 Relation-Design Version

|Req ID|R01|R02|R03|R04|R05|R06|R07|R08|R09|R10|R11|R12|R13|R14|R15|R16|R17|R18|R19|R20|R21|R22|R23|R24|R25|R26|R27|R28|R29|R30|R31|R32|
| - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - | - |
|R01|||||R|||||||R|||||||||||||R||R||||||
|R02||||R|||||||||||||||||||||||||||||
|R03|||||||||D|D|||||||||||||||||||||||
|R04|||||||||||||||||||||R|R|||||||D|D|||
|R05|||||||||||R||||||||||||||||R|R|||||
|R06||D|||||R||||||||||||||||||||||||||
|R07|||||||||||||||||||D||||||||||||||
|R08||||R|||||||||||||||D||D|D||||D|||D|D|||
|R09|||||||||||||||||||||||||||||||||
|R10|||R||||||||||||||||||||||||||||||
|R11|||||R||||||||||||||||||||||D|D|||||
|R12|||||||||||||||||||D||||||||D|R|||||
|R13||||||||||||||R|D||||||||||D||||||||
|R14|||||||||||||D||||D||||||||||||||||
|R15|||||||||||||D||||||||||||D||||||||
|R16|||||||||||||||||||||||||||||||||
|R17||||||||||||||D|||||||||||||||||D|D|
|R18|||||||||||||||||||D||||||||||||||
|R19|||||||R|||||R||||||R||R|||||||||||||
|R20|||||||||||||||||||D||||||||||||||
|R21||||R||||D|||||||||||||||||||||D|D|D||
|R22||||D||||D|||||||||||||R||||||||||||
|R23|||||||||||||||||||||||||||||||||
|R24|||||||||||||||||||||||R||||||||||
|R25|||||||||||||||||||||||||||||||||
|R26||||||||D|||||||||||||D||||||||||||
|R27|||||R||||||R|D||||||||||||||||D|||||
|R28||||||||||||D|||||||||||||||R||||||
|R29||||D||||D|||||||||||||R||||||||||||
|R30||||D||||D|||||||||||||R||||||||R||||
|R31|||||||||||||||||D|||||||||||||||D|
|R32|||||||||||||||||D||||||||||||||R||

---

## 6. Use Cases of the Main Scenarios



### ✅ Use Case 1: Place Order

**Actors**  
- **Primary:** Customer  
- **Secondary:** Wait Staff, Kitchen Staff  

**Inputs**  
- Menu selections  
- Customization options  
- Table number (for dine-in)  
- Contact info (for delivery/takeout)  
- Special instructions  
- Dietary restrictions / Allergen info  

**Actions**  
1. Customer browses the digital menu  
2. Selects items and applies customizations  
3. Reviews order summary  
4. Submits the order  
5. System validates and checks inventory  
6. Calculates total with tax  
7. Assigns to kitchen station(s)  
8. Estimates preparation time  
9. Confirms order to the customer  

**Outputs**  
- Order confirmation (with unique ID)  
- Estimated prep/delivery time  
- Itemized receipt  
- Kitchen order ticket  
- Inventory update trigger  

**Exceptions**  
- ❌ Item unavailable → Suggests alternatives  
- ❌ Invalid input → Highlights issues  
- ❌ System failure → Enables offline ordering  
- ❌ Incompatible customizations → Alerts user  
- ❌ Dietary request unfulfillable → Notifies customer  

---

### 🔧 Use Case 2: Prepare Order

**Actors**  
- **Primary:** Kitchen Staff  
- **Secondary:** Wait Staff, Manager  

**Inputs**  
- Order details  
- Priority level  
- Allergen/special instructions  
- Preparation requirements  

**Actions**  
1. System displays new orders  
2. Staff acknowledges receipt  
3. Orders sorted by priority/time  
4. Preparation begins  
5. Status updates as items are prepped  
6. Time tracked vs. estimate  
7. Items marked as complete  
8. Server notified for delivery  

**Outputs**  
- Real-time order status  
- Server notifications  
- Kitchen performance metrics  
- Inventory consumption logs  
- QC completion records  

**Exceptions**  
- ❌ Ingredient shortage → Notify manager/customer  
- ❌ Equipment issue → Reroute to another station  
- ❌ Prep delay → Update estimated time  
- ❌ QC failure → Item flagged for remake  
- ❌ Ambiguous instructions → Request clarification  

---

### 💳 Use Case 3: Process Payment

**Actors**  
- **Primary:** Customer  
- **Secondary:** Wait Staff, Manager  

**Inputs**  
- Order total  
- Payment method  
- Payment credentials  
- Discount codes / Loyalty info  
- Optional tip  

**Actions**  
1. System shows itemized bill  
2. Customer chooses payment method  
3. System applies discounts  
4. Payment info securely submitted  
5. Transaction processed and confirmed  
6. Receipt generated  
7. Order status updated to "Paid"  
8. Transaction logged  

**Outputs**  
- Payment confirmation  
- Digital or printed receipt  
- Updated order/payment status  
- Loyalty program update  

**Exceptions**  
- ❌ Declined payment → Request alternative  
- ❌ Network issue → Offer offline method  
- ❌ Invalid discount → Notify and remove  
- ❌ Unsupported method → Suggest alternatives  
- ❌ Timeout → Retry or suggest new method  

---

## 7. Domain Model as a UML Diagram

![Domain Model UML](domain_model.png)

---

## 8. Conclusion

The **Restaurant Ordering and Management System** is designed to streamline restaurant operations, focusing on table management, online ordering, kitchen order display, and payment processing. The system allows for efficient menu management, enabling administrators to easily update items. Customers can place orders directly from their table, with the kitchen receiving real-time updates. Staff can track orders, manage payments, and handle inventory seamlessly. This solution improves efficiency, reduces errors, and enhances the overall dining experience, ensuring smoother operations for both customers and staff.

---
