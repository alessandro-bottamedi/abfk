# abfk - A Better Fv Kiosk

A very simple, responsive, and modern alternative to the default FusionSolar kiosk dashboard.

## ✨ Features

- **Fully Responsive:** Looks great on any device, from a phone to a giant wall-mounted TV.
- **Highly Customizable:** Easily change the theme, language, and text size with a simple config.
- **Light & Dark Themes:** Choose the theme that best suits your environment.
- **Zero Dependencies:** It's a single HTML file. No complex setups, no servers needed. Just open it in a browser.

## 🚀 Setup

Using this dashboard is as simple as it gets:

1.  Download the `index.html` file from this repository.
2.  Open the file with any modern web browser.
3.  For kiosk mode, set your browser to full-screen (`F11` on most systems).

## ⚙️ Configuration

All settings are located in a single `config` object at the beginning of the `<script>` tag inside the `index.html` file. Open the file with a text editor to modify them.

```javascript
// --- DASHBOARD CONFIGURATION ---
const config = {
  apiUrl:
    "https://corsproxy.io/?url=https://uni003eu5.fusionsolar.huawei.com/rest/pvms/web/kiosk/v1/station-kiosk-file?kk=YOUR_KIOSK_KEY",
  refreshIntervalMinutes: 5,
  theme: "dark",
  textSize: "normal",
  language: "en",
};
// --- END OF CONFIGURATION ---
```

### Configuration Parameters

| Parameter                | Type     | Default    | Description                                                                                                                                                                                                               |
| :----------------------- | :------- | :--------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `apiUrl`                 | `String` | `""`       | **(Required)** This is the most important setting. You must replace `YOUR_KIOSK_KEY` with the key from your own kiosk URL provided by FusionSolar. It's recommended to use a CORS proxy to avoid browser security issues. |
| `refreshIntervalMinutes` | `Number` | `5`        | The interval in minutes at which the dashboard will automatically fetch new data from the API.                                                                                                                            |
| `theme`                  | `String` | `'dark'`   | Sets the visual theme. Available options: `'dark'`, `'light'`.                                                                                                                                                            |
| `textSize`               | `String` | `'normal'` | Adjusts the overall text size, useful for large displays viewed from a distance. Available options: `'normal'`, `'large'`, `'xlarge'`.                                                                                    |
| `language`               | `String` | `'en'`     | Sets the display language for all labels on the dashboard. Available options: `'en'` (English), `'it'` (Italian).                                                                                                         |

### How to get your `apiUrl`

1.  Log in to your Huawei FusionSolar portal.
2.  Click on the **"Kiosk"** button on the main dashboard to access the kiosk view.
3.  Enable Kiosk mode if it's not already active.
4.  Copy the long URL from your browser's address bar. It will look something like this:
    `https://uni003eu5.fusionsolar.huawei.com/pvmswebsite/nologin/assets/build/cloud.html#/kiosk?kk=XXXXXXXXXXXXXXXXX`
5.  From that URL, extract only the first part (your public URL), for example: `https://uni003eu5.fusionsolar.huawei.com`
6.  Now, construct the correct API endpoint by combining your public URL with the API path and your key (`kk=` parameter):
    `<your_public_url>/rest/pvms/web/kiosk/v1/station-kiosk-file?kk=XXXXXXXXXXXXXXXXX`
7.  To function correctly, the dashboard needs a CORS proxy. We recommend the free `corsproxy.io` service, but you can use any other. Prepend the proxy URL to your newly constructed API endpoint. The final URL will be:
    `https://corsproxy.io/?url=<your_public_url>/rest/pvms/web/kiosk/v1/station-kiosk-file?kk=XXXXXXXXXXXXXXXXX`

This final URL is what you need to paste into the `apiUrl` field in the configuration.

## 🤝 Contributing

Contributions are welcome! If you have ideas for new features, improvements, or bug fixes, feel free to open an issue or submit a pull request.

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).
