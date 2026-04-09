# Customer Workflow APIs Documentation

## 📦 Postman Collection

👉 [Download Postman Collection (JSON)](https://raw.githubusercontent.com/RafaySystems/paas-api-collections/refs/heads/main/Customer%20Workflow%20APIs.postman_collection.json)

---

## Overview

This document describes the APIs available in the Customer Workflow Postman collection.

---

## Project Management

### Create Project

**Method:** `POST`  
**Endpoint:** `https://{{console-domain}}/auth/v1/projects/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

**Request Body:**

```json
{"name":"{{project-name}}","description":""}
```

---

### List or Search Projects

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/auth/v1/projects/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Delete Project

**Method:** `DELETE`  
**Endpoint:** `https://{{console-domain}}/auth/v1/projects/{{project-id}}/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Create Workspace

**Method:** `POST`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/workspaces?fail-on-exists=true`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

**Request Body:**

```json
{
    "apiVersion": "paas.envmgmt.io/v1",
    "kind": "Workspace",
    "metadata": {
        "name": "delete",
        "project": "{{project-name}}"
    }
}
```

---

### Get Workspaces

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/workspaces?limit=3&offset=0&order=DESC&orderBy=createdAt`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Delete Workspace

**Method:** `DELETE`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/workspaces/{{workspace-name}}`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

## Instance Management

### List Compute Profiles

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/computeprofiles`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Get Compute Profile

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/computeprofiles/{{profile-name}}?systemCatalog=true`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Create Instance

**Method:** `POST`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/workspaces/{{workspace-name}}/computeinstances?fail-on-exists=true&auto-publish=true`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key |  |

**Request Body:**

```json
{
    "apiVersion": "paas.envmgmt.io/v1",
    "kind": "ComputeInstance",
    "metadata": {
        "workspace": "default-ws",
        "project": "development",
        "labels": {
            "External-ID": "6c9da2c6-adb1-4a1b-90b3-2fde7d5632aa"
        },
        "name": "dev-vm-2"
    },
    "spec": {
        "computeProfile": {
            "name": "small-gpu-vm",
            "systemCatalog": true
        },
        "variables": [
            {
                "name": "cpu",
                "valueType": "text",
                "value": "24",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "CPU",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "3"
                    }
                }
            },
            {
                "name": "disk",
                "valueType": "text",
                "value": "150",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "Disk",
                        "incrementDecrementLabel": "Disk Size (GB)",
                        "incrementDecrementMax": "2000",
                        "incrementDecrementMin": "100",
                        "incrementDecrementStep": "50",
                        "section": "VM Specification",
                        "type": "incrementDecrement",
                        "weight": "5"
                    }
                }
            },
            {
                "name": "gpu",
                "valueType": "text",
                "value": "1",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "radioOptions": [
                            {
                                "description": "",
                                "label": "1",
                                "value": "1"
                            }
                        ],
                        "section": "VM Specification",
                        "type": "text",
                        "weight": "2"
                    }
                }
            },
            {
                "name": "gpu-model",
                "valueType": "text",
                "value": "H100",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU Type",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "dropdownValues": [
                            {
                                "label": "H100",
                                "text": "",
                                "value": "H100"
                            }
                        ],
                        "radioOptions": [
                            {
                                "description": "",
                                "label": "H100",
                                "value": "H100"
                            }
                        ],
                        "section": "VM Specification",
                        "type": "radio",
                        "weight": "1"
                    }
                }
            },
            {
                "name": "memory",
                "valueType": "text",
                "value": "256",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "Memory",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "4"
                    }
                }
            },
            {
                "name": "password",
                "valueType": "text",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "VM Password",
                        "extraDescription": "VM Username: ubuntu",
                        "section": "VM Access",
                        "type": "text",
                        "weight": "6"
                    }
                },
                "value": "changeplz"
            },
            {
                "name": "ssh-key",
                "valueType": "text",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "SSH Public Key",
                        "section": "VM Access",
                        "weight": "6"
                    }
                },
                "value": ""
            },
            {
                "name": "video-memory",
                "valueType": "text",
                "value": "80",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU Memory",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "2.5"
                    }
                }
            }
        ],
        "computeType": "vm",
        "datacenter": {},
        "storageDetails": {}
    }
}
```

**Description:**

# Create Compute Instance

## Overview

This endpoint creates a new compute instance (virtual machine) within a specified workspace and project. The API provisions a VM with customizable specifications including CPU, GPU, memory, and storage configurations based on a compute profile template.

## Endpoint Details

- **Method**: POST
    
- **Path**: `/apis/paas.envmgmt.io/v1/projects/{project-name}/workspaces/{workspace-name}/computeinstances`
    

## Query Parameters

### `fail-on-exists`

- **Type**: Boolean
    
- **Default**: `true`
    
- **Description**: Controls the behavior when a compute instance with the same name already exists:
    
    - `true`: The API will fail and return an error if an instance with the specified name already exists
        
    - `false`: The API will allow duplicate names or handle existing instances gracefully
        

## Request Body Structure

### 1\. Metadata Section

Defines the organizational and identification details for the compute instance:

- **`workspace`**: The workspace where the instance will be created (e.g., `default-ws`)
    
- **`project`**: The project context for the instance (e.g., `development`)
    
- **`name`**: Unique identifier for the compute instance (e.g., `dev-vm-1`)
    
- **`labels`**: Same as profile.metadata.labels
    

### 2\. Spec Section

Contains the technical specifications and configuration for the compute instance:

#### **Compute Profile**

- **`name`**: Reference to a predefined compute profile template (e.g., `small-gpu-vm`)
    
- **`systemCatalog`**: Boolean indicating if the profile is from the system catalog (`true`) or custom
    

#### **Compute Type**

- **`computeType`**: Type of compute resource, set to `vm` for virtual machines
    

#### **Variables Array (Copied from** Profile.spec.variables**)**

Defines the configurable parameters for the VM. This section is copied from profile.spec.variables and updated with any overrides from user. Each variable includes:

- `name`: Variable identifier
    
- `valueType`: Data type (typically `text`)
    
- `value`: The configured value
    
- `options`: Metadata for UI display and validation
    

### 3\. VM Specifications (Variables)

#### **CPU Configuration**

- **Variable**: `cpu`
    
- **Value**: Number of CPU cores (e.g., `24`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled (cannot be modified after creation)
    

#### **GPU Configuration**

- **Variable**: `gpu`
    
- **Value**: Number of GPU units (e.g., `1`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled
    
- **Variable**: `gpu-model`
    
- **Value**: GPU model type (e.g., `H100`)
    
- **Options**: Dropdown/radio selection from available GPU types
    
- **Day 2 Operations**: Disabled
    
- **Variable**: `video-memory`
    
- **Value**: GPU memory in GB (e.g., `80`)
    
- **Day 2 Operations**: Disabled
    

#### **Memory Configuration**

- **Variable**: `memory`
    
- **Value**: RAM in GB (e.g., `256`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled
    

#### **Disk Configuration**

- **Variable**: `disk`
    
- **Value**: Disk size in GB (e.g., `150`)
    
- **Override**: Allowed
    
- **UI Control**: Increment/decrement slider
    
    - Min: 100 GB
        
    - Max: 2000 GB
        
    - Step: 50 GB
        

### 4\. VM Access Credentials

#### **Password Authentication**

- **Variable**: `password`
    
- **Description**: Password for VM access
    
- **Default Username**: `ubuntu`
    
- **Example**: `changeplz` (should be changed to a secure password)
    
- **Override**: Allowed
    

#### **SSH Key Authentication**

- **Variable**: `ssh-key`
    
- **Description**: SSH public key for secure key-based authentication
    
- **Value**: Paste your SSH public key content
    
- **Override**: Allowed
    
- **Note**: Recommended for production environments
    

## Example Use Case

This request creates a development VM (`dev-vm-1`) with:

- 24 CPU cores
    
- 1x NVIDIA H100 GPU with 80GB memory
    
- 256 GB RAM
    
- 150 GB disk storage
    
- Ubuntu OS with password and/or SSH key access
    

## Best Practices

1. **Security**: Always use strong passwords and prefer SSH key authentication for production VMs
    
2. **Naming**: Use descriptive names that indicate the environment and purpose (e.g., `dev-vm-1`, `prod-ml-gpu-01`)
    
3. **External IDs**: Maintain consistent External-ID labels for tracking across systems
    
4. **Resource Sizing**: Choose appropriate compute profiles and adjust variables based on workload requirements

---

### List Instances

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/workspaces/{{workspace-name}}/computeinstances`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

**Request Body:**

```json
{
    "apiVersion": "paas.envmgmt.io/v1",
    "kind": "ComputeInstance",
    "metadata": {
        "workspace": "default-ws",
        "project": "development",
        "labels": {
            "External-ID": "6c9da2c6-adb1-4a1b-90b3-2fde7d5632aa"
        },
        "name": "dev-vm-1"
    },
    "spec": {
        "computeProfile": {
            "name": "small-gpu-vm",
            "systemCatalog": true
        },
        "variables": [
            {
                "name": "cpu",
                "valueType": "text",
                "value": "24",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "CPU",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "3"
                    }
                }
            },
            {
                "name": "disk",
                "valueType": "text",
                "value": "150",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "Disk",
                        "incrementDecrementLabel": "Disk Size (GB)",
                        "incrementDecrementMax": "2000",
                        "incrementDecrementMin": "100",
                        "incrementDecrementStep": "50",
                        "section": "VM Specification",
                        "type": "incrementDecrement",
                        "weight": "5"
                    }
                }
            },
            {
                "name": "gpu",
                "valueType": "text",
                "value": "1",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "radioOptions": [
                            {
                                "description": "",
                                "label": "1",
                                "value": "1"
                            }
                        ],
                        "section": "VM Specification",
                        "type": "text",
                        "weight": "2"
                    }
                }
            },
            {
                "name": "gpu-model",
                "valueType": "text",
                "value": "H100",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU Type",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "dropdownValues": [
                            {
                                "label": "H100",
                                "text": "",
                                "value": "H100"
                            }
                        ],
                        "radioOptions": [
                            {
                                "description": "",
                                "label": "H100",
                                "value": "H100"
                            }
                        ],
                        "section": "VM Specification",
                        "type": "radio",
                        "weight": "1"
                    }
                }
            },
            {
                "name": "memory",
                "valueType": "text",
                "value": "256",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "Memory",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "4"
                    }
                }
            },
            {
                "name": "password",
                "valueType": "text",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "VM Password",
                        "extraDescription": "VM Username: ubuntu",
                        "section": "VM Access",
                        "type": "text",
                        "weight": "6"
                    }
                },
                "value": "changeplz"
            },
            {
                "name": "ssh-key",
                "valueType": "text",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "SSH Public Key",
                        "section": "VM Access",
                        "weight": "6"
                    }
                },
                "value": ""
            },
            {
                "name": "video-memory",
                "valueType": "text",
                "value": "80",
                "options": {
                    "override": {
                        "type": "allowed"
                    },
                    "displayMetadata": {
                        "alias": "GPU Memory",
                        "disableForDay2Operation": false,
                        "disabled": true,
                        "section": "VM Specification",
                        "weight": "2.5"
                    }
                }
            }
        ],
        "computeType": "vm",
        "datacenter": {},
        "storageDetails": {}
    }
}
```

**Description:**

# Create Compute Instance

## Overview

This endpoint creates a new compute instance (virtual machine) within a specified workspace and project. The API provisions a VM with customizable specifications including CPU, GPU, memory, and storage configurations based on a compute profile template.

## Endpoint Details

- **Method**: POST
    
- **Path**: `/apis/paas.envmgmt.io/v1/projects/{project-name}/workspaces/{workspace-name}/computeinstances`
    

## Query Parameters

### `fail-on-exists`

- **Type**: Boolean
    
- **Default**: `true`
    
- **Description**: Controls the behavior when a compute instance with the same name already exists:
    
    - `true`: The API will fail and return an error if an instance with the specified name already exists
        
    - `false`: The API will allow duplicate names or handle existing instances gracefully
        

## Request Body Structure

### 1\. Metadata Section

Defines the organizational and identification details for the compute instance:

- **`workspace`**: The workspace where the instance will be created (e.g., `default-ws`)
    
- **`project`**: The project context for the instance (e.g., `development`)
    
- **`name`**: Unique identifier for the compute instance (e.g., `dev-vm-1`)
    
- **`labels`**: Same as profile.metadata.labels
    

### 2\. Spec Section

Contains the technical specifications and configuration for the compute instance:

#### **Compute Profile**

- **`name`**: Reference to a predefined compute profile template (e.g., `small-gpu-vm`)
    
- **`systemCatalog`**: Boolean indicating if the profile is from the system catalog (`true`) or custom
    

#### **Compute Type**

- **`computeType`**: Type of compute resource, set to `vm` for virtual machines
    

#### **Variables Array (Copied from** Profile.spec.variables**)**

Defines the configurable parameters for the VM. This section is copied from profile.spec.variables and updated with any overrides from user. Each variable includes:

- `name`: Variable identifier
    
- `valueType`: Data type (typically `text`)
    
- `value`: The configured value
    
- `options`: Metadata for UI display and validation
    

### 3\. VM Specifications (Variables)

#### **CPU Configuration**

- **Variable**: `cpu`
    
- **Value**: Number of CPU cores (e.g., `24`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled (cannot be modified after creation)
    

#### **GPU Configuration**

- **Variable**: `gpu`
    
- **Value**: Number of GPU units (e.g., `1`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled
    
- **Variable**: `gpu-model`
    
- **Value**: GPU model type (e.g., `H100`)
    
- **Options**: Dropdown/radio selection from available GPU types
    
- **Day 2 Operations**: Disabled
    
- **Variable**: `video-memory`
    
- **Value**: GPU memory in GB (e.g., `80`)
    
- **Day 2 Operations**: Disabled
    

#### **Memory Configuration**

- **Variable**: `memory`
    
- **Value**: RAM in GB (e.g., `256`)
    
- **Override**: Allowed
    
- **Day 2 Operations**: Disabled
    

#### **Disk Configuration**

- **Variable**: `disk`
    
- **Value**: Disk size in GB (e.g., `150`)
    
- **Override**: Allowed
    
- **UI Control**: Increment/decrement slider
    
    - Min: 100 GB
        
    - Max: 2000 GB
        
    - Step: 50 GB
        

### 4\. VM Access Credentials

#### **Password Authentication**

- **Variable**: `password`
    
- **Description**: Password for VM access
    
- **Default Username**: `ubuntu`
    
- **Example**: `changeplz` (should be changed to a secure password)
    
- **Override**: Allowed
    

#### **SSH Key Authentication**

- **Variable**: `ssh-key`
    
- **Description**: SSH public key for secure key-based authentication
    
- **Value**: Paste your SSH public key content
    
- **Override**: Allowed
    
- **Note**: Recommended for production environments
    

## Example Use Case

This request creates a development VM (`dev-vm-1`) with:

- 24 CPU cores
    
- 1x NVIDIA H100 GPU with 80GB memory
    
- 256 GB RAM
    
- 150 GB disk storage
    
- Ubuntu OS with password and/or SSH key access
    

## Best Practices

1. **Security**: Always use strong passwords and prefer SSH key authentication for production VMs
    
2. **Naming**: Use descriptive names that indicate the environment and purpose (e.g., `dev-vm-1`, `prod-ml-gpu-01`)
    
3. **External IDs**: Maintain consistent External-ID labels for tracking across systems
    
4. **Resource Sizing**: Choose appropriate compute profiles and adjust variables based on workload requirements

---

### List Service Profiles

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/serviceprofiles`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

