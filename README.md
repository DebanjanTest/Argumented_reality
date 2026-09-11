# 🌐 WebAR Interactive AI Poster

[![MindAR](https://img.shields.io/badge/MindAR-v1.2.5-orange?style=flat-square&logo=augmented-reality)](https://hiukim.github.io/mind-ar-js-doc/)
[![A-Frame](https://img.shields.io/badge/A--Frame-v1.5.0-ef2d5e?style=flat-square&logo=aframe)](https://aframe.io/)
[![JSZip](https://img.shields.io/badge/JSZip-v3.10.1-yellow?style=flat-square)](https://stuk.github.io/jszip/)
[![WebAR](https://img.shields.io/badge/WebAR-No%20App%20Required-brightgreen?style=flat-square)](https://github.com/DebanjanTest/Argumented_reality)

An interactive Web Augmented Reality (WebAR) experience built with **MindAR** and **A-Frame**. Users can simply open a web page on their smartphone or computer camera, point it at the **AI Poster**, and view real-time AR slideshows and interactive infographic overlays—no app installation required!

---

## ✨ Features

- 📱 **Zero App Installation (WebAR):** Runs natively inside mobile and desktop web browsers (Safari, Chrome, Firefox, Edge).
- 🎯 **Multi-Target Image Tracking:** Uses MindAR compiled targets (`targets.mind`) with support for simultaneous tracking (`maxTrack: 5`).
- 🖼️ **Automated AR Slideshow:** Cycles through educational slide overlays every 7 seconds over the main target area.
- 💡 **Interactive Infographic Overlays:** Highlights sub-domains of Artificial Intelligence (Machine Learning, Deep Learning, and Neural Networks) directly over designated poster areas.
- 📦 **One-Click Asset Downloader:** Bundled with JSZip to allow users to download all poster assets and digital elements in a single `.zip` file directly from the browser.

---

## 📂 Project Structure

```text
Argumented_reality/
├── AI poster.jpg             # Reference poster to scan / print
├── index.html                # Main entry point (A-Frame scene & MindAR setup)
├── README.md                 # Project documentation
└── assets/
    ├── targets.mind          # Compiled MindAR feature descriptor file
    ├── Slideshow/            # Images used for the cycling slideshow overlay
    │   ├── 1.png
    │   ├── 2.png
    │   ├── 3.png
    │   └── 4.png
    └── elements/             # Visual overlays corresponding to poster targets
        ├── Artificial_intelligence.png
        ├── Deep_Learning.png
        ├── Machine_learning.png
        └── Neural_networks.png
```

---

## 🛠️ How It Works

1. **MindAR Image Tracking:** The `assets/targets.mind` file stores keypoint descriptors for up to 5 target images on the poster.
2. **Target Index Mapping:**
   - **Target 0 (`targetIndex: 0`):** Triggers the automated slideshow (`assets/Slideshow/1.png` through `4.png`).
   - **Target 1 (`targetIndex: 1`):** Overlays the **Artificial Intelligence** badge/infographic.
   - **Target 2 (`targetIndex: 2`):** Overlays the **Deep Learning** badge/infographic.
   - **Target 3 (`targetIndex: 3`):** Overlays the **Machine Learning** badge/infographic.
   - **Target 4 (`targetIndex: 4`):** Overlays the **Neural Networks** badge/infographic.
3. **Client-side Zipping:** When the **"Download Assets"** button is clicked, JSZip fetches the poster assets on the fly and triggers a zip download named `AI_Poster_Assets.zip`.

---

## 🚀 How to Get Started

> [!IMPORTANT]
> **HTTPS / Localhost Requirement:**
> Web browsers enforce strict security restrictions on camera access. The project **must** be served over `https://` or `http://localhost`. Directly double-clicking `index.html` (`file:///...`) will **not** allow camera access.

### Option 1: Quick Deployment via GitHub Pages (Recommended)

1. Open your repository on GitHub: [DebanjanTest/Argumented_reality](https://github.com/DebanjanTest/Argumented_reality).
2. Go to **Settings** > **Pages** (in the left sidebar).
3. Under **Build and deployment** > **Source**, select **Deploy from a branch**.
4. Set the branch to `main` and folder to `/ (root)`, then click **Save**.
5. Within 1–2 minutes, GitHub will generate your live HTTPS URL:
   ```text
   https://debanjantest.github.io/Argumented_reality/
   ```
6. Open this link on your mobile phone or scan the URL with a QR code!

---

### Option 2: Running Locally on Your Machine

#### 1. Clone the repository
```bash
git clone https://github.com/DebanjanTest/Argumented_reality.git
cd Argumented_reality
```

#### 2. Start a local static HTTP server
Choose any of the following lightweight servers:

- **Using Python 3:**
  ```bash
  python -m http.server 8000
  ```
- **Using Node.js (`npx serve`):**
  ```bash
  npx serve .
  ```
- **Using VS Code:**
  Install the [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) extension and click **"Go Live"**.

#### 3. Test on your browser
Open [http://localhost:8000](http://localhost:8000) in a browser that has a webcam.

#### 4. Testing on your Mobile Phone (Same Wi-Fi via HTTPS tunnel)
Because mobile camera access requires HTTPS, you can use [ngrok](https://ngrok.com/) or [localtunnel](https://localtunnel.github.io/www/) to expose your local port:
```bash
npx localtunnel --port 8000
# or
ngrok http 8000
```
Open the generated `https://` link on your smartphone's browser.

---

## 📖 Step-by-Step User Instructions

Follow these steps to experience the augmented reality poster:

1. **Prepare the Target Image:**
   - Open [`AI poster.jpg`](./AI%20poster.jpg) on a computer screen, tablet, or print it on paper.
   - Ensure the poster is placed under good lighting without heavy glare.
2. **Open the WebAR Application:**
   - On your smartphone or laptop, open the hosted URL in **Google Chrome** (Android) or **Safari** (iOS).
3. **Allow Camera Access:**
   - When prompted by your browser, tap **"Allow"** to grant camera permissions.
4. **Scan the Poster:**
   - Point your camera at the poster.
   - You will see a scanning overlay until the targets are detected.
5. **View the Interactive AR Experience:**
   - Keep your camera focused on the poster to see the rotating slideshow and the interactive AI components appear floating over their corresponding positions.
6. **Download Assets (Optional):**
   - Click or tap the **"Download Assets"** button at the bottom of the screen to save a `.zip` archive containing the poster graphics and element files.

---

## ⚙️ Customization Guide

### Changing the Slideshow Timing or Images
Edit `index.html` around line 40:
```javascript
const slideshowImages = [
  './assets/Slideshow/1.png',
  './assets/Slideshow/2.png',
  './assets/Slideshow/3.png',
  './assets/Slideshow/4.png'
];

// Change slide interval (in milliseconds, e.g., 5000 = 5 seconds)
setInterval(nextSlide, 7000);
```

### Compiling New Image Targets
If you update or redesign the poster:
1. Go to the online [MindAR Image Target Compiler](https://hiukim.github.io/mind-ar-js-doc/tools/compile).
2. Upload your target image(s) in the desired order (Target 0, Target 1, etc.).
3. Download the generated `targets.mind` file and place it in the `assets/` folder.

---

## ❓ Troubleshooting

| Issue | Solution |
| :--- | :--- |
| **Camera screen is black or doesn't start** | Ensure you are accessing via `https://` or `localhost`. Check browser permissions to confirm camera access is enabled. |
| **Target image is not detected** | Make sure the poster has sufficient lighting, is flat, and is not obscured by glare or reflections. |
| **Performance is laggy on mobile** | Close background apps or tabs and ensure your browser has hardware acceleration enabled. |
| **iOS Safari not tracking properly** | Ensure you are on iOS 14.5+ and have granted Safari camera permissions in *Settings > Safari > Camera*. |

---

## 🧰 Built With

- [MindAR.js](https://github.com/hiukim/mind-ar-js) - Web Augmented Reality engine for image tracking.
- [A-Frame](https://aframe.io/) - Web framework for building 3D and AR/VR experiences.
- [JSZip](https://stuk.github.io/jszip/) - Client-side ZIP file generation and compression.

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).