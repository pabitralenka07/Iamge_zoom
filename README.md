# 🔍 Interactive Image Zoom & Magnifier

<p align="center">
  <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white" alt="HTML5" />
  <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white" alt="CSS3" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge" alt="License" />
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=for-the-badge" alt="PRs Welcome" />
</p>

<p align="center">
  A sleek, realistic, and hardware-accelerated magnifying glass effect crafted with <strong>pure Vanilla CSS Custom Properties</strong>, <strong>SVG Vector Art</strong>, and <strong>Modern JavaScript (ES6+)</strong>.
</p>

---

## ✨ Features

- 🔍 **Realistic SVG Magnifying Glass**: Custom SVG overlay designed with authentic frame borders, metallic handle grip, glass tint, and light reflection highlights.
- 🖱️ **Fluid Cursor Tracking**: Smooth and responsive viewfinder positioning that tracks pointer movement seamlessly across the image.
- 🎚️ **Dynamic Mouse-Wheel Zoom**: Adjust magnification level in real-time from **3x up to 30x** simply by scrolling your mouse wheel while hovering.
- ⚡ **Hardware Accelerated**: Viewport and coordinates are driven by GPU-optimized CSS transforms (`translate`, `scale`) and CSS custom properties (`--x`, `--y`, `--viewfinder-scale`), avoiding costly browser reflows.
- 📐 **Edge Clamping & Containment**: Intelligent mathematical coordinate thresholding keeps the magnified image securely bounded within the lens frame.
- 📦 **Zero Dependencies**: Pure HTML5, CSS3, and Vanilla JavaScript—no external frameworks, canvas rendering, or heavy libraries required.
- 📱 **Responsive Presentation**: Automatically adapts to viewport dimensions using modern CSS `vmin` units and a locked `16:9` aspect ratio container.

---

## 📸 Preview & Interaction

| Action | Result |
| :--- | :--- |
| **Hover Pointer** | Activates the circular viewfinder and displays the realistic magnifying glass |
| **Move Pointer** | Smoothly tracks cursor across the target image with synchronized zoomed viewport |
| **Mouse Wheel Scroll** | Dynamically increases or decreases the zoom scale in real-time (3x – 30x) |
| **Leave Image** | Smoothly hides the viewfinder lens and unbinds event listeners for performance |

---

## 📂 Project Structure

```plaintext
Image_zoom/
├── index.html        # Semantic HTML layout and inline SVG magnifying glass
├── style.css         # Modern CSS styles, layout, and CSS Custom Properties
├── script.js         # Viewfinder tracking, wheel zoom, and threshold math
├── img.jpg           # High-resolution demo image
├── .gitignore        # Git ignore rules for clean repository hygiene
└── README.md         # Comprehensive project documentation
```

---

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/pabitralenka07/Iamge_zoom.git
cd Iamge_zoom
```

### 2. Launch the Application

Since this project uses vanilla web standards, you can run it immediately without building or installing npm packages.

#### Option A: Direct Open in Browser
Double-click `index.html` or open it directly in any modern browser:
```bash
# macOS
open index.html

# Linux
xdg-open index.html

# Windows
start index.html
```

#### Option B: VS Code Live Server
1. Open the folder in [VS Code](https://code.visualstudio.com/).
2. Install the **Live Server** extension (`ritwickdey.LiveServer`).
3. Click **"Go Live"** in the bottom status bar.

#### Option C: Python HTTP Server
```bash
python3 -m http.server 3000
```
Then visit `http://localhost:3000` in your web browser.

---

## ⚙️ Configuration & Customization

### Changing the Image
Update the `IMAGE_PATH` constant in `script.js`:
```javascript
/* -------------------------
   SET YOUR IMAGE HERE
--------------------------*/
const IMAGE_PATH = "your-custom-image.jpg";
```

### Adjusting Zoom Parameters
Customize the minimum, maximum, and step size of the scroll zoom in `script.js`:
```javascript
const CONFIG = {
  SCALE_MIN: 3,   // Minimum zoom scale (default: 3)
  SCALE_MAX: 30,  // Maximum zoom scale (default: 30)
  SCALE_STEP: 1   // Zoom level step per scroll tick (default: 1)
};
```

### Modifying Lens Size & Theme
In `style.css`, modify the `:root` variables to tailor lens dimensions and scale:
```css
:root {
  --viewfinder-scale: 4;        /* Default initial zoom scale */
  --viewfinder-size-scale: 0.5;  /* Lens diameter relative to container */
  --size: 50;                  /* Base size factor */
}
```

---

## 🧠 How It Works (Technical Overview)

1. **Dual Image Architecture**:
   - The primary image (`.zoomer__img`) displays the normal sized image.
   - A cloned high-resolution image (`.zoomer__viewfinder-img`) sits inside a circular masked container (`.zoomer__viewfinder-image-wrapper`).

2. **Mathematical Coordinate Synchronization**:
   ```javascript
   const xPercent = ((x - left) / width) * 100;
   const yPercent = ((y - top) / height) * 100;
   
   const threshold = 50 - 50 / STATE.SCALE;
   const setX = Math.min(Math.max(-threshold, xTranslation), threshold);
   const setY = Math.min(Math.max(-threshold, yTranslation), threshold);
   ```
   The script computes the cursor's percentage position relative to the image bounding box, mirrors the offset, and clamps it to a dynamic threshold proportional to the active zoom level.

3. **CSS Custom Properties & GPU Offloading**:
   - Offset updates pass directly to CSS variables (`--x`, `--y`) on the viewfinder elements.
   - The transforms utilize `translate()` and `scale()` to ensure fluid 60fps animations powered by GPU hardware acceleration.

4. **Event Management for Performance**:
   - `pointermove` and `wheel` listeners are registered on entry (`start()`) and dynamically deregistered on exit (`stop()`), conserving system resources when idle.

---

## 🌐 Browser Compatibility

| Chrome | Firefox | Safari | Edge | Opera |
| :---: | :---: | :---: | :---: | :---: |
| ✅ Full | ✅ Full | ✅ Full | ✅ Full | ✅ Full |

---

## 🤝 Contributing

Contributions, issues, and feature suggestions are welcome!

1. Fork the Project (`https://github.com/pabitralenka07/Iamge_zoom/fork`)
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

## 👤 Author

**Pabitra Lenka**
- GitHub: [@pabitralenka07](https://github.com/pabitralenka07)

---

<p align="center">
  Made with ❤️ and pure CSS/JS
</p>
