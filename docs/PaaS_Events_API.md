# PaaS Events API Documentation

## Overview
**Collection Name:** PaaS Events  
**Description:** APIs for querying PaaS-related events for compute and service instances.

### 📦 Postman Collection

You can download and import the Postman collection directly:

👉 [Download PaaS Events Collection](https://raw.githubusercontent.com/RafaySystems/paas-api-collections/refs/heads/main/PaaS%20Events.postman_collection.json)

---

## Authentication

All endpoints require the following header:

```
x-api-key: {{default-org-api-key}}
```

---

## Compute Instance Events

**Base URL:** `https://{{console-domain}}`

### Get Compute Instance Events
**GET** `/apis/dashboard.envmgmt.io/v1/events/paas/partner/kind/compute/instance`

Retrieve events related to PaaS compute instances within a given time range.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp (ISO or epoch, as supported) |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| status | Event status filter |
| orderby | Field to sort by (e.g. `created_at`) |
| order | Sort order (`asc` / `desc`) |
| org_id | Filter by organization ID |
| profile_id | Filter by profile ID |

---

## Service Instance Events

### Get Service Instance Events
**GET** `/apis/dashboard.envmgmt.io/v1/events/paas/partner/kind/compute/instance`

Retrieve events related to PaaS service instances within a given time range.

> Note: This endpoint currently uses the same path as compute instance events, as defined in the Postman collection.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| status | Event status filter |
| orderby | Field to sort by |
| order | Sort order |
| org_id | Filter by organization ID |
| profile_id | Filter by profile ID |

---

## Variables

| Variable | Description |
|--------|-------------|
| console-domain | Rafay console domain |
| default-org-api-key | Organization API key |
| start_time | Event query start time |
| end_time | Event query end time |