### Get Service Profile

**Method:** `GET`  
**Endpoint:** `https://{{console-domain}}/apis/paas.envmgmt.io/v1/projects/{{project-name}}/serviceprofiles/{{profile-name}}?systemCatalog=true`

**Headers:**

| Key | Value |
|-----|-------|
| x-api-key | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

---

## User Management

### Get Users and Roles

**Method:** `GET`  
**Endpoint:** `https://{{ops-console-domain}}/auth/v1/organizations/{{org-id}}/accountroles/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |

---

### Create User

**Method:** `POST`  
**Endpoint:** `https://{{ops-console-domain}}/auth/v1/organizations/{{org-id}}/adduser/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

**Request Body:**

```json
{
    "account": {
        "username": "tempuser3@yopmail.com",
        "first_name": "temp",
        "last_name": "user3",
        "phone": ""
    },
    "role": {
        "id": "7w2lnkp",
        "name": "ADMIN",
        "is_global": true,
        "scope": "ORGANIZATION"
    },
    "roles": [
        {
            "role": {
                "id": "7w2lnkp",
                "name": "ADMIN",
                "is_global": true,
                "scope": "ORGANIZATION"
            }
        }
    ]
}
```

---

### Create API Key

**Method:** `POST`  
**Endpoint:** `https://{{console-domain}}/auth/v1/users/{{user-id}}/apikey/`

**Headers:**

| Key | Value |
|-----|-------|
| X-RAFAY-API-KEYID | {{ops-console-api-key}} |
| X-ORGANIZATION-ID | {{org-id}} |

**Request Body:**

```json
{
    "name": "dynamic",
    "never_expire": true,
    "validity_hour": 0
}
```

---

## Variables

| Variable | Default Value |
|----------|--------------|
| profile-name |  |

---

## Source

Generated from Postman collection file.
