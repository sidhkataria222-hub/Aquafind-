# Aquafind-
AquaFind is a full-stack web application that helps students and faculty locate campus water refill stations. Built with React, Spring Boot, and PostgreSQL, it offers station search, availability status, walking-time estimates, and issue reporting to promote convenient hydration and reduce single-use plastic waste.
refillmap-fullstack/
│
├── frontend/                    # React + Vite
│   ├── public/
│   ├── src/
│   │   ├── App.jsx              # Main application UI
│   │   ├── main.jsx             # Entry point
│   │   └── styles.css           # Styling and responsive design
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   ├── Dockerfile
│   └── nginx.conf
│
├── backend/                     # Java + Spring Boot
│   ├── src/main/
│   │   ├── java/com/refillmap/
│   │   │   ├── RefillMapApplication.java
│   │   │   │
│   │   │   ├── config/
│   │   │   │   ├── WebConfig.java
│   │   │   │   └── SeedData.java
│   │   │   │
│   │   │   ├── controller/
│   │   │   │   └── StationController.java
│   │   │   │
│   │   │   ├── service/
│   │   │   │   └── StationService.java
│   │   │   │
│   │   │   ├── repository/
│   │   │   │   ├── StationRepository.java
│   │   │   │   └── IssueReportRepository.java
│   │   │   │
│   │   │   ├── model/
│   │   │   │   ├── Station.java
│   │   │   │   ├── IssueReport.java
│   │   │   │   ├── StationStatus.java
│   │   │   │   ├── WaterTemperature.java
│   │   │   │   └── IssueType.java
│   │   │   │
│   │   │   └── dto/
│   │   │       └── CreateIssueRequest.java
│   │   │
│   │   └── resources/
│   │       └── application.properties
│   │
│   ├── pom.xml
│   └── Dockerfile
│
├── docker-compose.yml           # Runs all services
└── README.md                    # Project documentation
