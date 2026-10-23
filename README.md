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
| Lightning | [LightningMaps / Blitzortung](https://www.lightningmaps.org/) | Live strike stream with automatically refreshed image tile fallback. Live overlays are not a historical lightning archive. |

This is a personal weather visualization, not an official warning or forecasting service. Network failures, access controls, coverage gaps, and provider changes can affect individual layers.

## Privacy / deployment

This repository is intended to remain **private**. GitHub Pages is not configured. Keeping the source repository private does not automatically make a separately published website private, so check access settings before any future deployment.

### Lightning troubleshooting

The viewer connects to the community live stream at `wss://live2.lightningmaps.org/` and plots strikes received in the displayed map. The status reports whether it is connected and how many recent strikes are visible. A count of zero can mean no strikes were received in the current view; this feed does not guarantee a complete 20-minute archive. If the connection drops, it retries with backoff and uses image tiles refreshed every 30 seconds. If both providers fail or browser/network restrictions apply, check the linked [official live Blitzortung map](https://maps.blitzortung.org/en/). Lightning is always **live**, even if the satellite time slider is moved to a historical frame. This volunteer network is non-commercial and is not a safety alert service.
