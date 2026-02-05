# Rafay PaaS API Documentation

Welcome to the Rafay PaaS API documentation.  
This directory contains Markdown-based API references generated from the official Postman collections.

All documents are intended to be rendered directly on GitHub and kept in sync with the Postman collections.

---

## 📚 API Documentation Index

### 🔐 Customer & Organization Management
- **[Customer Management API](./docs/Customer_Management_API.md)**  
  Create, update, list, and manage customer organizations.

---

### 🧾 SKU & Catalog Management
- **[SKU Management API](./docs/SKU_Management_API.md)**  
  List and retrieve compute and service SKU profiles from the system catalog.

---

### 📊 Usage & Billing Metrics
- **[Usage Metrics API](./docs/Usage_Metrics_API.md)**  
  Query usage and billing metrics for compute and service instances and profiles.

---

### 📣 Events & Auditing
- **[PaaS Events API](./docs/PaaS_Events_API.md)**  
  Fetch PaaS-related lifecycle and operational events for compute and service instances.

---

## 🔑 Authentication

Most APIs require an organization-scoped API key:

```
x-api-key: <ORG_API_KEY>
```

Some APIs may additionally require bearer tokens depending on deployment and configuration.

---

## ⏱ Time Range Parameters

Several APIs accept time-based query parameters:

- `range_from`
- `range_to`

These typically support ISO-8601 timestamps or epoch formats, depending on the endpoint.

---

## 📁 Recommended Folder Structure

```
docs/
├── README.md
├── Customer_Management_API.md
├── SKU_Management_API.md
├── Usage_Metrics_API.md
└── PaaS_Events_API.md
```

---

## 🛠 Source

These documents are generated from Postman collections maintained in:

https://github.com/RafaySystems/paas-api-collections

---

If you find inconsistencies between the APIs and documentation, please update the Postman collection first and regenerate the docs.
