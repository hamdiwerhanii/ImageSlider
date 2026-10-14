# ImageSlider

A lightweight, dependency-free image slider built with plain HTML, CSS and vanilla JavaScript.

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?logo=javascript&logoColor=black)
![No Dependencies](https://img.shields.io/badge/dependencies-none-success)

## Overview

**ImageSlider** is a small front-end practice project that implements a classic image carousel from scratch, without frameworks or libraries. It shows a set of One Piece-themed wallpapers one at a time, with Previous/Next buttons, numbered pagination bullets, and a "Slide # of N" counter.

The project is a learning exercise in core JavaScript concepts. The notes at the top of the HTML file list them:

1. Working with arrays and indexes
2. Walking through the logic scenario
3. Using functions
4. Some ES6 features (for example `Array.from`)
5. Ordering variables and functions
6. Using the console for debugging

## Features

- **Fade transitions:** slides are stacked and cross-fade through a 1-second CSS `opacity` transition.
- **Previous / Next navigation:** buttons step through the slides one at a time.
- **Boundary handling:** the Previous button is disabled on the first slide and the Next button on the last. Disabled buttons are dimmed and show a `no-drop` cursor.
- **Auto-generated pagination:** a numbered bullet list is built in JavaScript from the number of images, so adding or removing an `<img>` updates the pagination automatically.
- **Direct slide access:** clicking a numbered bullet jumps straight to that slide.
- **Slide counter:** an overlay badge shows the current position, for example `Slide #2 of 5`.
- **Active state highlighting:** the current bullet is highlighted in the accent color (`#009688`).

## Tech Stack

| Layer      | Technology                                                       |
| ---------- | ---------------------------------------------------------------- |
| Markup     | HTML5                                                            |
| Styling    | CSS3 (absolute positioning, transitions, floats)                 |
| Logic      | Vanilla JavaScript (DOM API, `Array.from`, `classList`, `data-*`) |
| Build/Deps | None. It is a static site with no build step.                    |

## Project Structure

```
ImageSlider/
├── README.md
└── Create Image Slider/
    ├── CreateImageSlider.html   # Page markup: slider container, images, controls
    ├── CreateImageSlider.css    # Layout, fade transition, buttons and pagination styles
    ├── CreateImageSlider.js     # Slider logic: navigation, pagination, state checks
    └── imgs/                    # Slide images (.jpg / .webp)
```

## Getting Started

### Prerequisites

- Any modern web browser (Chrome, Firefox, Edge, Safari)
- Optional: a static server such as the VS Code **Live Server** extension

### Installation

```bash
git clone https://github.com/hamdiwerhanii/ImageSlider.git
cd ImageSlider
```

### Running the project

You don't need to install or build anything. Pick one of these options:

- **Open directly:** double-click `Create Image Slider/CreateImageSlider.html` to open it in your browser.
- **VS Code Live Server:** right-click `CreateImageSlider.html` and choose **Open with Live Server**.
- **Any static server**, for example:
  ```bash
  npx serve "Create Image Slider"
  ```

## Usage

| Action                      | Result                                  |
| --------------------------- | --------------------------------------- |
| Click **Next**              | Go to the next slide (disabled on the last slide) |
| Click **Previous**          | Go to the previous slide (disabled on the first slide) |
| Click a numbered bullet     | Jump straight to that slide             |

### Adding your own images

1. Put your images in `Create Image Slider/imgs/`.
2. Add one `<img>` tag per image inside `.slider-container` in `CreateImageSlider.html`.

The script counts the images at load time and builds the pagination for them, so you don't need to change any JavaScript.

## How It Works

1. `Array.from(document.querySelectorAll(".slider-container img"))` collects the slides, and `currentSlide` starts at `1`.
2. A `<ul id="pagination-ul">` is created dynamically. It gets one `<li data-index="n">` per slide and is inserted into `#indicators`.
3. Each control (Previous, Next and the bullets) updates `currentSlide` and then calls `theChecker()`.
4. `theChecker()` does four things:
   - updates the "Slide # of N" label
   - clears every `active` class (`removeAllActive()`)
   - marks the current image and bullet as `active`
   - toggles the `disabled` class on Previous and Next at the first and last slide
5. The CSS sets inactive images to `opacity: 0` and `.active` to `opacity: 1`, so the change animates as a fade.

## Roadmap / Possible Improvements

- Make the slider **responsive**. Its width is currently fixed at `800px × 400px`.
- Add **autoplay** with pause-on-hover.
- Support **keyboard navigation** (arrow keys) and **touch/swipe** gestures.
- Use `<button>` elements for the controls, and add descriptive `alt` text to the images for better **accessibility**.
- Offer optional **looping** from the last slide back to the first.
- Replace `var` with `let`/`const` and use `addEventListener` instead of `onclick` properties.

## Contributing

Contributions, issues and suggestions are welcome. To contribute, fork the repository, create a feature branch, and open a pull request.

## License

No license file is currently included; all rights reserved by the author.

The slide images are One Piece fan wallpapers. They are used for demonstration only and belong to their respective copyright holders.

## Author

**Hamdi Werhani**: GitHub [@hamdiwerhanii](https://github.com/hamdiwerhanii)
