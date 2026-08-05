# Atlas Architecture

**Version:** 0.1.0

**Status:** Draft

**Owner:** Atlas Labs

---

# Overview

Atlas is built as a cloud-native, AI-first platform designed to provide intelligent decision support for electric vehicle drivers.

The architecture is modular, scalable and designed to support future expansion beyond the MVP.

---

# High-Level Architecture

```
                    +----------------------+
                    |   Atlas Mobile App   |
                    |     Flutter App      |
                    +----------+-----------+
                               |
                               |
                 HTTPS / REST API / WebSocket
                               |
                    +----------v-----------+
                    |    Atlas Backend     |
                    |      Supabase        |
                    +----------+-----------+
                               |
        +----------------------+----------------------+
        |                      |                      |
        |                      |                      |
+-------v------+      +--------v--------+    +--------v--------+
| PostgreSQL   |      | Authentication |    | Object Storage  |
| Database     |      | Supabase Auth  |    | Images / Assets |
+--------------+      +----------------+    +-----------------+
                               |
                               |
                     +---------v----------+
                     | Atlas Intelligence |
                     +---------+----------+
                               |
         +----------+----------+-----------+-----------+
         |          |          |           |           |
         |          |          |           |           |
   EV Library   EV DNA   Decision Engine   AI Copilot Weather Engine
```

---

# Architecture Principles

Atlas follows these principles.

- Clean Architecture
- Feature First Development
- API First
- Offline First
- Cloud Native
- AI Ready
- Testable
- Scalable

---

# Mobile Architecture

Framework

Flutter

Language

Dart

Architecture

Clean Architecture

State Management

Riverpod

Routing

GoRouter

Dependency Injection

Riverpod Providers

Networking

Dio

Serialization

Freezed + Json Serializable

Local Storage

Hive

Secure Storage

Flutter Secure Storage

Maps

Google Maps Flutter

Push Notifications

Firebase Cloud Messaging

---

# Folder Structure

```
lib/

core/

config/

constants/

theme/

utils/

services/

shared/

features/

authentication/

garage/

home/

trip_planner/

charging/

ai/

profile/

widgets/

main.dart
```

Each feature is isolated and contains its own presentation, domain and data layers.

---

# Clean Architecture

Each feature follows this structure.

```
feature/

presentation/

widgets/

pages/

providers/

domain/

entities/

repositories/

usecases/

data/

datasources/

models/

repository_impl/
```

Business logic never depends on UI.

---

# Backend

Backend Platform

Supabase

Responsibilities

Authentication

Database

Storage

Realtime

Edge Functions

API Gateway

Future integrations

---

# Database

Database Engine

PostgreSQL

Main Modules

Users

Vehicles

Vehicle Models

Trips

Charging Stations

Charging Sessions

Weather Cache

AI History

Notifications

---

# Authentication

Supported methods

Email

Google

Apple

Future

Togg Account

Tesla Account

Fleet Login

---

# Atlas Intelligence

Atlas Intelligence is separated from the application.

It contains four independent modules.

---

## EV Library

Responsible for vehicle specifications.

Stores

Battery capacity

Usable battery

Charging power

Charging curve

Consumption

Weight

Efficiency

Vehicle dimensions

Range

Software generation

---

## EV DNA

Personal driving profile.

Learns

Average speed

Driving style

Climate usage

Battery habits

Charging habits

Favorite stations

Real consumption

---

## Decision Engine

Core business engine.

Inputs

Battery level

Weather

Traffic

Elevation

Vehicle

Charging stations

Driver profile

Outputs

Recommended route

Recommended charger

Arrival battery

Charging duration

Confidence score

---

## AI Copilot

Natural language interface.

Converts technical information into human language.

Example

"Can I reach Ankara today?"

AI uses Decision Engine output.

AI never estimates directly.

---

# External Services

Google Maps Platform

Weather API

Charging Network APIs

Firebase

OpenAI

Future

Vehicle APIs

Insurance APIs

Energy APIs

---

# API Design

REST API

JSON

Versioned

/api/v1/

Example

GET

/vehicles

POST

/trips

GET

/charging-stations

POST

/ai/chat

---

# Security

JWT Authentication

HTTPS Only

Encrypted Secrets

Secure Storage

Role Based Access

Rate Limiting

Audit Logs

---

# Offline Strategy

Atlas should continue operating when internet is unavailable.

Cached

Vehicle Data

Trip History

Garage

Favorites

Recently Used Charging Stations

Synchronization occurs automatically.

---

# Error Handling

Every API returns

Status

Message

Error Code

Request ID

All exceptions are logged.

---

# Scalability

Current Target

10,000 Users

Future Target

1,000,000 Users

Horizontal scaling is supported.

Stateless backend.

---

# CI/CD

GitHub

↓

GitHub Actions

↓

Build

↓

Tests

↓

Android

↓

iOS

↓

Deployment

---

# Monitoring

Supabase Logs

Crashlytics

Performance Monitoring

Analytics

Future

Grafana

Prometheus

---

# Testing Strategy

Unit Tests

Widget Tests

Integration Tests

Golden Tests

Manual Beta Testing

---

# Coding Standards

Feature First

Small Widgets

Repository Pattern

Immutable Models

Strong Typing

No Business Logic in UI

Meaningful Naming

---

# Future Architecture

Atlas Platform

↓

Atlas Fleet

↓

Atlas Business

↓

Atlas API

↓

Atlas Analytics

↓

Atlas Intelligence

All products will share the same backend platform.

---

# Architecture Goals

Simple

Reliable

Fast

Scalable

Maintainable

Cloud Native

AI Ready

Developer Friendly

---

© Atlas Labs
