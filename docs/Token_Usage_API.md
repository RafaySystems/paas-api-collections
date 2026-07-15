# Token Usage API Documentation

## Overview

APIs for retrieving aggregated token usage metrics.

## Authentication

```
X-RAFAY: <API_KEY>
```

---

## Aggregated

**Method:** `POST`  
**Endpoint:** `https://ops-console.gpupaas-qc.dev.rafay-edge.net/api.gaap.k8smgmt.io/v1alpha1/model/usage/aggregated?limit=30`

### Headers

|Header|Value|
|---|---|
|X-RAFAY|<API_KEY>|

### Query Parameters

|Name|Value|
|---|---|
|limit|30|

### Request Body

```json
{"start":1779301800,"end":1779960149}
```

---

## TotalAggregated

**Method:** `POST`  
**Endpoint:** `https://ops-console.gpupaas-qc.dev.rafay-edge.net/api.gaap.k8smgmt.io/v1alpha1/model/usage/totalaggregated?page=0&limit=10`

### Headers

|Header|Value|
|---|---|
|X-RAFAY|<API_KEY>|

### Query Parameters

|Name|Value|
|---|---|
|page|0|
|limit|10|

### Request Body

```json
{"start":1769806600,"end":1779960140}
```

---

