# Moon Tracker 🌙

An AR web app for **Karwa Chauth**: point your phone at the sky and it shows where the moon is, when it rises and when it will actually be visible above the rooftops.

**Live:** https://chand-dekho.vercel.app

## Features

- **AR moon finder**: camera view with the moon marker, an arrow towards it and the horizon line. Also works without the camera on a dark sky.
- **Tonight's path**: the moon's track for the next 12 hours with hourly times.
- **"Visible from" time**: when the moon clears local buildings or trees. You can measure the roof height by aiming at the roof edge (📐).
- **Moonrise countdown, phase and cloud forecast** for that time.
- **Steady marker**: on iPhone the gyroscope drives the motion and the compass only corrects north slowly. Smoothing is adjustable.
- **Share**: a text with the time, or a 9:16 story image (camera photo or flat night sky) for Instagram, TikTok, Snapchat or the gallery.
- **Help (?)**: steps for iPhone and Android when location, camera or motion access is blocked, plus a fallback where you type in your city.
- German or English, picked from the device language. Settings and location are saved on the device.

## How it works

The whole app is a single [`index.html`](index.html) with no framework and no build step.

| What | Source |
|---|---|
| Moon position, phase, rise and set | [SunCalc](https://github.com/mourner/suncalc), via CDN |
| Cloud forecast and city search | [Open-Meteo](https://open-meteo.com), no API key. Coordinates are rounded to about 10 km before they are sent. |
| Phone direction | `DeviceOrientationEvent`. On iOS: gyro `alpha` plus `webkitCompassHeading`. |
| Analytics | Vercel Web Analytics, no cookies |

It needs HTTPS for location, camera and motion sensors. Vercel provides that.

## Run locally

Serve the folder over HTTPS and open it on your phone, or open `index.html` on a desktop. On a desktop there are no sensors, so you only get the text info.

## Deploy

```bash
vercel deploy --prod
```

[`vercel.json`](vercel.json) only copies `index.html` into `dist/`. That build step is what makes Vercel serve the analytics script. Bump `VERSION` in `index.html` on every deploy; it is shown in the footer.

## License

[MIT](LICENSE) © 2026 Sameer Goswami · SG Studio · [app.goswami.de](https://app.goswami.de)
