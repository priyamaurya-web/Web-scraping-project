# Weather Web Scraping Project

A Python-based web scraping project that retrieves real-time weather data using two different approaches — Google Search scraping via BeautifulSoup and the `wttr.in` weather API with auto IP-based location detection.

---

## Features

- Scrape live weather data (temperature, sky condition, wind) from Google Search
- Auto-detect user's current city using IP geolocation
- Fetch a 3-day weather forecast using the `wttr.in` service
- Lightweight — no paid API keys required

---

## Project Structure

```
weather-webscraping/
│
├── Weather_Webscraping_project.ipynb   # Main notebook
└── README.md
```

---

## Approaches

### Approach 1 — Google Search Scraping (BeautifulSoup)
Sends a search query to Google for a given city and parses the weather snippet from the HTML response.

**Extracted data:**
- Temperature
- Time of reading
- Sky description (e.g. Haze, Cloudy)
- Wind speed and direction

**Example output:**
```
Temperature is: 89°F
Time: Monday 12:16 PM
Sky Description: Haze
Winds E at 10 to 15 km/h.
```

> ⚠️ **Note:** Google frequently updates its HTML class names. If scraping breaks, inspect the current page structure and update the class selectors accordingly.

---

### Approach 2 — IP Geolocation + wttr.in
Uses `ipinfo.io` to detect the user's current city from their IP address, then fetches a detailed 3-day ASCII weather forecast from `wttr.in`.

**Extracted data:**
- Current location (auto-detected)
- Current temperature, wind, visibility, precipitation
- Morning / Noon / Evening / Night forecasts for 3 days

**Example output:**
```
Current Location: Salt Lake City
Weather report: Salt Lake City

   \  /       Partly cloudy
_ /"".-    73 °F
  \_(   ).  ↖ 8 mph
  /(___(__) 9 mi
```

---

## Dependencies

```
requests
beautifulsoup4
```

Install via:

```bash
pip install requests beautifulsoup4
```

---

## How to Run

1. Open `Weather_Webscraping_project.ipynb` in Google Colab or Jupyter Notebook
2. Run **Cell 1** for city-specific Google weather scraping (change the `city` variable as needed)
3. Run **Cell 2** for auto-detected location forecast via `wttr.in`

---

## Limitations

- Google scraping depends on CSS class names that may change without notice
- IP geolocation may not always reflect the actual physical location (e.g. VPN, cloud environments like Colab will return the server's location)
- `wttr.in` output is ASCII-formatted and best suited for terminal/console display

---

## Tech Stack

`Python` | `Requests` | `BeautifulSoup4` | `ipinfo.io` | `wttr.in`
