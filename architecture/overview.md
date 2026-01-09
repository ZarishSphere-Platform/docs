# Zarish Sphere Platform Architecture Overview

## Introduction

The **Zarish Sphere Platform** is a modular, enterprise-grade distributed system designed for humanitarian and development organizations. It provides a unified digital ecosystem that integrates administrative (ERP) and clinical (HIS/EMR/EHR) operations.

## Core Architecture

The platform follows a **Microservices Architecture** with a focus on interoperability through the **HL7 FHIR** standard.

### 1. API Gateway (Zarish Connect)
- **Role:** Central entry point for all external and internal requests.
- **Functionality:** Reverse proxy, routing, and load balancing.

### 2. Identity & Access Management (Zarish Access)
- **Role:** Centralized OAuth2 and OpenID Connect provider.
- **Functionality:** User authentication, role-based access control (RBAC), and session management.

### 3. Clinical Core (Zarish Sphere & FHIR Server)
- **Role:** Management of clinical data.
- **Functionality:** Patient records, practitioner management, and organization structures following FHIR profiles.

### 4. Specialized Modules
- **Zarish HIS:** Hospital Information System for clinical workflows.
- **Zarish HRA:** Human Resources and Administration.
- **Zarish FIN:** Financial management and accounting.
- **Zarish LOG:** Logistics and supply chain management.
- **Zarish GEO:** Geographic data and mapping.

## Data Flow

1. **Client Request:** Mobile or Web apps send requests to `Zarish Connect`.
2. **Authentication:** `Zarish Connect` validates tokens with `Zarish Access`.
3. **Routing:** Requests are routed to the appropriate microservice.
4. **Persistence:** Services interact with their respective databases (PostgreSQL/Redis) or the central FHIR data store.

## Technology Stack

| Layer | Technology |
| :--- | :--- |
| **Backend** | Go (Golang) |
| **Frontend** | React, TypeScript, TailwindCSS |
| **Database** | PostgreSQL, Redis |
| **Interoperability** | HL7 FHIR |
| **Infrastructure** | Docker, Kubernetes |
