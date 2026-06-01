# 📱 Attendence — Elite School Management Ecosystem 🚀

<div align="center">
  <p>
    <img src="https://img.shields.io/badge/Kotlin-0095D5?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin" />
    <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
    <img src="https://img.shields.io/badge/Jetpack_Compose-4285F4?style=for-the-badge&logo=android&logoColor=white" alt="Jetpack Compose" />
    <img src="https://img.shields.io/badge/SQLite_Room-3DDC84?style=for-the-badge&logo=sqlite&logoColor=white" alt="Room SQLite" />
    <img src="https://img.shields.io/badge/Firebase_Firestore-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  </p>
  <p>
    <img src="https://img.shields.io/badge/Architecture-MVVM_Clean_Code-orange?style=flat-square&logo=clean-code" alt="MVVM Architecture" />
    <img src="https://img.shields.io/badge/Database-Offline_First-blue?style=flat-square&logo=sqlite" alt="Offline-First" />
    <img src="https://img.shields.io/badge/Automation-WhatsApp_Accessibility-green?style=flat-square&logo=whatsapp" alt="WhatsApp Automation" />
  </p>
</div>

---

## 📖 Ecosystem Overview

### 💡 What It Is
**Attendence** is an enterprise-grade, offline-first Android application designed to unify school administration, staff, and parents into a single, high-performance digital ecosystem. It replaces traditional paper-based registries with a smart, fully automated system.

### ⚡ How It Works
1. **`[👑 Setup]` Principal Registration:** The school principal registers the institution and generates a secure Invite Code.
2. **`[🧑‍🏫 Onboard]` Teacher Integration:** Teachers join using the Invite Code, accessing their designated classes upon administrative approval.
3. **`[📝 Record]` One-Tap Attendance:** Staff mark student statuses (Present, Absent, Leave, Late) in seconds, even without an active internet connection.
4. **`[🔄 Sync]` Cloud Sync:** Data is preserved locally in Room SQLite and automatically uploaded to Firestore when connection is available.
5. **`[🤖 Notify]` Automatic Dispatch:** Custom PDF reports are generated on-device and instantly sent to parents via WhatsApp automation.

### 🌟 Key Benefits
* **Zero Admin Overhead:** Saves teachers up to 30 minutes daily by eliminating manual entry and report creation.
* **100% Reliable Offline:** Runs seamlessly in environments with poor network connectivity.
* **Instant Parent Trust:** Automatic, visual progress reports sent straight to parents' smartphones.

---

## 🛠️ The Tech Stack

* **`[☕ Kotlin]` Modern Language Base:** Utilizes modern functional patterns, coroutines, and flow APIs for fast, thread-safe asynchronous operations.
* **`[🎨 Jetpack Compose]` Declarative UI:** Pure Kotlin-based modern UI framework ensuring buttery-smooth animations, reusable custom components, and highly responsive states.
* **`[💾 Room SQLite]` Offline-First Database:** Serves as the primary single source of truth, facilitating offline operations, instant querying, and data reliability.
* **`[🔥 Firebase Firestore]` Real-Time Sync:** Scalable cloud storage for cross-device state management and live administrative updates.
* **`[🛡️ Datastore Preferences]` Secure Preferences:** Key-value storage utilizing Flow-based transactions to manage local settings and user subscriptions safely.

---

## 🚀 Core Features & Step-by-Step Use Cases

### 🎭 1. 4-Tier Role-Based Security Matrix
* **Role Tiers:** `Standard Teacher` ➔ `Admin Teacher` ➔ `Incharge Teacher` ➔ `Principal (Owner)`
* **How to use:**
  1. *Join & Set:* A teacher registers with an invite code. The Principal assigns them a specific role.
  2. *Standard View:* Standard Teachers can only take attendance; settings and admin options are hidden.
  3. *Admin/Incharge Powers:* Admins edit profiles, Incharges manage class rosters, and the Principal holds full master control.

### 💳 2. Smart Multi-Plan Queuing & Subscription Safeguards
* **Tiers:** Free Trial (14 days), Premium, Elite, and Ultimate.
* **How to use:**
  1. *Queue Future Purchases:* When a plan is active (e.g. 3-Month Plan), the Principal can purchase another plan (e.g. 1-Year Plan).
  2. *Automatic Rollover:* The next queued plan automatically activates 1 hour prior to expiry, or can be manually activated within 5 days of expiry.
  3. *Graceful Downgrade:* Expiry reverts the school to the Free tier without deleting any data. An alert urges limit adjustments before cloud resources are cleaned up.

### 👁️ 3. Granular Class Access & Roster Controls
* **How to use:**
  1. *Visibility Mode:* Toggle between `OPEN` (all teachers see all classes) and `RESTRICTED` access control.
  2. *Configure Access:* Principal long-presses a class to assign specific teacher rights (View, Take Attendance, Sync, Reports) and restrict access to custom hourly time-windows.
  3. *Natural Sort & Search:* Student rosters automatically cast strings to numbers (`CAST(rollNumber AS INTEGER)`), sorting lists naturally (`1, 2, ... 10` instead of `1, 10, 2`).

### 🏆 4. Gamified Student Performance & Re-ordering
* **How to use:**
  1. *Score Points:* Students earn or lose points based on daily attendance, behavior, and Class Representative (CR) tasks.
  2. *Monthly Roll-Over:* Points reset to `0` at 12:00 AM on the 1st of every month to keep the competition fresh, saving historic tallies.
  3. *Rank-Based Re-ordering:* On the last day of the month, the system proposes a new optimized roll number sequence to the Principal. Upon review, the Principal applies it for the upcoming month.

### 🤖 5. Zero-Touch WhatsApp Accessibility Automation
* **How to use:**
  1. *Select & Generate:* Compile attendance or custom score sheets into beautiful PDF files.
  2. *Trigger Dispatch:* With one tap, the app triggers Android's accessibility service to dispatch the PDFs and report text directly to parents' WhatsApp profiles without manual typing or copy-pasting.

### 🛡️ 6. Enterprise-Grade Audit Logging
* **How to use:**
  1. *Silent Tracking:* Every administrative event, backup, or attendance entry is silently logged locally with high-context hardware and user metadata.
  2. *Principal Inspect:* The Principal opens the master logs screen to search, filter by severity levels (INFO, SUCCESS, ERROR), review device details, and export full logs to CSV.

---

## 📦 Distribution & Privacy Notice

> [!IMPORTANT]
> **This is a highly secure, private repository.** 
> The source code is closed to the public. Distribution is carried out strictly through signed, production-ready **APK files** shared directly with authorized educational institutions.
