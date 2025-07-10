<div align="center">
  <img 
    src="https://capsule-render.vercel.app/api?type=soft&color=7b21e8&height=120&text=Linki%&animation=fadeIn&fontColor=ffffff&fontSize=60" 
    width="100%"
  />
</div>

# Linki - All-in-one platform for influencer marketing

## 📝 Project Overview

Linki is a comprehensive marketing platform connecting **influencers** with **advertisers**. Influencers can participate in brand campaigns, while advertisers can find suitable influencers for their marketing initiatives. The platform ensures a secure and transparent advertising ecosystem through features like **electronic contracts, real-time chat, and automated settlements**.

### [ERD Link](https://www.erdcloud.com/d/tHnS9EZLguhoSFaMD)
### [User Page](https://www.linki.kr)
### [Admin Page](https://www.admin.linki.kr)
### [Team Notion](https://shorturl.at/dwkOo)
## 🏗️ System Architecture

### Microservice Architecture
```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│   Frontend      │    │   API Gateway   │    │   Discovery     │
│   (Vue.js)      │◄──►│   (Port: 8000)  │◄──►│   (Port: 8761)  │
│                 │    │                 │    │                 │
└─────────────────┘    └─────────────────┘    └─────────────────┘
                                │
                ┌───────────────┼───────────────┐
                │               │               │
        ┌───────▼──────┐ ┌──────▼──────┐ ┌─────▼──────┐
        │Integration   │ │Chat Service │ │Payment     │
        │Service       │ │             │ │Service     │
        │              │ │             │ │            │
        └──────────────┘ └─────────────┘ └────────────┘
                │               │               │
        ┌───────▼──────┐ ┌──────▼──────┐ ┌─────▼──────┐
        │Subscribe     │ │Admin        │ │Chatbot     │
        │Service       │ │Integration  │ │Service     │
        │              │ │Service      │ │            │
        └──────────────┘ └─────────────┘ └────────────┘
```



```markdown
<div align="center">
  <img
    src="https://capsule-render.vercel.app/api?type=soft&color=7b21e8&height=120&text=LINKI%20PROJECT&animation=fadeIn&fontColor=ffffff&fontSize=60"
    width="100%"
  />
</div>

# Linki - Influencer Marketing Platform

## 📝 Project Overview

Linki is a comprehensive marketing platform connecting **influencers** with **advertisers**. Influencers can participate in brand campaigns, while advertisers can find suitable influencers for their marketing initiatives. The platform ensures a secure and transparent advertising ecosystem through features like **electronic contracts, real-time chat, and automated settlements**.

---

## 🛠️ Tech Stack

### Backend
- **Framework**: Spring Boot 3.4.5+
- **Language**: Java 17
- **Database**: MySQL 8.0
- **ORM**: JPA/Hibernate + MyBatis
- **Security**: Spring Security + JWT
- **Message Oriented Middleware**: Apache Kafka
- **Service Discovery**: Netflix Eureka
- **API Gateway**: Spring Cloud Gateway
- **Cache**: Redis
- **External APIs**:
    - YouTube Data API v3
    - YuCanSign Electronic Contract API
    - Toss Payments API
    - OpenAI GPT API

### Frontend
- **Framework**: Vue.js 3
- **State Management**: Pinia
- **Router**: Vue Router 4
- **HTTP Client**: Axios
- **Charts**: ApexCharts, ECharts
- **Real-time Communication**: WebSocket + STOMP

### Infrastructure
- **Cloud Storage**: Naver NCloud
- **Build Tool**: Gradle
- **Development Tools**: Vite, ESLint, Prettier

---

## 🎯 Key Features

### 👤 User Management
- **Influencers**: Channel registration, campaign proposal submission, contract management
- **Advertisers**: Campaign creation, influencer selection, contract drafting
- **Administrators**: User management, contract approval, settlement management
- **OAuth Login**: Google social login support

### 📊 Campaign & Contract Management
- Campaign creation and management
- Proposal submission and review
- Electronic contract generation (YuCanSign integration)
- Automatic contract status updates
- Advertising fulfillment verification system

### 💬 Real-time Communication
- WebSocket-based real-time chat
- Contract progress notifications
- SSE (Server-Sent Events) based notification system
- Email notification feature

### 💳 Payment & Settlement
- Toss Payments integration
- Automatic subscription renewal service
- Subscription cancellation service

### 📈 Analytics & Reporting
- YouTube channel statistics collection
- Campaign performance analysis
- Dashboard and chart provision
- Influencer/Advertiser evaluation system

### 🤖 AI Features
- GPT-based chatbot service
- Campaign recommendation system
- Content analysis

---

## 📁 Project Structure

```

linki/
├── backend/
│   ├── discovery-service/          \# Eureka Server
│   ├── apigateway-service/         \# API Gateway
│   ├── integration-service/        \# Main business logic
│   ├── admin-integration-service/  \# Admin functionalities
│   ├── chat-service/               \# Chat service
│   ├── payment-service/            \# Payment service
│   ├── subscribe-service/          \# Subscription service
│   └── chatbot-service/            \# Chatbot service
├── frontend/
│   ├── linki-user/                 \# User web app
│   ├── linki-admin/                \# Admin web app
│   └── json-server/                \# Mock API for development
└── quries/                         \# Database schema & dummy data

````

---

## 🚀 How to Run

