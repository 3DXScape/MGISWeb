# CLAUDE.md

## Project Overview

**OOSPWeb** is a Blazor WebAssembly (WASM) application (.NET 10) for OpenSitePlan (OSP) / MobileGIS — an open-source initiative focused on spatial computing and geospatial standards (OGC, ISO, IEEE, MSF Spatial Computing).

GitHub remote: `https://github.com/3DXScape/MGISWeb`

---

## Build & Run

```bash
dotnet build          # Build
dotnet run            # Dev server (http://localhost:5197 / https://localhost:7281)
dotnet publish        # Production build
```

Hot reload is enabled in development via the DevServer package.

---

## Project Structure

```
/Layout/          - MainLayout, NavMenu, CookieConsent components
/Pages/           - Routable pages (Home, About, Projects, Services, ...)
/wwwroot/         - Static assets
  /css/app.css    - Global styles
  /lib/bootstrap/ - Bootstrap CSS
  /sample-data/   - JSON data files (projects, etc.)
Program.cs        - App entry point (registers HttpClient)
App.razor         - Router root
_Imports.razor    - Global using directives
```

---

## Tech Stack

- **Blazor WebAssembly** (.NET 10) — all routing and rendering is client-side
- **Bootstrap** — layout, grid, responsive utilities
- **Bootstrap Icons** — icon classes on nav items
- **HttpClient** — used in pages to fetch JSON from `wwwroot/sample-data/`
- No test project configured

---

## Key Conventions

- Pages live in `/Pages/` with a matching `.razor.css` scoped stylesheet
- Layout components (shared chrome) live in `/Layout/`
- Static data is served as JSON from `wwwroot/sample-data/` and fetched via `HttpClient`
- Cookie consent state is stored in `localStorage` via JS interop in `CookieConsent.razor`
- Routing is defined by `@page` directives; `NotFound.razor` handles unmatched routes

---

## Active Work / Notes

- Rebranding in progress: MGIS_Logo → OSP_Logo; NavMenu updated
- Demo/template pages (Counter, Weather, Action) are leftover scaffolding and may be removed
- Content on About page currently duplicates Home page — needs differentiation
- `sample-data/project.json` holds project listing data fetched by Projects.razor
