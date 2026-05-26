# 📱 Attendence — The Elite School Management Ecosystem 🚀

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

## 📖 Introduction: What is Attendence & How It Works 🏫✨

### 💡 In Simple Words
**Attendence** is a high-performance Android application built to bridge the gap between school administration, teachers, and parents. It completely digitizes the process of taking attendance, scheduling holidays, managing school rosters, and distributing reports. 

Instead of manual registers, sheets, or tedious copy-pasting, **Attendence** works as an automated ecosystem:
1. **`[👑 Admin]` The Principal Sets Up the School:** The Principal registers the school in the app, generating a secure **Invite Code**.
2. **`[🧑‍🏫 Staff]` Teachers Join the Network:** Teachers register using this Invite Code. Once approved by the Principal, they gain instant access to class rosters based on administrative policies.
3. **`[⚡ Fast]` Attendance is Marked in Seconds:** Teachers open their customized dashboard, select a class, and mark attendance (Present, Absent, Late, or on Leave) with one-tap efficiency.
4. **`[💾 Offline]` Data Syncs Silently:** The app is **offline-first**. It works perfectly inside classrooms with poor cell reception. As soon as the device connects to the internet, it silently syncs the data to the cloud.
5. **`[🤖 Robot]` Parents Get Instant Automated Updates:** The app generates gorgeous, professional PDF reports on-device and dispatches them directly to parents' WhatsApp or WhatsApp Business numbers automatically, removing all manual effort from the teacher's day.

---

## 💎 Core Features & Engineering Foundations 🌟🛠️

### 🛡️ Enterprise-Grade Activity & Audit Logging
To ensure maximum accountability, transparency, and operational clarity across the entire school staff, the application includes a comprehensive **real-time logging framework**.
* **Dual-Layer Storage Architecture:**
  * **Local Room Database Cache:** Persists logs on-device so teachers' actions are registered even when offline. Background routines automatically prune the log space to `MAX_LOGS_TO_KEEP = 1000` to prevent local storage bloat.
  * **Cloud Firestore Sync:** When connected, logs are instantly published to Firestore under the school collection (`/schools/{schoolId}/audit_logs/{logId}`).
* **High-Context Metadata Payloads:** Each logged event records:
  * **Traceability:** Level (`INFO`, `SUCCESS`, `WARNING`, `ERROR`, `USER_ACTION`) and Category (`AUTH`, `SYNC`, `ATTENDANCE`, `CLASS`, `STUDENT`, `SYSTEM`, `BACKUP`).
  * **Event Translation:** Natural, human-readable statements translating complex system state transitions for administrative understanding.
  * **User & Device Identity:** Captures the performing teacher's Name, Email, and UID, alongside detailed hardware metrics (`Build.MANUFACTURER`, `Build.MODEL`, and Android version) for hardware forensic auditing.
* **Interactive Administrative Portal:** A custom screen accessible by the Principal with advanced text filtering (search queries matching message contents or internal stack traces), categories, level tags, CSV log exporting, and a safe Room database purging suite.

### 💳 Tiered Subscription Ecosystem & Data Preservation
The application implements a structured, premium billing system with pricing options tailored to school sizes. It supports **four flexible billing durations** (1 Month, 3 Months, 6 Months, 1 Year) with increasing discount rates to offset cloud storage, firestore reads/writes, and server maintenance costs:
* **`[🆓 Free]` Core Attendance Utilities:** Limited to 3 classes, 20 students per class, and basic local operations.
* **`[💎 Premium]` Scale-Up Package (For Departments & Small Schools):** Up to 10 classes, 60 students per class, 5 teachers, batch report exports, and custom initials changes.
  * *Pricing Structure:* 1 Month (₹200) | 3 Months (₹549 - Save ~9%) | 6 Months (₹999 - Save ~17%) | 1 Year (₹1799 - Save ~25%)
* **`[👑 Elite]` Advanced Institutional Suite (For Growing Schools):** Up to 30 classes, 100 students per class, 15 teachers, custom school logo integration, and advanced security configurations.
  * *Pricing Structure:* 1 Month (₹600) | 3 Months (₹1649 - Save ~8%) | 6 Months (₹2999 - Save ~17%) | 1 Year (₹5499 - Save ~24%)
