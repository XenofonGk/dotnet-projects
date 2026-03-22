# ASP.NET MVC 5 — Mosh Tutorial Notes
> Video: https://www.youtube.com/watch?v=hZ1DASYd9rk  
> Author notes for personal study

---

## Setup (Mac with VS Code)

```bash
# Create project
dotnet new mvc -n ProjectName
cd ProjectName

# Add Razor runtime compilation (hot reload for views)
dotnet add package Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation

# Run
dotnet run
```

**Program.cs** — enable runtime compilation:
```csharp
builder.Services.AddControllersWithViews().AddRazorRuntimeCompilation();
```

**Important:** Your `.csproj` must use the Web SDK:
```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
```

---

## 1. MVC Architecture

| Layer | Responsibility |
|-------|---------------|
| **Model** | Data + business logic |
| **View** | What the user sees (HTML + Razor) |
| **Controller** | Handles requests, talks to model, returns view |

The flow: **Request → Router → Controller → Model → Controller → View → Response**

---

## 2. Controllers

- Every controller class inherits from `Controller`
- Each public method = an **Action** (maps to a URL)
- Returns an `IActionResult`

```csharp
public class MoviesController : Controller
{
    public IActionResult Index()
    {
        return View();
    }

    public IActionResult Details(int id)
    {
        return View();
    }
}
```

---

## 3. Action Results

| Method | What it returns |
|--------|----------------|
| `View()` | Renders a Razor view |
| `Content("text")` | Plain text/HTML string |
| `Json(obj)` | JSON response |
| `NotFound()` | 404 |
| `RedirectToAction("Name")` | Redirect to another action |

---

## 4. Routing

**Convention-based** — defined globally (default):
```
/controller/action/id
/movies/details/1  →  MoviesController.Details(1)
```

**Attribute-based** — defined on the method directly:
```csharp
[Route("movies/featured")]
public IActionResult Featured()
{
    return View();
}
```

Attribute routing gives you more control. Useful for APIs and custom URLs.

---

## 5. Passing Data to Views

**Three ways:**

```csharp
// 1. ViewData — dictionary, no type safety
ViewData["Title"] = "Movies Page";

// 2. ViewBag — dynamic wrapper around ViewData
ViewBag.Title = "Movies Page";

// 3. ViewModel (BEST) — strongly typed
var model = new Movie { Name = "Terminator" };
return View(model);
```

Always prefer **ViewModels** for real apps. ViewBag/ViewData are fine for quick prototypes.

---

## 6. Razor Syntax

```html
@* This is a Razor comment *@

@{ var name = "Mosh"; }          @* Code block *@

<h1>@name</h1>                   @* Output variable *@

@if (Model.IsNew) {
    <span>New!</span>
}

@foreach (var movie in Model.Movies) {
    <li>@movie.Name</li>
}
```

---

## 7. Views & Folder Structure

```
Views/
  Shared/
    _Layout.cshtml       ← master layout (like a template)
    _ViewStart.cshtml    ← sets default layout for all views
  Movies/
    Index.cshtml
    Details.cshtml
  Home/
    Index.cshtml
```

- Views must match controller name + action name by convention
- `_Layout.cshtml` contains `@RenderBody()` where page content is injected

---

## 8. Partial Views

Reusable chunks of UI. Like components.

```html
@* Inside a view *@
@Html.Partial("_NavBar")
```

Partial view file: `Views/Shared/_NavBar.cshtml`  
Naming convention: prefix with underscore `_`

---

## 9. Action Parameters

MVC automatically maps URL/form data to action parameters:

```csharp
// URL: /movies/details?id=5
public IActionResult Details(int id) { ... }

// URL: /movies/details/5  (via route)
[Route("movies/details/{id}")]
public IActionResult Details(int id) { ... }
```

---

## 10. Adding Bootstrap

Already included when you use `dotnet new mvc`.  
Check `wwwroot/lib/bootstrap/`.

Use in layout:
```html
<link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.min.css" />
```

---

## Key Concepts to Remember

- **Convention over configuration** — follow naming conventions and things just work
- **Separation of concerns** — controllers don't know HTML, views don't know business logic
- **Strongly typed views** — declare `@model MovieViewModel` at top of view for IntelliSense
- **`wwwroot/`** — all static files go here (CSS, JS, images)
- **`appsettings.json`** — configuration (connection strings, etc.)
