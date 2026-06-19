# 🚀 Deep Space AI Terminal — ML Algorithm Visualizer

> An interactive, browser-based visualizer for core Machine Learning algorithms — built with pure HTML, CSS, and JavaScript. No frameworks, no dependencies, no server required.

![Theme](https://img.shields.io/badge/Theme-Deep%20Space%20AI%20Terminal-8B5CF6?style=flat-square)
![Stack](https://img.shields.io/badge/Stack-HTML%20%7C%20CSS%20%7C%20JS-3B82F6?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-22C55E?style=flat-square)

---

## 📸 Overview

This project is a multi-page interactive learning tool that lets you **see machine learning algorithms work in real time**. Add data points to a canvas, tune hyperparameters with live sliders, and watch decision boundaries, regression lines, and loss curves update instantly — all inside your browser.

Built with a **retro-futuristic "Deep Space AI Terminal"** aesthetic — glassmorphism cards, animated particle fields, gradient glow effects, and a deep dark colour palette inspired by Vercel, Linear, and Stripe's dark modes.

---

## 🗂️ Project Structure

```
project/
├── Index.html                   # Landing page & navigation hub
├── regression_visualizer.html   # Regression algorithms visualizer
├── classification_visualizer.html  # Classification algorithms visualizer
└── README.md
```

> **Important:** All three files must be kept in the **same folder** for page navigation to work correctly.

---

## ✨ Features

### 🏠 Index Page
- Animated hero section with live neural network canvas
- Glassmorphism algorithm cards with hover glow effects
- Animated particle field with connection lines
- Floating orb background layers
- Navigation links to Regression and Classification visualizers

### 📈 Regression Visualizer
**Algorithms covered:**
| Algorithm | Key Concept | Penalty |
|---|---|---|
| Linear Regression | OLS — least squares fit | None |
| Polynomial Regression | Basis expansion φ(x) | None |
| Ridge Regression | L2 regularization | λ‖w‖² |
| Lasso Regression | L1 regularization | λ‖w‖₁ |
| Logistic Regression | Binary classification via sigmoid | None |

**Interactive features:**
- Click canvas to add data points
- Drag existing points to reposition them (Move mode)
- Live residual lines showing per-point error
- **Weight Magnitudes bar chart** for Ridge/Lasso — zero weights render as dimmed bars so you can see sparsity live
- **Residual distribution histogram** for Linear/Poly/Logistic
- **Loss curve canvas** showing MSE/cross-entropy over gradient descent iterations
- λ slider for Ridge and Lasso — watch weights shrink in real time
- Polynomial degree selector (2–8)
- Decision threshold τ slider for Logistic
- Live stats bar: R², MSE, slope (w₁), intercept (b)
- 5-stage algorithm walkthrough with equations per algorithm

### 🎯 Classification Visualizer
**Algorithms covered:**
| Algorithm | Boundary Type | Key Idea |
|---|---|---|
| K-Nearest Neighbors | Voronoi tessellation | Majority vote of K closest neighbors |
| Support Vector Machine | Hyperplane (max margin) | Largest margin separator |
| Decision Tree | Axis-aligned rectangles | Recursive Gini/Entropy splitting |
| Random Forest | Ensemble boundary | Bagging + random feature subsets |
| Logistic Regression | Linear hyperplane | Sigmoid + cross-entropy |

**Interactive features:**
- Add up to 3 classes (Class A ●, Class B ▲, Class C ■)
- Click to add points, drag to move them
- **Decision region heatmap** — full canvas colour-coded by predicted class
- Live accuracy %, misclassified point count, boundary type
- Misclassified points highlighted in amber
- Per-algorithm hyperparameter sliders (K, C, max depth, num trees, learning rate)
- Bias / Variance / Interpretability chips per algorithm
- 5-stage algorithm walkthrough with equations per algorithm
- ⊕ Demo button seeds 36 balanced points across 3 clusters

---

## 🎨 Design System

### Colour Palette
| Token | Hex | Usage |
|---|---|---|
| `--bg-deep` | `#030712` | Page background |
| `--bg-dark` | `#0F172A` | Card backgrounds |
| `--blue` | `#3B82F6` | Linear / KNN / forward pass |
| `--purple` | `#8B5CF6` | Ridge / SVM / backward pass |
| `--green` | `#22C55E` | Linear fit line / Class A / logo dot |
| `--orange` | `#F59E0B` | Random Forest / logistic / warnings |
| `--pink` | `#EC4899` | Lasso / misclassified highlights |

### Typography
- **Display:** [Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk) — headings, labels, buttons
- **Code/Mono:** [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) — equations, tags, stats, axis labels

### UI Components
- **Glassmorphism cards** — `backdrop-filter: blur(20px)` + semi-transparent backgrounds + indigo border glow on hover
- **Particle canvas** — 100 drifting dots with proximity connection lines (distance < 90–100px)
- **Animated orbs** — 3 fixed-position blurred radial gradients floating via `translateY` keyframes
- **Mouse glow** — 600×600px radial gradient that follows the cursor
- **Sticky navbar** — darkens on scroll, gradient logo, ghost back button + CTA

---

## 🧮 Algorithms — Technical Details

### Regression
**Linear** — Ordinary Least Squares, gradient descent history logged for loss curve.

**Polynomial** — Vandermonde design matrix `X ∈ ℝⁿˣ⁽ᵈ⁺¹⁾`, solved via Normal Equation `w* = (XᵀX)⁻¹Xᵀy` with LU decomposition. Gradient descent also run for loss history.

**Ridge (L2)** — Closed-form `w* = (XᵀX + λI)⁻¹Xᵀy`. The `+ λI` guarantees invertibility even for singular design matrices. GD run with L2 penalty for loss curve.

**Lasso (L1)** — Coordinate descent with **soft thresholding** operator `S_λ(w) = sign(w)·max(|w|−λ, 0)`. Produces exact zero weights at high λ — visible in the weight bar chart.

**Logistic** — Sigmoid activation + binary cross-entropy loss, gradient descent. Decision boundary at `wx + b = 0`, adjustable threshold τ.

### Classification
**KNN** — Euclidean or Manhattan distance, K-nearest majority vote. Decision regions computed by querying every pixel on the heatmap canvas.

**SVM** — One-vs-rest with gradient descent on hinge loss + L2 regularization. Soft margin controlled by `C`.

**Decision Tree** — Recursive binary splits chosen by Gini impurity reduction. Stops at `maxDepth` or minimum sample count.

**Random Forest** — Bootstrap sampling (with replacement), `√d` random feature subsets per split, aggregated majority vote across T unpruned trees.

**Logistic Regression** — One-vs-rest sigmoid classifiers, gradient descent, cross-entropy loss.

---

## 🚀 Getting Started

### Run locally
No installation needed — just open the files in a browser:

```bash
# Clone or download the project
git clone https://github.com/your-username/deep-space-ai-terminal.git
cd deep-space-ai-terminal

# Open in browser (any method works)
open Index.html
# or
python -m http.server 8080   # then visit http://localhost:8080
```

### Usage workflow
1. Open `Index.html` in any modern browser
2. Click **Explore Regression** or **Explore Classification**
3. Select an algorithm from the pill tabs at the top
4. Click the canvas to add data points (use **Demo** for pre-loaded data)
5. Adjust hyperparameter sliders in the right panel
6. Click **▶ Fit** / **▶ Classify** to run the algorithm
7. Step through the **Algorithm Stages** to read the math behind each phase
8. Click **← Home** in the navbar to return to the landing page

---

## 🌐 Browser Compatibility

| Browser | Support |
|---|---|
| Chrome / Edge 90+ | ✅ Full |
| Firefox 88+ | ✅ Full |
| Safari 14+ | ✅ Full |
| Mobile Chrome / Safari | ✅ Responsive |

> `backdrop-filter` (glassmorphism blur) requires a modern browser. Falls back gracefully to a semi-transparent background.

---

## 📁 File Size

| File | Size (approx.) |
|---|---|
| `Index.html` | ~65 KB |
| `regression_visualizer.html` | ~55 KB |
| `classification_visualizer.html` | ~60 KB |

All assets (fonts) are loaded from Google Fonts CDN. No local assets required.

---

## 🔮 Potential Extensions

- [ ] Add **Neural Network** visualizer with backpropagation animation
- [ ] Add **k-Means Clustering** and **DBSCAN** unsupervised visualizer
- [ ] Add **cross-validation** split view for bias-variance demonstration
- [ ] Export trained model weights as JSON
- [ ] Add dataset presets (moons, circles, XOR, blobs)
- [ ] Mobile touch support for drag interactions

---

## 👤 Author

**Vansh** ([@i-vansh-codes](https://github.com/i-vansh-codes))
B.Tech AI & ML — Ambala College of Engineering and Applied Research
Kurukshetra University

---

## 📄 License

This project is open source under the [MIT License](LICENSE).

---

> *"Real AI startup product, built at 3am in a server room."*