* **`[🌌 Ultimate]` Absolute Capacity (For Large Organizations):** Unlimited classes, students, and teachers, priority Firestore syncing, and direct developer assistance.
  * *Pricing Structure:* 1 Month (₹1200) | 3 Months (₹3299 - Save ~8%) | 6 Months (₹5999 - Save ~17%) | 1 Year (₹10999 - Save ~24%)

#### ⏰ Subscription Warning & Grace Period Protections
To prevent immediate lockouts and safeguard essential records:
* **7-Day Pre-Expiry Warn Banners:** Starting 7 days before subscription end, the Principal's dashboard highlights a yellow warning banner, accompanied by local push notifications for proactive renewal.
* **Non-Destructive Free Downgrade:** Upon subscription expiry, the account shifts to the *Free Plan*. **Importantly, no user data (classes, students, attendance history) is deleted or modified.** All local and cloud records are carefully preserved.
* **Grace Period Warning Card:** An alert card remains active on the settings/billing page. The user is notified that their records are kept intact for a grace period. If they choose to remain on the free plan, they must scale their active usage down to the free tier limits (e.g. deleting excess classes) or renew their plan before the grace period ends, after which excess cloud resources are automatically purged to release cloud storage allocations.
* **Billing System Integration:** Users checkout using a secure Google Play mockup Sandbox purchase sheet simulating Credit Cards, UPI, and Google Pay, writing transactional states instantly to Cloud Firestore. Refer to [play_billing_setup_guide.md](file:///C:/Users/Afaan/.gemini/antigravity-ide/brain/c3a8468a-3424-4e71-aa1c-cdfd680d0df3/play_billing_setup_guide.md) for Google Play Console integration instructions.

### 🎭 4-Tier Teacher Permissions & Authorization Matrix
To enforce professional administrative standards, the application implements a strict **4-Tier security model** that dynamically alters the UI visibility, bottom navigation tabs, settings options, and route accessibility based on the logged-in teacher's role:
* **`[🧑‍🏫 Standard]` Standard Teacher:** Scope is strictly confined to taking and marking attendance. 
  * **Complete Redirection & Isolation:** The *Principal Dashboard* bottom navigation tab and the *School Access* (invite code) settings menu are completely hidden. If a Standard teacher attempts to deep-link or navigate directly to restricted pages, an automated navigation interceptor immediately reroutes them back to the Day View screen.
* **`[⚡ Admin]` Admin Teacher:** Intermediate operational access.
  * **Capability:** Can take attendance, add new student profiles to rosters, and edit student profile details.
  * **Restriction:** Strictly prohibited from deleting students.
* **`[🔥 Incharge]` Incharge Teacher:** High-level supervisor class permissions.
  * **Capability:** Inherits all Admin capabilities. Can also add and delete students directly inside the **Manage Classes** roster view.
  * **Control:** Granted access to configure and adjust the *Monthly Score Limit* via the class settings menu.
* **`[👑 Principal]` Principal (The Boss):** Master administrative control.
  * **Capability:** Holds complete oversight of school operations, including approval of registered staff, database backups/restores, central holiday scheduling, and comprehensive audit logs.
  * **Accidental Deletion Safeguard:** To prevent accidental deletion of students from the analytical screens, the Principal Dashboard's master student registry completely hides student delete options. Student deletion is exclusively allowed within the permitted teacher's **Manage Students / Class Roster** view.

### 👥 Robust Class & Student Registry
* **`[🏫 Streamlined]` Dynamic Class Allocation:** Create classrooms, assign division streams, and populate them with detailed student profiles (including Roll Number, Name, Parent Name, and Phone Number).
* **`[🎓 Leadership]` Class Representative (CR) System:** Designate specific students as Class Representatives to assist teachers in organizing daily class operations. CRs are highlighted with dynamic visual badges and specialized scoring mechanisms embedded directly into the attendance matrix.
* **`[👁️ Privacy]` Granular Class Visibility System:** Principals have full control over which teachers can view and access each class through:
  * **School-Wide Visibility Modes:** Toggle between OPEN (all teachers can see all classes) and RESTRICTED (per-teacher permissions apply) from the Principal Dashboard.
  * **Per-Teacher Class Access:** Long-press any class, enter the Access section, and toggle individual teacher permissions including "Can View Class," "Can Take Attendance," "Can Sync," and "Can Generate Reports."
  * **Time-Window Scheduling:** Set allowed access hours (start/end time) per teacher per class — teachers only see the class during their designated time window.
  * **Real-Time Enforcement:** When a principal revokes a teacher's "Can View" permission, the class immediately disappears from the teacher's Manage Classes section, even if it was previously synced to local storage.
  * **Principal-Only Deletion:** Class deletion is restricted exclusively to principals, preventing accidental removal by administrators.
  * **Access Policy Presets:** Four one-tap policy toggles (Everyone, Academic Staff Only, Hidden, Limited Access) allow quick batch permission configuration per class.
* **`[📝 Professional]` Premium Serif Name Typography:** All student names across the main attendance logs, details summary dialogs, and statistics grids are rendered using high-fidelity `FontFamily.Serif` typography to deliver a formal, elegant, and highly attractive visual representation.
* **`[📊 Real-Time]` Today's Roster Stats Calculations:**
  * Displays a dual-line card format: Student Count on Line 1 and real-time attendance stats `"Today: P:X, A:Y, L:Z"` on Line 2 immediately after attendance is completed (even partially).
  * Computes stats dynamically by querying and matching the Room database status entries against absolute case-insensitive matches (`Present`, `Absent`, `Leave`), completely resolving old `0` calculation errors.

### 📅 Smart Holiday Calendar & Display Gating
* **Perfect Multi-Device Month Grids:** The holiday calendar month grid uses responsive layout constraints to guarantee that all calendar cells, headers, and navigation keys fit perfectly on any Android screen size (from compact devices to large tablets) without clipping or partial-cell alignments.
* **Interactive Theme Coloring:** Administrators can select custom aesthetic pastel tones when creating new school holidays, which colorize calendar highlight marks, monthly grids, and daily attendance banners.
* **Immutable Attendance Locks:** Active attendance marking is automatically disabled on designated holiday dates, and a beautiful, high-visibility warning banner alerts teachers that school is closed, preserving data integrity.

### 🔄 Advanced Cloud-Caching & Synchronization
* **`[💾 Offline-First]` SQLite (Room DB) Caching:** Local SQLite storage guarantees flawless operations even in completely offline environments.
* **`[📡 Demand-Sync]` Adaptive Data Dispatch:** Replaced heavy, continuous listeners with smart, manual, and delta-based sync actions to conserve battery, reduce data consumption, and minimize Firebase Firestore read/write quota usage.
* **`[⚔️ Safe-Merge]` Conflict Resolution Engine:** Robust transaction management prevents offline changes from overriding administrative locks or newer server-side edits.

---

## 🛡️ Professional Permissions Architecture & Rationale 🔒🧩

From an enterprise Android engineering perspective, maintaining device stability, user privacy, and strict permission compliance is paramount. Below is the technical breakdown of the permissions requested by the **Attendence** app, their implementation architecture, and why they are vital to the ecosystem.

### 1. `android.permission.INTERNET` 🌐
* **Purpose:** Network Socket Creation and API Access.
* **Developer POV Rationale:** 
  To achieve seamless cloud synchronization, the application establishes secure outbound TLS connections to the Firebase Authentication servers (for user sign-in and session retention) and Google Cloud Firestore (for database read/write actions, subscription verification, and holiday updates).
* **Security Implementation:** All web traffic is strictly gated over HTTPS and TLS 1.3, enforced by the app's `networkSecurityConfig` declarations in the manifest.

### 2. `android.permission.ACCESS_NETWORK_STATE` 📶
* **Purpose:** Network Connectivity Monitoring.
* **Developer POV Rationale:** 
  To implement a reliable offline-first database pattern, the app uses a dynamic `NetworkMonitor` observer. By checking the device's transport capabilities (Wi-Fi, Cellular, Ethernet) before launching network requests, the app:
  * Intelligently buffers cloud writes inside the local Room SQLite DB when offline.
  * Avoids wasting CPU and radio power attempting failed connections over high-latency or dead networks, heavily optimizing battery consumption.
  * Automates the background syncing routine immediately upon transition to an active network state.

### 3. `android.permission.BIND_ACCESSIBILITY_SERVICE` 🤖 (The "Attendance Auto-Sender" Service)
* **Purpose:** Automation of Batch PDF Delivery on WhatsApp & WhatsApp Business.
* **Developer POV Rationale & Mechanics:**
  Sending daily or monthly attendance reports to 200+ parents manually is an operational bottleneck for teachers. To solve this, the application registers an Android Accessibility Service (`WhatsAppAutomatorService`).
  
  * **How it Operates:** 
    When the teacher triggers a batch send, the app programmatically parses parent phone numbers and executes implicit `ACTION_SEND` intents containing the student’s custom PDF file URI. The intent targets WhatsApp (`com.whatsapp`) or WhatsApp Business (`com.whatsapp.w4b`).
  * **Event Sniffing & Automation:** 
    The `WhatsAppAutomatorService` listens exclusively to `TYPE_WINDOW_STATE_CHANGED` and `TYPE_WINDOW_CONTENT_CHANGED` accessibility events emanating *only* from the WhatsApp packages.
  * **Node Inspection & Programmatic Clicks:** 
    The service scans the active window's visual tree (`rootInActiveWindow`) to resolve the "Send" button. It utilizes a failsafe hierarchy:
    1. Looks up the button's layout resource IDs directly using `flagReportViewIds` (targeting specific IDs across current WhatsApp updates such as `com.whatsapp:id/send` or `com.whatsapp.w4b:id/send`).
    2. If WhatsApp layout updates obfuscate or modify the ID, the engine performs a recursive node-tree traversal matching nodes by content descriptions or texts containing the localized keyword `"Send"`.
    3. Once resolved, it triggers an `ACTION_CLICK` action on the node, simulating a tap on the user's behalf.
    4. Instantly after dispatch, it issues a `GLOBAL_ACTION_BACK` command to return to the app's queue, proceeding to the next student immediately.

#### 🔒 Security, Trust, and Privacy Safeguards (Accessibility API)
Because the Accessibility API is highly sensitive, the `WhatsAppAutomatorService` has been engineered with strict privacy safeguards:
* **Zero Telemetry / Data Logging:** The service is entirely local. It does **not** write to storage, log chat content, or transmit any analytical data to external servers.
* **Read-Only / Action-Specific:** It never reads user contact lists, message histories, status updates, or incoming chat packets. It is programmed to do exactly **one** thing: locate the Send button of the active package and tap it.
* **Targeted Filtering:** It is tightly scoped via `accessibility_service_config.xml` to ignore all system events other than those originating from `com.whatsapp` and `com.whatsapp.w4b`.
* **Android 13+ Restrictive Sandbox Compliance:** On modern Android versions (Android 13, 14+), the OS implements a "Restricted Settings" sandbox for side-loaded apps utilizing accessibility services. The app includes built-in guidance, directing the administrator/teacher to open App Info, click the top-right options menu, and select **"Allow Restricted Settings"** to authorize the accessibility daemon securely.

---

## 🛠️ Technology Stack & Architecture 📐🧱

* **UI Engine:** Jetpack Compose (Modern declarative UI with a custom HSL palette, dark mode toggles, and animated glassmorphic surfaces).
* **State Management:** MVVM Architecture with Clean Architecture principles (Repositories, Use Cases, ViewModels, and unidirectional State/Event Flows).
* **Database & Persistence:** Room Persistence Library (SQLite local cache) & Firebase Firestore Cloud DB.
* **Asynchronous Concurrency:** Kotlin Coroutines & Flow (for reactive, resource-efficient UI updates).
* **Report Engine:** Android PDF Graphics Canvas.
* **Language:** Kotlin 1.9+ with full Proguard configuration.

---
*Developed with ❤️ to empower modern educators and administrations by Afaan.*
