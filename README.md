Vehicle Mode Shift Control

**MATLAB | Simulink | Stateflow**

##  Overview

Designed and simulated a vehicle mode management system with longitudinal vehicle dynamics and logic-based speed control. The system allows switching between **ECO, NORMAL, and SPORT** modes using a Stateflow supervisory controller.

---

##  Objective

* Implement mode selection using Stateflow
* Adjust target speed based on selected mode
* Control throttle using speed feedback logic
* Simulate closed-loop vehicle longitudinal dynamics

---

##  System Architecture

### 1️ Vehicle Plant Model

[
m \frac{dv}{dt} = F_{engine} - F_{break} -F_{drag} -F_{roll}
]

* Engine force = Gain × Throttle
* Drag force = 0.5× dragcoeff× b× (Speed)^2
* Braking force = max Torque × Throttle percentage
* Rolling Force = Mass×gravity×Roll_coeff
* Speed obtained using Integrator

---

### 2️ Mode Controller (Stateflow)

```
[mode_cmd == 1] → ECO
[mode_cmd == 2] → NORMAL
[mode_cmd == 3] → SPORT
```

Each mode defines a different:

* Target speed
* Throttle limit

---

### 3️ Speed Logic Controller

```matlab
error = target_speed - vehicle_speed;
throttle = min(max(error/gain, 0), Tmax);
```

* Closed-loop control
* No PID controller used
* Saturation ensures safe throttle limits

---

##  Results

* Stable speed tracking for all modes
* Smooth acceleration response
* Distinct dynamic behavior for ECO/NORMAL/SPORT


---

## 🔧 Concepts Demonstrated

* Model-Based Design
* Supervisory Control (Stateflow)
* Closed-loop speed control
* Modular subsystem design

---


