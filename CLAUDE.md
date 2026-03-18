# MMGISWeb

Corporate website for **MobileGIS Ltd**, built with Blazor WebAssembly (.NET 10). Focuses on OpenSitePlan and geospatial standards (OGC, CityGML, GeoPose, etc.).

## Stack

- **Framework:** Blazor WebAssembly (client-side only, no server)
- **Language:** C# / Razor components
- **Target:** net10.0
- **Styling:** Bootstrap 5 + scoped CSS (`.razor.css` files per component)
- **Root namespace / assembly:** `MGISWeb`

## Project file

The active project file is `mgisweb.csproj`. Ignore `CompanySite.csproj`, `CompanySite.csprojx`, `ospWeb.csproj` — these are old/archived artifacts. The `old/` directory is excluded from build.

## Dev server

```bash
dotnet watch
```

- HTTP: http://localhost:5198
- HTTPS: https://localhost:7281

## Structure

```
Layout/         # NavMenu, MainLayout (shared layout components)
Pages/          # Route-level pages: Home, About, Projects, Action, Counter, Weather
wwwroot/        # Static assets: index.html, css/app.css, Bootstrap lib, logo, sample-data/
_Imports.razor  # Global @using statements for all components
App.razor       # Root router component
Program.cs      # WebAssembly entry point, HttpClient registration
```

## Data

Projects page loads from `wwwroot/sample-data/weather.json` (filename is a leftover from the Blazor template — the actual content is project data, not weather).

## Conventions

- Scoped CSS lives in `ComponentName.razor.css` alongside each component — prefer editing there over `app.css` for component-specific styles.
- Responsive breakpoints in `wwwroot/css/app.css`: 640px (mobile) and 1200px (wide).
- Navigation links in `Layout/NavMenu.razor` — both internal routes and external links (OpenSitePlan, Polytope Services).
- No backend; all data is static JSON or hardcoded in Razor markup.
