# Usage Metrics API Documentation

## Overview
**Collection Name:** Usage Metrics  
**Description:** APIs for querying usage and billing metrics for compute and service instances and profiles.

**Base URL:** `https://{{console-domain}}`

---

## Authentication

All endpoints require the following header:

```
x-api-key: {{default-org-api-key}}
```

---

## Instance Usage Metrics

### Compute Instance Usage
**GET** `/apis/billing.envmgmt.io/v1/metrics/partner/instance/kind/compute/usage`

Retrieve usage metrics for compute instances within a given time range.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| instance_organization_id | Filter by organization ID |

---

### Service Instance Usage
**GET** `/apis/billing.envmgmt.io/v1/metrics/partner/instance/kind/service/usage`

Retrieve usage metrics for service instances within a given time range.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| instance_organization_id | Filter by organization ID |

---

## Profile Usage Metrics

### Compute Profile Usage
**GET** `/apis/billing.envmgmt.io/v1/metrics/partner/profile/kind/compute/usage`

Retrieve aggregated usage metrics grouped by compute profiles.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| offset | Pagination offset |
| instance_organization_id | Filter by organization ID |

---

### Service Profile Usage
**GET** `/apis/billing.envmgmt.io/v1/metrics/partner/profile/kind/compute/usage`

Retrieve aggregated usage metrics grouped by service profiles.

> Note: As defined in the Postman collection, this endpoint currently shares the same path as compute profile usage.

**Required Query Parameters**

| Name | Type | Description |
|----|----|----|
| range_from | string | Start timestamp |
| range_to | string | End timestamp |

**Optional Query Parameters**

| Name | Description |
|----|----|
| limit | Max number of records |
| offset | Pagination offset |
| instance_organization_id | Filter by organization ID |

---

## Variables

| Variable | Description |
|--------|-------------|
| console-domain | Rafay console domain |
| default-org-api-key | Organization API key |
| start_time | Metrics query start time |
| end_time | Metrics query end time |
| org-id | Organization ID |
