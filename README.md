<div align="center">
  <img
    src="https://capsule-render.vercel.app/api?type=soft&color=7b21e8&height=120&text=LINKI%20&animation=fadeIn&fontColor=ffffff&fontSize=60"
    width="100%"
    alt="Linki Banner"
  />
</div>

---

## 📢 What is Linki? All-in-one Influencer Marketing Platform

**Linki** is an all-in-one marketing platform that seamlessly connects influencers and advertisers.  
Influencers can join brand campaigns, while advertisers can easily discover and contract with the right influencers.  
The platform ensures a secure and transparent advertising ecosystem with features like electronic contracts, real-time chat, and automated settlements.

### [Go to ERD Diagram](https://www.erdcloud.com/d/tHnS9EZLguhoSFaMD)
### [Notion Page - Meeting Logs, Deliverables ](https://shorturl.at/dwkOo)
---

## 🚀 Getting Started

### 1. Prerequisites
- Java 17+
- Node.js 18+
- MySQL 8.0+
- Redis 6.0+
- Apache Kafka 2.8+

### 2. Database Setup

```bash
mysql -u root -p < quries/tableInit.sql
mysql -u root -p linkiDB < quries/dummydata.sql
```

### 3. Backend Service Startup

#### 3.1 Discovery Service (Eureka)

```bash
cd discovery-service
./gradlew bootRun
# http://localhost:8761
```

#### 3.2 API Gateway

```bash
cd apigateway-service
./gradlew bootRun
# http://localhost:8000
```

#### 3.3 Core Services

```bash
# Integration Service
cd integration-service && ./gradlew bootRun

# Chat Service
cd ../chat-service && ./gradlew bootRun

# Payment Service
cd ../payment-service && ./gradlew bootRun

# Subscribe Service
cd ../subscribe-service && ./gradlew bootRun

# Admin Integration Service
cd ../admin-integration-service && ./gradlew bootRun

# Chatbot Service
cd ../chatbot-service && ./gradlew bootRun
```

### 4. Frontend Startup

#### 4.1 User Web App

```bash
cd frontend/linki-user
npm install
npm run dev
# http://localhost:3001
```

> **Pinia persisted state plugin**
>
> ```bash
> npm install pinia-plugin-persistedstate@3
> ```

#### 4.2 Admin Web App

```bash
cd frontend/linki-admin
npm install
npm run dev
# http://localhost:3002
```

---

## 🔧 Configuration

### Backend Config

Check each service's `application.yml` or `application.properties`:

```yaml
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

### Environment Variables

```bash
export SECRET_HS256=your_jwt_secret_key
export YOUTUBE_API_KEY=your_youtube_api_key
export UCAN_SIGN_API_KEY=your_ucan_sign_key
export TOSS_CLIENT_KEY=your_toss_client_key
export TOSS_SECRET_KEY=your_toss_secret_key
export OPENAI_API_KEY=your_openai_api_key
```

---

## 📊 Database Schema

**Key Tables**
- `user`: Basic user info
- `influencer`: Influencer details
- `advertiser`: Advertiser details
- `channel`: YouTube channel info
- `campaign`: Campaign details
- `proposal`: Proposal details
- `contract`: Contract info
- `settlement`: Settlement details
- `chat`: Chatroom info
- `message`: Message content

---

## 🔍 API Documentation

**User Management**
- `POST /v1/api/auth/login` — User login
- `POST /v1/api/auth/register` — User registration
- `GET /v1/api/user/profile` — Get user profile

**Campaign**
- `GET /v1/api/campaigns` — List campaigns
- `POST /v1/api/campaigns` — Create campaign
- `POST /v1/api/proposals` — Submit proposal

**Contract**
- `POST /v1/api/contracts` — Create contract
- `GET /v1/api/contracts/{id}` — Get contract
- `PUT /v1/api/contracts/{id}/complete` — Complete contract

**Chat**
- `GET /v1/chat-service/api/chats` — List chat rooms
- `WebSocket /ws/chat` — Real-time chat

**Payments**
- `POST /v1/payment-service/api/billing` — Register billing key
- `POST /v1/subscribe-service/api/subscribe` — Subscribe

---

## 🔐 Security

- JWT authentication/authorization
- Spring Security
- CORS policy
- API rate limiting
- Sensitive info encryption
- DB lock for concurrency

---

## 📈 Performance

- Redis caching
- 54 DB indexes
- Keyset pagination
- Kafka async processing
- CDN for static files

---

## 🤝 Contributing

1. Fork the repo
2. Create your branch (`git checkout -b feature/AmazingFeature`)
3. Commit (`git commit -m 'Add some AmazingFeature'`)
4. Push (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📝 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 👥 Team
- [Nanhee Jeong](https://github.com/Eveieve): Advertiser Features
- [Minhyeok Shin](https://github.com/minhyeokshin) (Team Lead): Data Analysis, Admin Features
- [Yoonah Ko](https://github.com/kya9505) (Deputy Lead): Docs, Chat
- [Jeongseop Lee](https://github.com/dlwjdtjq001): Network, Payment/Subscription, MSA Infra
- [Sungjun Kim](https://github.com/kimsj18): Security, User, Chatbot
- [Seonmin Kim](https://github.com/seonmin12): Influencer Features
  
---

## 📞 Contact

For any inquiries, please open an issue or contact us via email.

---

**Linki** — An innovative marketing platform connecting influencers and brands 🚀
