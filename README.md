# Smart City Data Collector — Kickoff Presentation

![SMART CITY DATA COLLECTOR](images/image69.jpeg)

Welcome to the **Smart City Data Collector** kickoff presentation for 2026. This repository contains the presentation slides used for briefing students on their journey from designers to hardware hackers and data artists.

## 🚀 Project Overview

The project is divided into four distinct phases that guide students through the entire data lifecycle in an urban environment:

1.  **Phase 1: The Hardware** — Building custom sensor kits using Seeeduino LoRaWAN and Grove sensors (no soldering required).
2.  **Phase 2: The Software** — Utilizing the GLR Configurator to generate low-code firmware and flashing it via the Arduino IDE.
3.  **Phase 3: Fieldwork** — Collecting real-world geospatial data (GPS, light, sound, motion) throughout the city of Rotterdam.
4.  **Phase 4: Data to Design** — Visualizing the captured datasets using tools like **Kepler.gl** or **Adobe After Effects**.

---

## 🛠️ Tech Stack & Setup

This presentation is built using **Marp** (Markdown Presentation Ecosystem) with a custom **Grafisch Lyceum Rotterdam (GLR)** theme.

### Viewing the Presentation
If you are viewing this locally, you can open the pre-rendered [presentation.html](presentation.html) in any web browser.

### Editing the Presentation
To edit the presentation, follow these steps:

1.  **Install Marp for VS Code**: Download and install the [Marp for VS Code Extension](https://marketplace.visualstudio.com/items?itemName=marp-team.marp-vscode).
2.  **Theme Configuration**: Ensure Marp knows about the custom GLR theme. Open your VS Code `settings.json` and add:
    ```json
    "markdown.marp.themes": [
        "https://raw.githubusercontent.com/loos-glr/winterspring-2026-tech-presentation/main/theme.css"
    ]
    ```
    *(Alternatively, use the local `theme.css` in your workspace settings)*.

---

## 📁 Repository Structure

*   [`presentation.md`](presentation.md): The main source file for the kickoff slides.
*   [`presentation.html`](presentation.html): The exported, interactive HTML version of the presentation.
*   [`theme.css`](theme.css): Custom CSS providing the GLR branding and slide layouts (e.g., `title-slide`, `chapter`, `logo-slide`).
*   [`images/`](images/): Assets including background images, sensor photos, and animations.
*   [`template-simple.md`](template-simple.md): A simplified Marp template for future GLR lessons.

---

## 🔗 Resources

*   **GLR Configurator Portal**: [https://loos.sd-lab.nl](https://loos.sd-lab.nl)
*   **Kepler.gl**: For geospatial 3D data mapping.
*   **Marp Documentation**: [marp.app](https://marp.app)

---

© 2026 Grafisch Lyceum Rotterdam — *Invisible Data Made Visible.*