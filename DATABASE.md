# Atlas Database Design

**Version:** 0.1.0

**Status:** Draft

**Owner:** Atlas Labs

---

# Overview

Atlas uses PostgreSQL as its primary relational database, hosted on Supabase.

The database is designed with scalability, security, and maintainability in mind.

The schema follows normalization principles while allowing optimized queries for mobile applications.

---

# Database Principles

- UUID as primary keys
- Soft delete support
- Audit timestamps
- Foreign key constraints
- Indexed search columns
- Cloud-native design

---

# Core Modules

The database consists of the following modules.

- Users
- Vehicles
- Vehicle Library
- Trips
- Charging
- AI
- Notifications
- Settings
- Analytics

---

# Entity Relationship Overview

Users

↓

Vehicles

↓

Trips

↓

Charging Sessions

↓

AI Recommendations

---

# Tables

## users

Stores registered users.

Fields

- id
- email
- full_name
- profile_photo
- language
- country
- created_at
- updated_at

---

## manufacturers

Vehicle manufacturers.

Examples

Tesla

Togg

BYD

Kia

BMW

Mercedes-Benz

---

## vehicle_models

Vehicle model library.

Fields

- manufacturer_id
- model_name
- model_year
- battery_capacity
- usable_battery
- max_ac_power
- max_dc_power
- wltp_range
- consumption
- weight

---

## user_vehicles

Vehicles owned by users.

Fields

- user_id
- vehicle_model_id
- nickname
- license_plate
- current_odometer
- purchase_date
- is_default

---

## trips

Trip history.

Fields

- vehicle_id
- origin
- destination
- distance
- estimated_consumption
- actual_consumption
- departure_time
- arrival_time

---

## charging_networks

Charging providers.

Examples

Trugo

Eşarj

Zes

Voltrun

Tesla Supercharger

---

## charging_stations

Charging station library.

Fields

- network_id
- latitude
- longitude
- city
- address
- connector_type
- max_power
- availability

---

## charging_sessions

Charging history.

Fields

- user_vehicle_id
- charging_station_id
- start_percentage
- end_percentage
- charged_energy
- charging_duration
- charging_cost

---

## ai_conversations

AI chat history.

Fields

- user_id
- question
- answer
- created_at

---

## ai_recommendations

Stores AI decisions.

Examples

Charge tonight.

Avoid station X.

Reduce speed.

Use AC charging.

---

## notifications

Push notifications.

Examples

Low battery.

Weather warning.

Trip reminder.

---

## weather_cache

Temporary weather storage.

---

## favorites

Favorite charging stations.

---

## user_preferences

Application settings.

Language

Theme

Units

Charging preferences

Navigation preferences

---

# Relationships

User

↓

User Vehicles

↓

Trips

↓

Charging Sessions

Every charging session belongs to one vehicle.

Every vehicle belongs to one user.

Every recommendation belongs to one user.

---

# Index Strategy

Indexed Columns

email

vehicle_model_id

charging_station_id

created_at

latitude

longitude

---

# Security

Supabase Row Level Security (RLS)

Every user can only access their own data.

---

# Backup Strategy

Daily Backup

Point-in-time Recovery

Automated Snapshots

---

# Future Tables

battery_health

telemetry

fleet

insurance

energy_prices

maintenance

software_updates

---

# Database Goals

Fast

Reliable

Scalable

Secure

AI Ready

---

© Atlas Labs
