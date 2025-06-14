# 🔌 JBus Interface (JBI) – VLSI Physical Design Project (RTL to GDSII)

## 🔧 Tools Used
- **Synopsys Design Compiler** – RTL Synthesis  
- **Synopsys IC Compiler II (ICC2)** – Floorplan, Placement, CTS, Routing  
- **Synopsys PrimeTime (pt_shell)** – Static Timing Analysis (STA)  
- **Technology Node**: 14nm standard cell library  

---

## 📘 Project Description
The **JBus Interface (JBI)** project is a complex physical design implementation done using **14nm technology**, integrating a large number of macros (**84**) and operating with two clock domains:
- `cmp_gclk` at **1.1 GHz**  
- `jbus_gclk` at **0.9 GHz**  

The design reflects extensive multi-clock domain handling, aggressive skew and uncertainty optimization, and clean STA closure across all phases. This project highlights strong control over physical constraints, timing budget distribution, and congestion management.

---

## 🛠 Flow Steps

### 1. RTL Synthesis (Design Compiler)
- Synthesized using 10K base standard cells  
- Clock constraints: `cmp_gclk = 1.1 GHz`, `jbus_gclk = 0.9 GHz`
- Transition time:  
  - **Data = T/3**  
  - **Clock = T/6**  
- Max fanout limited to **16**
- Setup Uncertainty:  
  - **30% of clock** applied in synthesis  
- Hold Uncertainty:  
  - **20% of clock**

### 2. Floorplanning (ICC2)
- **84 macros** integrated  
- **50% core utilization**  
- Aspect Ratio: **1.0** (square)  
- IO placement from **left to right**
- Die area: **146770.71 mm²**
- Density: **21.24%**

### 3. Power Planning
- Power stripes and rings inserted based on macro proximity
- Voltage drop analysis ensured reliable power delivery

### 4. Placement
- Cells placed with congestion-aware optimization
- **Horizontal Congestion**: 0.79 (limit ≤ 1)  
- **Vertical Congestion**: 0.71 (limit ≤ 1)
- Final cell count: **35,703**

### 5. Clock Tree Synthesis (CTS)
- NDR applied:  
  - **2x spacing**  
  - **3x width**
- Clock buffers/inverters used: **BUF/INV {4, 6, 8, 10, 12}**
- **Insertion Delay**: 400ps  
- **Target Skew**: 50ps
- Setup uncertainty: **20% of clk**  
- Hold uncertainty: **20% of clk**

### 6. Routing
- Global and detailed routing completed
- Clean DRC  
- No shorts or opens

### 7. Static Timing Analysis (PrimeTime)
- Global timing met in `pt_shell` for both **setup and hold**
- **0 slack, 0 violations** post-route

---

## 📊 Results

| Metric                    | Value                |
|---------------------------|----------------------|
| Technology                | 14nm                 |
| Clock Domains             | cmp_gclk (1.1 GHz), jbus_gclk (0.9 GHz) |
| Standard Cell Count       | 35,703               |
| Macros Integrated         | 86                   |
| Utilization               | 50%                  |
| Aspect Ratio              | 1.0                  |
| IO Placement              | Left to Right        |
| Die Area                  | 146770.71 mm²        |
| Cell Density              | 21.24%               |
| Horizontal Congestion     | 0.79 (within limit)  |
| Vertical Congestion       | 0.71 (within limit)  |
| DRC / LVS                 | Clean                |
| Shorts / Opens            | 0                    |
| Setup Slack               | 0 (Met)              |
| Hold Slack                | 0 (Met)              |
| Total Power – Leakage     | 5.88e+08 pW          |

---

## 📸 Snapshots
*Note: Screenshots not uploaded due to NDA*

- Floorplan with 84 macros and IO across left-to-right
  ![Screenshot 2025-06-13 183934](https://github.com/user-attachments/assets/7572ed7e-5746-448c-8eca-fa1fd1835131)

- Placement view showing balanced utilization
  ![Screenshot 2025-06-13 184337](https://github.com/user-attachments/assets/3f24cb1b-4a7b-45c2-8505-c69ec5e9a495)

- CTS clock tree with NDR applied and 50ps skew
  ![Screenshot 2025-06-13 184621](https://github.com/user-attachments/assets/26907939-96ea-4e3b-a611-639a9127afdb)

- Post-route routing view with metal layer stack around the macros
  ![Screenshot 2025-06-13 185848](https://github.com/user-attachments/assets/5f392c43-0bb9-41c4-83b8-1587ebfc79b2)

- PrimeTime report for multi-clock domain timing closure
  ![Screenshot 2025-06-13 190126](https://github.com/user-attachments/assets/5f75932d-f4d3-465a-9014-e26e076f28b0)
  
  1) Setup - ![Screenshot 2025-06-13 190701](https://github.com/user-attachments/assets/8a1f27cf-1f16-44d0-967b-61be797d92eb)
  2) Hold - ![Screenshot 2025-06-13 190826](https://github.com/user-attachments/assets/1e21eb7d-9ca0-4850-8b43-2dda3e3ad2f2)

- Signoff PV with zero congestion
  ![Screenshot 2025-06-13 190246](https://github.com/user-attachments/assets/8106b54a-14e4-4ec8-b2f2-a56dfa7eff17)

- Opens and shorts DRC - clean
  ![Screenshot 2025-06-13 191353](https://github.com/user-attachments/assets/bc15a98a-dc19-4a3c-b935-f1632c03a85b)


---

## 📌 Notes
- All constraints (transition, fanout, uncertainty) applied consistently across flow  
- Timing closure achieved with zero violations under multi-clock domain STA  
- CTS configured with custom NDR rules for enhanced routing quality  
- All stages executed using scripted Tcl flows under Synopsys environment  
- Reports reviewed and verified manually at each milestone  

---

## 🎯 Purpose
This project demonstrates advanced physical design capabilities involving **multi-clock domains**, **macro-heavy floorplanning**, and **tight clock skew control**.  
It highlights my practical knowledge in managing synthesis, CTS, routing, and STA for a high-complexity design in **14nm node**.  
**JBus Interface** reflects real-world project alignment and tool expertise in industrial-grade chip design.

