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
We focus exclusively on the Q-Commerce sector (e.g., Zepto, Blinkit, Swiggy Instamart). Their business relies on **10-minute SLAs**(Service Level Agreements). Their risk is highly volatile, fluctuating based on hyper-local geography, weather, and civic conditions. Even minor external disruptions instantly halt their operations, making their lost income immediate, verifiable, and perfect for parametric triggers.

### 🛑 Strict Coverage Constraints
* **INCLUDED:** Loss of income specifically due to external disruptions.
* **EXCLUDED:** Health, life, accidents, or vehicle repair coverage.
* **MODEL:** Week-to-week dynamic micro-premiums calculated by AI.

---

## 🏍️ Real-World Scenarios (Meet Raju)
*Raju is a Q-commerce rider operating in South Delhi. Here is how TimeShield protects his time:*

1. **Hyper-Local Waterlogging:** A sudden severe downpour (>65mm/hr) paired with gridlock traffic (<5 km/h) hits Raju's geofenced zone. Delivering in 10 minutes is physically impossible. The platform halts orders for 2 hours. *TimeShield auto-detects the anomaly and pays Raju for 2 lost hours.*
2. **Telecom Shutdown (Civic Disruption):** Due to local unrest, the government suspends mobile internet. Without 4G, Raju's app is dead. *TimeShield's edge-computing logs his location offline and triggers a retrospective payout once connectivity is restored.*
3. **Global App Crash:** The Q-Commerce platform's servers go down nationally for 3 hours. Raju is on his bike, the weather is perfect, but he cannot receive orders. *TimeShield's platform monitor detects the outage and issues a payout.*

---

## ⚙️ System Architecture & Workflow

TimeShield operates silently in the background, minimizing friction for the worker:

1. **Frictionless Onboarding:** Rider logs in via SSO(Single Sign-On). The system analyzes their historical earning data to establish a baseline **Average Hourly Wage**.
2. **Automated Weekly Policy:** Every Sunday at 11:59 PM, the AI evaluates the upcoming 7-day risk for the rider's specific pincode and deducts a micro-premium from their wallet.
3. **Active Parametric Polling:** The backend continuously polls Weather, Traffic, and Platform APIs every 15 minutes.
4. **Trigger & Fraud Validation:** When an event threshold is breached, the system runs anomaly detection for GPS spoofing and cross-references platform activity.
5. **Zero-Touch Payout:** Once validated, `Lost Hours × Average Hourly Wage` is instantly routed to the worker via a simulated payment gateway (UPI).

---

## 🧠 The AI Engine & Mathematical Model

### 1. Dynamic Weekly Premium Model (XGBoost)
Every Sunday, our ML Risk Model evaluates the 7-day forecast for a worker's specific pin code. It calculates a dynamic weekly premium based on the probability of disruptions:

```math
Pw = Σ [ α·P(Wd) + β·P(Sd) + γ·P(Td) ] × µ_hourly × H_expected
```
*   `Pw`: Weekly Premium
*   `P(Wd), P(Sd), P(Td)`: Probability of Weather, Social, or Tech disruptions on day *d*.
*   `α, β, γ`: AI-tuned risk weights for the specific pincode.
*   `µ_hourly`: The rider's baseline hourly wage (calculated from historical platform data).
*   `H_expected`: Expected working hours for the week.

### 2. Risk Profiling & Pricing (XGBoost): 
We will utilize a gradient boosting model to predict the likelihood of disruptions based on historical weather data, traffic patterns, and festive calendars per pincode. This dynamically adjusts the α, β, γ risk weights to price the weekly premium fairly.

### 3. Intelligent Fraud Validation (Isolation Forest)
Zero-touch payouts require zero-tolerance for fraud. Our anomaly detection models validate claims through:
*   **Location Verification:** Cross-checks active GPS pings against the disruption zone.
*   **Anti-Spoofing:** Flags physically impossible GPS jumps (detects mock location apps).
*   **Platform Status Check:** Verifies via simulated platform APIs that the worker was "Online" but deliveries inexplicably dropped to zero.

