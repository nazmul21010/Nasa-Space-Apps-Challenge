# VITALS — Astronaut Health Monitor

**An intelligent decision-support dashboard for astronaut health monitoring during long-duration space missions.**

Built for the **2026 NASA Space Apps Challenge**  
**Challenge:** Create Health Monitoring Software for Astronauts on Space Missions

**Team:** QuantumBytes  
**Location:** Cumilla, Bangladesh

---

##  Overview

Long-duration space missions expose astronauts to several health risks, including radiation exposure, bone density loss, cardiovascular deconditioning, immune system changes, sleep deficiency, and psychological stress.

**VITALS** is a health-monitoring dashboard designed to help astronauts and mission support teams understand health indicators, recognize potential risks, and take timely action.

By combining vital telemetry, mission scenarios, risk alerts, and health history in one interface, VITALS transforms raw monitoring data into an understandable, action-oriented view of astronaut wellbeing.

> **Our mission:** Monitor astronaut health, identify potential risks early, and support informed decisions during space exploration.

##  The Challenge

Astronauts on long-duration missions need an effective way to identify changes in their physical and behavioral health before minor issues become serious.

VITALS addresses this challenge by providing a centralized dashboard to:

- Monitor essential health indicators.
- Identify elevated health and mission risks.
- Understand why specific indicators matter.
- Generate prioritized alerts.
- Record responses and flight-surgeon notes.
- Review mission health trends over time.

##  Key Features

### 1. Mission Health Overview

Provides an at-a-glance summary of astronaut wellbeing across four major health categories:

- **Bone Health:** Supports awareness of bone density and exercise-related risks.
- **Cardiovascular Health:** Tracks vital signs and cardiovascular indicators.
- **Immune Health:** Highlights immune-related monitoring considerations.
- **Behavioral Health:** Helps review sleep, stress, and mood indicators.

### 2. Vital Telemetry Monitoring

Displays essential health and mission telemetry, including:

- Heart rate (HR)
- Blood oxygen saturation (SpO₂)
- Body temperature
- Radiation dose
- Sleep duration
- Exercise activity
- Mood indicators

### 3. Radiation Risk Monitoring

Tracks cumulative radiation exposure separately from routine vital signs.

Features include:

- Career radiation dose tracking.
- Configurable threshold comparisons.
- Elevated extravehicular activity (EVA) risk indicators.
- Radiation-event scenario simulation.
- Action-oriented warnings for mission personnel.

### 4. Intelligent Mission Alerts

Generates prioritized alerts based on simulated or imported mission data.

Alert-management features include:

- Risk prioritization.
- Alert status tracking.
- Recommended follow-up actions.
- Flight-surgeon notes.
- Recording and escalation of responses.

### 5. Mission Scenario Simulation

VITALS includes three scenario modes for testing the dashboard:

| Scenario | Purpose |
|---|---|
| Nominal Cruise | Represents routine mission monitoring. |
| Radiation Event | Demonstrates elevated radiation-risk alerts. |
| Sleep & Stress Risk | Illustrates potential behavioral health concerns. |

### 6. Mission Timeline and Replay

Simulates day-by-day mission progression and supports reviewing:

- Historical health indicators.
- Mission milestones.
- Changes in health telemetry.
- Scenario progression.
- Previous simulated mission states.

### 7. CSV Telemetry Import

Users can import telemetry data from CSV files using the following format:

```csv
day,hr,spo2,temp,rad,sleep,exercise,mood
1,72,98,36.8,0.4,7.5,60,8
2,76,97,36.9,0.5,7.0,55,7
3,81,96,37.0,0.7,6.0,40,6
```

**Supported columns:**

| Column | Description |
|---|---|
| `day` | Mission day |
| `hr` | Heart rate |
| `spo2` | Blood oxygen saturation |
| `temp` | Body temperature |
| `rad` | Radiation dose value |
| `sleep` | Sleep duration |
| `exercise` | Exercise activity value |
| `mood` | Mood indicator |

The values above are illustrative sample data, not validated astronaut measurements. Ensure that uploaded data uses the units and value ranges expected by the application.

### 8. Crew Support and Communication

The platform also provides:

- Mission-role support.
- Crew communications.
- A crew-facing health assistant.
- Shareable mission health reports.
- Documentation of health-related actions.

### 9. Offline-First Operation

VITALS can operate without a configured MySQL database.

In offline-first mode:

- The dashboard remains accessible.
- Local mission simulation remains available.
- Database-backed features are unavailable.
- Shared persistent data and cross-user real-time synchronization require a working database connection.

### 10. Collaborative Data and Real-Time Updates

When MySQL is configured, the backend supports persistent data and Server-Sent Events (SSE) for real-time updates.

This enables a foundation for collaboration between crew members and mission support personnel.

---

## 🛠️ Technology Stack

| Component | Technology |
|---|---|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Backend | Node.js |
| Web Framework | Express.js |
| Database | MySQL 8+ (optional) |
| Database Driver | mysql2 |
| Real-Time Updates | Server-Sent Events (SSE) |
| Data Import | CSV |
| Deployment | Render Web Services |

##  Project Structure

```text
VITALS/
├── assets/          # Visual assets
├── vitals.html      # Dashboard UI and client-side simulation
├── server.js        # Express API, persistence, and SSE
├── schema.sql       # Database schema reference
├── package.json     # Project scripts and dependencies
├── package-lock.json
├── .env             # Local environment variables (not committed)
├── .gitignore       # Excludes secrets and unnecessary files
└── README.md        # Project documentation
```

