# 🚀 Week 2 .NET Master Guide

This workspace contains two distinct project types:
1.  **MyProject**: An ASP.NET Core MVC (Model-View-Controller) application.
2.  **TodoApi**: A RESTful Web API with OpenAPI (Swagger) support.

---

## 🛠️ Quick Productivity Tips
- `prop` + `Tab`: Quickly create a property.
- `ctor` + `Tab`: Create a constructor.
- `cw` + `Tab`: Write `Console.WriteLine()`.
- **Hot Reload**: Use `dotnet watch` to auto-restart the app when you save changes.
- **Razor Runtime Compilation**: Enabled in `MyProject`, allowing UI changes without restarting the app.

---

## 🏗️ Project Architectures

### 1. MyProject (MVC)
Best for traditional web applications where the server renders HTML.
- **Models**: `Category.cs` (Data structures).
- **Views**: `.cshtml` files (UI using Razor engine).
- **Controllers**: `HomeController.cs` (Handles logic & routing).
- **Data**: `ApplicationDbContext.cs` (EF Core bridge to SQL Server).

### 2. TodoApi (Web API)
Best for providing data to mobile apps or modern frontend frameworks (React/Angular).
- **Models**: `TodoItem.cs` and `TodoItemDTO.cs` (Data transfer objects to hide secrets).
- **Controllers**: `TodoItemsController.cs` (Handles HTTP GET/POST/PUT/DELETE).
- **Documentation**: Swagger/OpenAPI enabled at `/swagger` (or `/openapi/v1.json`).

---

## 💾 Database Cheat Sheet

### EF Core Approaches
1.  **Code-First**: Write C# classes (Models) first, then generate the DB. (Used here).
2.  **DB-First**: Existing database is used to generate C# classes.

### SQL Server Connection (`appsettings.json`)
```json
"ConnectionStrings": {
  "DefaultConnection": "Server=localhost,1433;Database=MyDb;User Id=sa;Password=YourPass123;TrustServerCertificate=True;"
}
```

### Essential CLI Commands (Entity Framework)
Run these in the project directory where the `DbContext` lives:
- `dotnet ef migrations add AddCategoryToDb`: Create a migration script.
- `dotnet ef database update`: Apply changes to the actual database.
- `dotnet ef migrations remove`: Roll back the last migration (if not updated yet).

---

## 🚀 How to Run
From the root directory (`Week 2/`):

**To run the MVC App:**
```bash
dotnet run --project MyProject
```

**To run the API:**
```bash
dotnet run --project TodoApi
```

**To run both (from VS Code):**
Use the **Run and Debug** sidebar and select the compound launch profile.

---

## 📝 Learning Points for Week 2
- **Dependency Injection**: Services are registered in `Program.cs` (e.g., `builder.Services.AddDbContext<...>`).
- **Middleware Pipeline**: The order of `app.Use...` in `Program.cs` matters (Routing -> Auth -> Endpoints).
- **DTOs (Data Transfer Objects)**: In `TodoApi`, we use DTOs to avoid exposing sensitive fields like `Secret` to the client.
- **Tag Helpers**: In MVC, use `asp-controller`, `asp-action`, and `asp-for` in your HTML to link to C# logic.

---
