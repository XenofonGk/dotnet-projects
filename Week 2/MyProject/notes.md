# 🚀 Professional Developer's Guide (Best Practices)

Use this guide to expand your project properly and maintain professional standards.

---

## 🏗️ How to Add a New Page (Step-by-Step)

If you want to add a "Contact Us" page, follow these steps:

1.  **Add a Model (Optional):** If the page handles data, create a class in `Models/`.
2.  **Add an Action in Controller:**
    - Go to `HomeController.cs`.
    - Create a method like: `public IActionResult Contact() { return View(); }`.
3.  **Create the View:**
    - Right-click `Views/Home/` and create `Contact.cshtml`.
    - Add your HTML content here.
4.  **Add to Navigation:**
    - Go to `Views/Shared/_Layout.cshtml`.
    - Find the `<nav>` section and add a link using Tag Helpers:
      `<a class="nav-link" asp-controller="Home" asp-action="Contact">Contact</a>`

---

## 🌟 Best Practices for Clean Code

### 1. Naming Conventions (C#)
- **PascalCase** for Classes and Methods: `public class CategoryController`, `public void SaveData()`.
- **camelCase** for local variables and parameters: `var categoryList = ...`, `(int id)`.
- **Properties** should always have `get; set;`.

### 2. The "Skinny Controller" Rule
- Keep your **Controllers** as light as possible.
- Put complex math or business logic into separate "Service" classes (Week 3 level!).
- Controllers should only: **Get data -> Pass to View -> Return response**.

### 3. Use Tag Helpers instead of standard HTML
Instead of `<a href="/Home/Index">`, always use:
`<a asp-controller="Home" asp-action="Index">`
*Reason: If you change your URL structure later, .NET will automatically update all your links.*

### 4. Database Integrity
- Always use `[Key]` for IDs.
- Use `[Required]` for fields that must not be empty.
- **Never** change a Model class and forget to run:
  `dotnet ef migrations add NameOfChange`
  `dotnet ef database update`

---

## ⚠️ Common "Gotchas" (Debugging Tips)

| Problem | Likely Solution |
| :--- | :--- |
| **Login failed for 'sa'** | Check your password in `appsettings.json`. Ensure it's identical to the one in your SQL Server setup. |
| **Table 'X' not found** | Did you run `dotnet ef database update`? |
| **Red underlines on Model types** | Check your `using` statements at the top of the file! |
| **Page not loading** | Check the terminal for error logs; it usually tells you exactly which line failed. |

---

## 💡 Productivity Shortcuts
- **CTRL + .** (or CMD + .): Auto-import missing `using` statements.
- **dotnet watch**: Run this in your terminal to see changes instantly without restarting the app manually.
- **Azure Data Studio**: Always keep this open to verify your data is actually being saved.

---
*Happy Coding! You're building a solid foundation.* 💻
