# Customer Management API Documentation

## Overview
**Collection Name:** Customer Management  
**Description:** API endpoints for managing customer organizations in Rafay PaaS.

### 📦 Postman Collection

You can download and import the Postman collection directly:

👉 [Download Customer Management Collection](https://raw.githubusercontent.com/RafaySystems/paas-api-collections/main/Customer%20Management.postman_collection.json)

---

## Authentication

Most endpoints require authentication using the following headers:

```
X-RAFAY-API-KEYID: {{ops-api-key}}
```

---

## Endpoints

**Base URL:** `{{ops-console-domain}}`

### Create Customer
**POST** `/auth/v1/signup/organization/`

Creates a new customer organization.

**Request Body**
```json
{
  "username": "fname.lname@example.com",
  "organization_name": "Example Ltd",
  "first_name": "fname",
  "last_name": "lname",
  "password": "notapassword"
}
```

---

### List / Search Customers
**GET** `/auth/v1/organizations`

Retrieve a list of customer organizations.

**Query Parameters**
| Name | Type | Description |
|----|----|----|
| limit | int | Number of records |
| offset | int | Pagination offset |
| name | string | Filter by name |
| external_id | string | Filter by external ID |

---

### Get Customer Details
**GET** `/auth/v1/organizations/{org-id}`

Fetch details of a specific customer.

---

### Update Customer
**PUT** `/auth/v1/organizations/{org-id}`

Update customer organization details.

**Request Body**
```json
{
  "id": "{org-id}",
  "name": "Example Ltd",
  "active": true,
  "approved": true,
  "type": "free"
}
```

---

## Variables

| Variable | Description |
|--------|-------------|
| ops-console-domain | Rafay console domain |
| ops-api-key | API key ID |
| token | Bearer token |
| org-id | Organization ID |
