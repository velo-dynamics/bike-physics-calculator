# 🚴‍♂️ Interactive Bicycle Physics & Speed Calculator

A responsive, web-based physics model that calculates a cyclist's steady-state forward speed based on their mechanical power output and real-world environmental resistive forces. 

Unlike basic linear calculators, this tool runs a **bisection search numerical solver loop** to isolate exact terminal velocity across fluid environments.

## 🚀 Live Demo
Try out the interactive web application here:
👉 **[Launch Live Bike Physics Calculator](https://github.io)**

---

## 🔬 Mathematical Modeling & Logic

The application models the total power required to maintain a steady speed by factoring in aerodynamic drag, rolling resistance, and gravitational forces:

$$\text{Power Required} = (\text{Drag Force} + \text{Rolling Resistance} + \text{Gravitational Force}) \times \text{Speed}$$

### 💨 1. Dynamic Air Density & Drag
Instead of using a hardcoded air density, the script computes localized air density ($\rho$) dynamically based on ambient temperature inputs using an ideal gas law approximation at standard sea-level pressure ($101,325\text{ Pa}$):

$$\rho = \frac{101325}{287.05 \times (T_{\text{Celsius}} + 273.15)}$$

* **Wind Vectors:** Handles headwind or tailwind velocities, converting km/h inputs into metric airspeed ($m/s$).
* **Aero Profile:** Scales resistance scaling directly against the rider's active Drag Coefficient Area ($C_{d}A$).

### 🛞 2. Surface Rolling Resistance Coefficients ($C_{rr}$)
The calculation maps rolling resistance relative to system mass against material benchmarks:
* **Time Trial (TT) Tires:** $0.004$
* **Standard Road Tires:** $0.005$
* **Gravel Tires:** $0.010$
* **Mountain Bike (MTB) Tires:** $0.015$
* **Custom:** Fully adjustable user-defined coefficient overrides.

### 📐 3. Mass & Gradient Matrix
Combines isolated fields for **Rider Mass** and **Bike Mass** against precise elevation gradients to accurately map geometric slope resistances.

---

## 🛠️ Project Features
- **Real-Time Physics Solver:** Uses a 60-iteration continuous bisection loop (`speedForPower`) to identify true velocity where power inputs perfectly balance external resistance vectors.
- **Dynamic Metrics Output:** Displays outputs simultaneously across multiple standard units ($\text{km/h}$, $\text{mph}$, and power-to-weight ratio in $\text{W/kg}$).
- **Zero Dependencies:** Pure vanilla JavaScript DOM manipulation with instantaneous responsive listeners hooked directly to your browser's render pipeline.

## 🎛️ Code Structure
- **`index.html`** - Responsive control dashboard and slider grid interface.
- **`alpe-dhuez.html`** - Preconfigured high-gradient mountain pass simulation scenario.

---

## 📄 License
This application is open-source and available under the **MIT License**.
