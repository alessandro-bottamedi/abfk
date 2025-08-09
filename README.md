# abfk - A Better FV Kiosk

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

To get the dashboard working, you need to set your public API URL. For a pre-configured setup that requires no user interaction, you can edit the config object directly within the index.html file.

```javascript
// --- DASHBOARD CONFIGURATION ---
const config = {
  apiUrl: "YOUR_API_URL_GOES_HERE",
  // ... other settings
};
// --- END OF CONFIGURATION ---
```

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

Contributions are welcome\! If you have ideas for new features, improvements, or bug fixes, feel free to open an issue or submit a pull request.

## 📄 License

This project is open-source and available under the [MIT License](https://www.google.com/search?q=LICENSE).
