# E-Commerce Microservices Application

A full-stack MERN e-commerce application built with microservices architecture, featuring 4 separate Node.js backend services and a React frontend.

## 🏗️ Architecture Overview

This application demonstrates modern microservices architecture with the following components:

```
Frontend (React) → API Gateway → Microservices
                                    ├── User Service (3001)
                                    ├── Product Service (3002)
                                    ├── Cart Service (3003)
                                    └── Order Service (3004)
```

## 🔧 Technology Stack

### Backend
- **Runtime**: Node.js with Express.js
- **Database**: MongoDB with Mongoose ODM
- **Authentication**: JWT tokens
- **Architecture**: RESTful APIs with microservices

### Frontend
- **Framework**: React 18
- **Routing**: React Router
- **State Management**: React Query + Context API
- **HTTP Client**: Axios
- **Styling**: CSS3 with responsive design

## 📦 Microservices

### 1. User Service (Port 3001)
- User registration and authentication
- Profile management
- JWT token generation and validation
- User data persistence

## Project Execution
- -------------------------------------
### Dockerized deployment

**Create and Configure docker images and push to Hub**

- `docker-compose up -d --build`


<img width="1198" height="196" alt="image" src="https://github.com/user-attachments/assets/821a6b2f-4429-4f0c-acb0-4adce0cf236f" />


#
**Application Worked as expected in Docker**
#
- **Frontend**
  <img width="1755" height="720" alt="Screenshot from 2025-07-23 09-42-10" src="https://github.com/user-attachments/assets/b0885dd7-98b4-4140-a344-9549988c3d66" />
#
- **Products**
#
  <img width="1755" height="720" alt="Screenshot from 2025-07-23 09-42-23" src="https://github.com/user-attachments/assets/646250da-093b-4813-96e2-a332beb58780" />

- **User registration**

#
  <img width="1406" height="861" alt="image" src="https://github.com/user-attachments/assets/ab4059ed-cbc7-49f7-a91c-995e327df789" />
  #
  <img width="1755" height="720" alt="Screenshot from 2025-07-23 09-43-47" src="https://github.com/user-attachments/assets/c3e88eaa-c186-4be3-a30c-551e9699518e" />

#
- **MongoDB Records**
  <img width="1236" height="786" alt="Screenshot from 2025-07-23 10-02-19" src="https://github.com/user-attachments/assets/1925cb7e-2bea-4fcc-b3ac-87ac5fed85a2" />

- **Safely Shutdown Docker**

- `docker-compose down`

  <img width="837" height="207" alt="image" src="https://github.com/user-attachments/assets/de1b32e6-0611-44e1-bb24-a0799429ef8c" />


#
### Kubernetes Setup

**Create and Configure K8s Cluster in AWS**

- `eksctl create cluster --name munish-ecommerce-cluster-3 --region us-west-2--nodegroup-name standard-workers
          --node-type t3.medium --nodes 3`

#

<img width="731" height="444" alt="Screenshot from 2025-07-23 21-55-45" src="https://github.com/user-attachments/assets/f5427e52-e14d-4d96-8610-35abceac51f0" />

**Create Jenkins pipeline and deploy the application**

<img width="1150" height="500" alt="image" src="https://github.com/user-attachments/assets/82bef5c5-94e4-4af4-8003-3b4ac47da00d" />

<img width="670" height="500" alt="Screenshot from 2025-07-23 12-14-02" src="https://github.com/user-attachments/assets/4a817ade-b45a-423f-939f-0de777a99939" />

#
- **Post Pipline Success, Validating Services, Pods, Kube Nodes**
- `kubects get nodes`
- <img width="959" height="137" alt="Screenshot from 2025-07-23 12-26-37" src="https://github.com/user-attachments/assets/5054ea2a-1aad-4c19-870a-9e2365516bc7" />

- `kubects get pods`
- <img width="744" height="185" alt="Screenshot from 2025-07-23 12-24-34" src="https://github.com/user-attachments/assets/12867788-b5c6-4bdc-adc4-3cf99d28b172" />

- `kubects get svc`
  - Frontend end type configured as Loadbalancer
  
- <img width="1470" height="240" alt="Screenshot from 2025-07-23 12-24-15" src="https://github.com/user-attachments/assets/104453e8-3e5e-49cd-8bb7-c60fc3542f6f" />








































The application will be available at:
- Frontend: http://localhost:3000
- User Service: http://localhost:3001
- Product Service: http://localhost:3002
- Cart Service: http://localhost:3003
- Order Service: http://localhost:3004

## 🎯 Features

### User Features
- **Authentication**: Register and login with JWT tokens
- **Product Browsing**: View products with search, filtering, and pagination
- **Shopping Cart**: Add, update, and remove items
- **Checkout Process**: Complete order placement with shipping and payment
- **Order Management**: View order history and track status
- **Profile Management**: Update personal information and addresses

### Admin Features (Future Enhancement)
- Product and category management
- Order status updates
- Inventory management
- User management

## 📁 Project Structure

```
ecommerce-microservices/
├── backend/
│   ├── user-service/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   ├── server.js
│   │   └── package.json
│   ├── product-service/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── server.js
│   │   └── package.json
│   ├── cart-service/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── server.js
│   │   └── package.json
│   └── order-service/
│       ├── models/
│       ├── routes/
│       ├── server.js
│       └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── contexts/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.js
│   │   └── index.js
│   └── package.json
├── package.json
└── README.md
```

## 🔧 API Testing

You can test the APIs using tools like Postman or curl:

```bash
# Health check for all services
curl http://localhost:3001/health
curl http://localhost:3002/health
curl http://localhost:3003/health
curl http://localhost:3004/health

# Register a new user
curl -X POST http://localhost:3001/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"firstName":"John","lastName":"Doe","email":"john@example.com","password":"password123"}'

# Get products
curl http://localhost:3002/api/products

# Get categories
curl http://localhost:3002/api/categories
```

## 🚀 Deployment

### Production Considerations

1. **Environment Variables**: Use proper environment variable management
2. **Database**: Use MongoDB Atlas or other managed database services
3. **Process Management**: Use PM2 or similar for process management
4. **Load Balancing**: Implement load balancing for high availability
5. **Monitoring**: Add logging and monitoring solutions
6. **Security**: Implement rate limiting, CORS, and other security measures
