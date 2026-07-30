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
