# 🔹 Week 2: ASP.NET Core MVC & Web API

Welcome to the second week of my .NET internship preparation. This week focused on building web applications using the **Model-View-Controller (MVC)** pattern and creating RESTful APIs.

---

## 🛠️ Project Showcase

### 📦 1. MyProject (MVC Application)
A full-featured ASP.NET Core MVC application built with **Entity Framework Core**.
- **Features:** 
  - **Category Management:** Create, View, Edit, and Delete categories.
  - **Database Integration:** Integrated with SQL Server for persistent data.
  - **Migrations:** Managed with EF Core Code-First approach.
  - **Razor Views:** Clean UI with server-side rendering.
- **Tech:** ASP.NET Core 10, EF Core, SQL Server, Razor Pages, Bootstrap.

### 🌐 2. TodoApi (Web API)
A modern RESTful API for task management.
- **Features:**
  - **CRUD Operations:** Full GET, POST, PUT, DELETE functionality.
  - **DTO Pattern:** Use of Data Transfer Objects to separate models from public APIs.
  - **Swagger/OpenAPI:** Interactive API documentation for testing.
- **Tech:** ASP.NET Core 10, EF Core (In-Memory/SQL), OpenAPI (Swagger).

---

## 🏗️ Technical Highlights
- **Dependency Injection:** Services are registered and managed in `Program.cs`.
- **Database Migrations:** Full cycle of `add-migration` and `database update`.
- **Validation:** Server-side validation using Data Annotations (`[Required]`, `[Key]`).
- **Middleware:** Configuration of the HTTP request pipeline (Routing, Auth, Static Assets).

---

## ⚙️ Setup & Running

### 1. Database Update
Ensure your SQL Server is running, then run the following in `MyProject/`:
```bash
dotnet ef database update
```

### 2. Run the Projects
To start the MVC app:
```bash
dotnet run --project MyProject
```
To start the API:
```bash
dotnet run --project TodoApi
```

---

## 📺 Course Companion
For detailed, step-by-step notes following the **Bhrugen Patel (DotNetMastery)** course, check out [video.md](./video.md).

---
*Developed with ❤️ by XenofonGk*
