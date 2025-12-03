# Trip Planners

Travel itineraries and trip plans organized by current and past trips.

## 📁 Folder Structure

```
99-trip-planners/
├── index.html                              # Main landing page
├── current-trips/                          # Ongoing trip plans
│   └── 2025-2026-asian-adventure/         # Trip name
│       ├── 2025-12-korea/                 # YYYY-MM-country
│       │   ├── seoul_itinerary_en.html
│       │   └── seoul_itinerary_cn.html
│       ├── 2025-12-japan/                 # (Future)
│       └── ...
└── past-trips/                             # Completed trips
    └── (archived trip folders)
```

## 🗂️ Naming Convention

### Trip Folders
- Format: `YYYY-YYYY-trip-name` (e.g., `2025-2026-asian-adventure`)
- Use lowercase with hyphens
- Include year range for multi-year trips

### Country/City Folders
- Format: `YYYY-MM-country` (e.g., `2025-12-korea`)
- **Date first** for chronological sorting
- Use lowercase country name
- Include year and month (YYYY-MM format)
- For multi-month stays, use start month

### Files
- Use descriptive names with language suffix
- Format: `city_itinerary_[en|cn].html`
- Examples:
  - `seoul_itinerary_en.html` (English)
  - `seoul_itinerary_cn.html` (Chinese)

## 🌍 Current Trips

### Asian Adventure 2025-2026
**Duration:** December 2025 - January 2026

- **Korea** (Dec 2025) - ✅ Complete
  - Seoul: Dec 3-9, 2025
- **Japan** (Dec 2025) - 🚧 Coming soon
  - Osaka & Kyoto: Dec 9-15, 2025
- More destinations TBA

## 📝 Adding New Trips

1. Create folder structure:
   ```bash
   mkdir -p current-trips/trip-name/YYYY-MM-country
   ```

2. Add itinerary HTML files to the country folder

3. Update `index.html` with new trip card

4. Commit and push:
   ```bash
   git add .
   git commit -m "Add [destination] itinerary"
   git push
   ```

## 🔗 GitHub Pages

Live site: https://wanzi-molly.github.io/trip-planners/

## 📦 Repository

GitHub: https://github.com/wanzi-molly/trip-planners