---

## ⚡ The Parametric Trigger Engine

Our background engine polls APIs every 15 minutes to detect objective threshold breaches. If conditions are met, a claim is generated automatically.

| Disruption Type | Trigger Threshold / Mock API Logic | First-Principle Rationale |
| :--- | :--- | :--- |
| 🌧️ **Environmental (Waterlogging)** | `Rainfall > 50mm/hr` AND `Avg_Speed < 5 km/h` | Rain alone doesn't stop work; severe rain + gridlock physically breaks the 10-minute supply chain. |
| 💥 **Tech (App Crash)** | `Platform_Status == "Outage"` for > 30 mins | Worker is active in the correct zone, but the delivery provider's servers have failed them. |
| 📵 **Social (Telecom Shutdown)** | `Internet_Status == "Suspended"` | App stores offline, encrypted GPS pings locally. Syncs retrospectively when 4G is restored to validate and pay the claim. |
| 🚧 **Civic Paralysis (Curfews)** | `AI NLP Threat == CRITICAL` & `Confidence > 0.90` | Uses AI to parse local news/police feeds. Legal/physical barricades make working impossible. |
| 🏭 **Regulatory Halt (Severe AQI)** | `commercial_2W_ban == true` | Triggers when AQI mandates (e.g., GRAP-IV) legally force commercial 2-wheelers off the road. |

### Example Payload: Civic Paralysis Trigger
```json
{
  "zone": "South_Delhi",
  "ai_threat_level": "CRITICAL",
  "event_classification": "Section_144_Curfew",
  "confidence_score": 0.94,
  "source_triggers": ["police_twitter", "local_news_surge"]
}
```

---

## 🛠️ Tech Stack

### Mobile-First Approach
Gig workers manage their livelihoods from a 6-inch screen mounted on a scooter. Our platform is built specifically for this operational constraint.

*   **Frontend (Mobile App):** React Native, Expo, TailwindCSS (NativeWind)
    *   *Why?* True native performance, smooth transitions, and seamless offline-caching capabilities.
*   **Backend & API Engine:** Python (FastAPI)
    *   *Why?* Extremely fast, native support for our Machine Learning models, and excellent for async API polling tasks.
*   **Database & Offline Storage:**
    *   *Cloud:* PostgreSQL (Supabase/Firebase) for transactional integrity.
    *   *Local/Edge:* SQLite / WatermelonDB (Crucial for storing offline GPS pings during internet shutdowns).
*   **AI / Machine Learning:**
    *   *Predictive Risk:* Scikit-Learn (XGBoost)
    *   *Fraud Detection:* Isolation Forests
    *   *Event NLP:* HuggingFace (Zero-shot classification for civic events)
*   **External APIs (Simulated & Real):**
    *   *Weather:* OpenWeatherMap API
    *   *Traffic:* TomTom / Google Maps Traffic API
    *   *Payments:* Razorpay Test API / UPI Deep-linking
*   **DevOps:** Docker, GitHub Actions, Render/Vercel (Backend Hosting).

---

## 📅 Execution Roadmap (6-Week Sprint)

*   **Phase 1 (March 4-20): Ideation & Foundation**
    *   Define exact constraints, mathematical premium models, and parametric triggers.
    *   Finalize system architecture and submit initial Readme/Pitch.
*   **Phase 2 (March 21-April 4): Prototyping the Engine**
    *   Build the dynamic premium calculator (ML Model).
    *   Set up CRON jobs to poll the 3 specific Mock/Public APIs.
    *   Establish the "Zero-Touch" smart contract logic.
*   **Phase 3 (April 5-17): Scale, Polish & Demo**
    *   Integrate Isolation Forest fraud detection.
    *   Build the React Native mobile UI and the Admin dashboard.
    *   Finalize simulated payment gateways and record the final demonstration video.
