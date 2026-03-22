# 🚀 .NET Developer Internship Preparation

![.NET](https://img.shields.io/badge/.NET-10.0-512BD4?logo=dotnet)
![C#](https://img.shields.io/badge/C%23-13.0-239120?logo=csharp)
![SQL Server](https://img.shields.io/badge/SQL_Server-2022-CC2927?logo=microsoft-sql-server)
![Entity Framework](https://img.shields.io/badge/EF_Core-10.0-512BD4?logo=dotnet)

This repository documents my journey from learning the basics of C# to building complex ASP.NET Core MVC applications and Web APIs.

---

## 📅 Roadmap Overview

### 🔹 [Week 1: C# Fundamentals](https://github.com/XenofonGk/dotnet-projects/tree/main/Week1)
Focus: Object-Oriented Programming (OOP), Logic, and Console Applications.
- **Projects:** Bank Account Simulation, Library Management, To-Do List, Student Grade Calculator.
- **Key Skills:** Classes, Inheritance, Collections, Exception Handling.

### 🔹 [Week 2: ASP.NET Core MVC & Entity Framework](https://github.com/XenofonGk/dotnet-projects/tree/main/Week%202)
Focus: Model-View-Controller architecture and Database Integration.
- **Projects:** 
  - **MyProject (MVC):** A category management system with SQL Server.
  - **TodoApi:** A RESTful API with DTO patterns and Swagger documentation.
- **Key Skills:** EF Core Migrations, SQL Server, Razor Views, Dependency Injection.

---

## 🛠️ Technical Stack
- **Language:** C# 13 / .NET 10.0
- **Database:** Microsoft SQL Server (Docker-based)
- **ORM:** Entity Framework Core
- **Architecture:** MVC (Model-View-Controller)
- **Tools:** Azure Data Studio, dotnet CLI

---

## ⚙️ How to Run Locally

### Prerequisites
- .NET 10 SDK
- Docker (for SQL Server)

### Running the MVC App
```bash
cd "Week 2/MyProject"
dotnet ef database update
dotnet run
```

### Running the Web API
```bash
cd "Week 2/TodoApi"
dotnet run
```

---
*Developed by Xenofon Gkountas*
