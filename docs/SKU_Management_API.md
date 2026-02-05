# SKU Management API Documentation

## Overview
**Collection Name:** SKU Management  
**Description:** APIs for listing and retrieving system catalog compute and service SKU profiles.

**Base URL:** `https://{{console-domain}}`

---

## Authentication

All endpoints require the following header:

```
x-api-key: {{default-org-api-key}}
```

---

## Compute Profiles

### List Compute Profiles
**GET** `/apis/paas.envmgmt.io/v1/projects/system-catalog/computeprofiles`

Returns all available compute profiles from the system catalog.

**Query Parameters (optional)**

| Name | Type | Description |
|----|----|----|
| limit | int | Number of results |
| offset | int | Pagination offset |

---

### Get Compute Profile
**GET** `/apis/paas.envmgmt.io/v1/projects/system-catalog/computeprofiles/{profile-name}`

Returns details of a specific compute profile.

**Path Parameters**

| Name | Description |
|----|----|
| profile-name | Name of the compute profile |

---

## Service Profiles

### List Service Profiles
**GET** `/apis/paas.envmgmt.io/v1/projects/system-catalog/serviceprofiles`

Returns all available service profiles.

**Query Parameters (optional)**

| Name | Type | Description |
|----|----|----|
| limit | int | Number of results |
| offset | int | Pagination offset |

---

### Get Service Profile
**GET** `/apis/paas.envmgmt.io/v1/projects/system-catalog/serviceprofiles/{profile-name}`

Returns details of a specific service profile.

**Path Parameters**

| Name | Description |
|----|----|
| profile-name | Name of the service profile |

---

## Variables

| Variable | Description |
|--------|-------------|
| console-domain | Rafay console domain |
| default-org-api-key | Organization API key |
| profile-name | SKU profile name |
