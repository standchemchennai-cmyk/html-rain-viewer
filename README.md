# HTML Rain Viewer

A standalone interactive weather map for exploring **satellite infrared cloud imagery**, **precipitation radar**, and **lightning activity** around India and the Bay of Bengal.

## Features

- Real geographic basemap with pan and zoom.
- Colour-enhanced infrared (IR) imagery from JMA Himawari, plus alternate satellite colour modes.
- Historical satellite playback over approximately the previous 24 hours, using published observation timestamps.
- Independent satellite, radar, and lightning on/off checkboxes and opacity controls.
- Chennai, ECR coast, Tamil Nadu, Bay of Bengal, and India map presets.
- Time labels in India Standard Time (IST).

> **Important:** Orange and red in enhanced infrared imagery indicate very cold/high cloud tops, **not directly measured rain intensity**. Rain radar is a separate overlay.

## Run

Open [index.html](./index.html) in a current browser with internet access. No build process or installation is needed. The page connects directly to third-party imagery services.

For a local development server, run `python -m http.server 8000` in the repository folder and open `http://localhost:8000`.

## Data sources and caveats

| Layer | Source | Notes |
| --- | --- | --- |
| Basemap | Esri World Topographic Map | Online tiles; service availability and usage limits apply. |
| Infrared satellite | [Japan Meteorological Agency (Himawari)](https://www.jma.go.jp/bosai/himawari/) | Uses the provider's available observation times; a requested frame may be unavailable. |
| Rain radar | [RainViewer](https://www.rainviewer.com/) | Historical availability is much shorter than 24 hours, typically around two hours. Geographic coverage may vary. |
| Lightning | [LightningMaps](https://www.lightningmaps.org/) | Live overlay, not a 24-hour historical lightning archive. |

This is a personal weather visualization, not an official warning or forecasting service. Network failures, access controls, coverage gaps, and provider changes can affect individual layers.

## Privacy / deployment

This repository is intended to remain **private**. GitHub Pages is not configured. Keeping the source repository private does not automatically make a separately published website private, so check access settings before any future deployment.