*The exact file list may vary depending on your repository.*

---

## ⚙️ Getting Started

### Prerequisites

Install the following software:

- [Node.js 18 or newer](https://nodejs.org/)
- npm, included with Node.js
- [MySQL 8+](https://dev.mysql.com/downloads/) — optional for local offline-first operation

### 1. Clone the Repository

```bash
git clone YOUR_GITHUB_REPOSITORY_URL
cd YOUR_PROJECT_FOLDER
```

Replace the example placeholders with your actual repository URL and project directory.

### 2. Install Dependencies

```bash
npm install
```

### 3. Start the Application

```bash
npm start
```

### 4. Open the Dashboard

Visit the following address in your browser:

**http://localhost:3000**

If MySQL is not running or configured, VITALS is designed to fall back to offline-first mode.

---

##  Optional MySQL Configuration

To enable database-backed persistence and collaboration, configure a local `.env` file in the project root.

```env
PORT=3000
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=your_password
DB_NAME=vitals_db
```

Replace the example credentials with your local database configuration.

The server creates the required database tables when it successfully connects, according to the implemented initialization logic.

**Security recommendations:**

- Never commit `.env` to GitHub.
- Never expose database credentials in frontend JavaScript.
- Use environment variables for production secrets.
- Use a dedicated database account with restricted privileges.
- Validate imported CSV data on the server where applicable.

If MySQL is unavailable, database-backed endpoints will not work even though the local dashboard and supported simulations remain usable.

---

##  Deployment on Render

VITALS can be deployed as a Render Web Service.

1. Push the project to GitHub.
2. Sign in to [Render](https://render.com/).
3. Create a new **Web Service** and connect your repository.
4. Configure the deployment settings.

| Setting | Value |
|---|---|
| Build Command | `npm install` |
| Start Command | `npm start` |
| Health Check Path | `/api/health` |

5. Add the required database environment variables in Render if using a hosted MySQL instance.
6. Deploy the application.
7. Test the dashboard and health-check endpoint.

**Live Demo:** Coming soon — add the deployed URL here after successful deployment.

**Note:** Confirm that `/api/health` exists in `server.js` and that your selected hosting and database providers are configured correctly before submitting the project.

---

##  Data Sources and Scientific Inspiration

VITALS is inspired by publicly available NASA research and spaceflight health research.

### NASA Open Science Data Repository (OSDR)

The [NASA Open Science Data Repository](https://osdr.nasa.gov/) provides access to biological and biomedical research datasets relevant to spaceflight.

The project references the following studies as research context:

- OSD-575
- OSD-656
- Research associated with the Inspiration4 mission

### NASA Human Research Program

The [NASA Human Research Program](https://www.nasa.gov/hrp/) investigates health and performance risks associated with human spaceflight.

Relevant research areas include:

- Space radiation exposure.
- Bone and muscle loss.
- Cardiovascular changes.
- Sleep and circadian disruption.
- Behavioral health and psychological adaptation.
- Immune system changes.

These sources inform the project's design concepts. Their mention does not imply that every dashboard indicator, threshold, or alert has been clinically validated against the cited studies.

---

##  Evaluation and Demonstration

VITALS can be demonstrated through controlled scenarios:

1. **Nominal Cruise:** Review baseline telemetry and mission health indicators.
2. **Radiation Event:** Simulate elevated radiation exposure and observe the resulting warnings.
3. **Sleep & Stress Risk:** Simulate changes in sleep and mood indicators.
4. **CSV Import:** Import sample telemetry and review the displayed values.
5. **Alert Management:** Review alerts, update their statuses, and record notes.
6. **Mission Replay:** Examine simulated changes across mission days.
7. **Database Mode:** Verify persistence and real-time updates when MySQL is configured.

Evaluation should distinguish between software functionality, the consistency of simulated alerts, and actual medical prediction performance. A successful simulation does not establish clinical accuracy.

---

## 👥 Team QuantumBytes

| Team Member | Role |
|---|---|
| Noor Hossain | Team Leader, Developer, and System Architect |
| Bijoy Kumar Ray | Developer and Security Lead |
| Samiya Anzuman | Documentation Lead |
| MD. Nazmul Islam Hridoy | Researcher |
| Tanjil Al-Nayeef | QA Lead |

**NASA Space Apps Challenge Location:** Cumilla, Bangladesh

---

##  Disclaimer

VITALS is a hackathon prototype and educational decision-support interface.

It is **not a medical device** and must not be used for clinical diagnosis, treatment, or autonomous medical decision-making.

The dashboard's simulated values, thresholds, scenarios, and alerts are not substitutes for validated medical monitoring systems, professional clinical judgment, or official mission radiation-safety procedures.

---

##  License

No license has been selected yet.

Before publishing the project for reuse, choose a suitable open-source license. The [MIT License](https://opensource.org/license/mit) is one common option for hackathon projects.

If you select MIT, add a `LICENSE` file containing the appropriate license text and copyright attribution.

---

##  Acknowledgments

We acknowledge NASA's publicly available spaceflight research resources and the NASA Space Apps Challenge for inspiring us to explore practical solutions for astronaut health monitoring.

**VITALS — Turning Mission Health Data into Actionable Awareness.**

Built with curiosity, collaboration, and a vision for safer human space exploration. 🚀