### 1. Prerequisites
- Java 17+
- Node.js 18+
- MySQL 8.0+
- Redis 6.0+
- Apache Kafka 2.8+

### 2. Database Setup
```sql
mysql -u root -p quries/tableInit.sql
mysql -u root -p linkiDB < quries/dummydata.sql
````

### 3\. Backend Service Execution Order

#### 3.1 Discovery Service (Eureka Server)

```bash
cd discovery-service
./gradlew bootRun
# Check: http://localhost:8761
```

#### 3.2 API Gateway

```bash
cd apigateway-service
./gradlew bootRun
# Check: http://localhost:8000
```

#### 3.3 Core Services

```bash
# Integration Service (Main service)
cd integration-service
./gradlew bootRun

# Chat Service
cd chat-service
./gradlew bootRun

# Payment Service
cd payment-service
./gradlew bootRun

# Subscribe Service
cd subscribe-service
./gradlew bootRun

# Admin Integration Service
cd admin-integration-service
./gradlew bootRun

# Chatbot Service
cd chatbot-service
./gradlew bootRun
```

### 4\. Frontend Execution

#### 4.1 User Web App

```bash
cd frontend/linki-user
npm install
npm run dev
# Check: http://localhost:3001
```

Add persistedstate API:

```bash
cd frontend/linki-user
npm install pinia-plugin-persistedstate@3
```

#### 4.2 Admin Web App

```bash
cd frontend/linki-admin
npm install
npm run dev
# Check: http://localhost:3002
```

-----

## 🔧 Configuration

### Backend Configuration Files

Check the `application.yml` or `application.properties` in each service for the following settings:

```yaml
# Common Configuration
eureka:
  client:
    service-url:
      defaultZone: http://localhost:8761/eureka

spring:
  datasource:
    url: jdbc:mysql://localhost:3306/linkiDB
    username: your_username
    password: your_password
  
  redis:
    host: localhost
    port: 6379
```

### Environment Variable Setup

```bash
# JWT Secret Key
export SECRET_HS256=your_jwt_secret_key

# YouTube API Key
export YOUTUBE_API_KEY=your_youtube_api_key

# YuCanSign API
export UCAN_SIGN_API_KEY=your_ucan_sign_key

# Toss Payments
export TOSS_CLIENT_KEY=your_toss_client_key
export TOSS_SECRET_KEY=your_toss_secret_key

# OpenAI API
export OPENAI_API_KEY=your_openai_api_key
```

-----

## 📊 Database Schema

### Key Tables

  - **user**: Basic user information
  - **influencer**: Influencer details
  - **advertiser**: Advertiser details
  - **channel**: YouTube channel information
  - **campaign**: Campaign details
  - **proposal**: Proposal details
  - **contract**: Contract information
  - **settlement**: Settlement details
  - **chat**: Chatroom information
  - **message**: Message content

-----

## 🔍 API Documentation

### Key API Endpoints

#### User Management

  - `POST /v1/api/auth/login` - User login
  - `POST /v1/api/auth/register` - User registration
  - `GET /v1/api/user/profile` - Retrieve user profile

#### Campaign Management

  - `GET /v1/api/campaigns` - List campaigns
  - `POST /v1/api/campaigns` - Create a new campaign
  - `POST /v1/api/proposals` - Submit a campaign proposal

#### Contract Management

  - `POST /v1/api/contracts` - Create a new contract
  - `GET /v1/api/contracts/{id}` - Retrieve contract details
  - `PUT /v1/api/contracts/{id}/complete` - Mark contract as complete

#### Chat

  - `GET /v1/chat-service/api/chats` - List chat rooms
  - `WebSocket /ws/chat` - Real-time chat communication

#### Payments

  - `POST /v1/payment-service/api/billing` - Register billing key
  - `POST /v1/subscribe-service/api/subscribe` - Subscribe to service

-----

## 🔐 Security

  - JWT-based authentication and authorization
  - Spring Security configuration
  - CORS policy enforcement
  - API Rate Limiting
  - Sensitive information encryption
  - Concurrency control via database locks

-----

## 📈 Performance Optimization

  - Redis caching
  - Database index optimization (54 indexes applied)
  - Keyset pagination for efficient data retrieval
  - Asynchronous processing with Kafka for high-traffic handling
  - CDN integration for images and static files

-----

## 🤝 How to Contribute

1.  Fork the repository
2.  Create your feature branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

-----

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](https://www.google.com/search?q=LICENSE) file for details.

-----

## 👥 Team

  - [Minhyeok Shin](https://www.google.com/search?q=https://github.com/minhyeokshin) (Team Lead): Data Analysis, Platform Admin Features
  - [Yoonah Ko](https://github.com/kya9505) (Deputy Lead): Notion & Documentation, Chat
  - [Jeongseop Lee](https://github.com/dlwjdtjq001): Network Management, Payment/Subscription Features, MSA Infrastructure
  - [Sungjun Kim](https://github.com/kimsj18): Security, User Management, Chatbot
  - [Seonmin Kim](https://github.com/seonmin12): Influencer Features
  - [Nanhee Jeong](https://github.com/Eveieve): Advertiser Features

-----

## 📞 Contact

For any inquiries about the project, please open an issue or contact us via email.

-----

**Linki** - An innovative marketing platform connecting influencers and brands 🚀

```
```
