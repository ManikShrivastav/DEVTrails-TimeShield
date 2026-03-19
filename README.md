<div align="center">
  
  # 🛡️ TimeShield
  **AI-Powered Parametric Insurance for the Indian Gig Economy**
  
  [![Hackathon](https://img.shields.io/badge/DEVTrails_2026-Hackathon_Submission-blue?style=for-the-badge&logo=devpost)](#)
  [![Platform](https://img.shields.io/badge/Platform-React_Native-61DAFB?style=for-the-badge&logo=react)](#)
  [![AI/ML](https://img.shields.io/badge/AI_Engine-XGBoost_%7C_Isolation_Forest-FF9900?style=for-the-badge&logo=scikitlearn)](#)
  [![Status](https://img.shields.io/badge/Status-In_Development-success?style=for-the-badge)](#)

  *Built with ❤️ for the delivery heroes of India.*

</div>

---

## 💡 The First Principle

> **We do not insure physical assets or health; we insure a worker's time and their ability to earn.**

**TimeShield** is a dynamic, zero-touch parametric insurance platform. When external disruptions—extreme weather, social unrest, or tech outages—paralyze a gig worker's operations, TimeShield automatically detects the event and instantly triggers a payout for lost wages. 
**No human adjusters. No complex claims. Zero friction.**

---

## 🎯 Target Persona & Coverage Scope

### The Persona: Q-Commerce Delivery Partner
We focus exclusively on the Q-Commerce sector (e.g., Zepto, Blinkit, Swiggy Instamart). Their business relies on **10-minute SLAs**. Their risk is highly volatile, fluctuating based on hyper-local geography, weather, and civic conditions. Even minor external disruptions instantly halt their operations, making their lost income immediate, verifiable, and perfect for parametric triggers.

### 🛑 Strict Coverage Constraints
* **INCLUDED:** Loss of income specifically due to external disruptions.
* **EXCLUDED:** Health, life, accidents, or vehicle repair coverage.
* **MODEL:** Week-to-week dynamic micro-premiums calculated by AI.

---

## 🏍️ Real-World Scenarios (Meet Raju)
*Raju is a Q-commerce rider operating in South Delhi. Here is how TimeShield protects his time:*

1. 🌧️ **Hyper-Local Waterlogging:** A sudden severe downpour (>65mm/hr) paired with gridlock traffic (<5 km/h) hits Raju's geofenced zone. Delivering in 10 minutes is physically impossible. The platform halts orders for 2 hours. *TimeShield auto-detects the anomaly and pays Raju for 2 lost hours.*
2. 📵 **Telecom Shutdown (Civic Disruption):** Due to local unrest, the government suspends mobile internet. Without 4G, Raju's app is dead. *TimeShield's edge-computing logs his location offline and triggers a retrospective payout once connectivity is restored.*
3. 💥 **Global App Crash:** The Q-Commerce platform's servers go down nationally for 3 hours. Raju is on his bike, the weather is perfect, but he cannot receive orders. *TimeShield's platform monitor detects the outage and issues a payout.*

---

## ⚙️ System Architecture & Workflow

TimeShield operates silently in the background, minimizing friction for the worker:

1. **📲 Frictionless Onboarding:** Rider logs in via SSO. The system analyzes their historical earning data to establish a baseline **Average Hourly Wage**.
2. **🤖 Automated Weekly Policy:** Every Sunday at 11:59 PM, the AI evaluates the upcoming 7-day risk for the rider's specific pincode and deducts a micro-premium from their wallet.
3. **📡 Active Parametric Polling:** The backend continuously polls Weather, Traffic, and Platform APIs every 15 minutes.
4. **🛡️ Trigger & Fraud Validation:** When an event threshold is breached, the system runs anomaly detection for GPS spoofing and cross-references platform activity.
5. **💸 Zero-Touch Payout:** Once validated, `Lost Hours × Average Hourly Wage` is instantly routed to the worker via a simulated payment gateway (UPI).

---

## 🧠 The AI Engine & Mathematical Model

### 1. Dynamic Weekly Premium Model (XGBoost)
Every Sunday, our ML Risk Model evaluates the 7-day forecast for a worker's specific pin code. It calculates a dynamic weekly premium based on the probability of disruptions:

```math
Pw = Σ [ α·P(Wd) + β·P(Sd) + γ·P(Td) ] × µ_hourly × H_expected
