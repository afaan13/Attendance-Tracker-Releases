<h1 align="center">Attendence - The Elite School Ecosystem</h1>

<div align="center">
  <img src="https://img.shields.io/badge/Kotlin-0095D5?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin" />
  <img src="https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white" alt="Android" />
  <img src="https://img.shields.io/badge/Jetpack_Compose-4285F4?style=for-the-badge&logo=android&logoColor=white" alt="Jetpack Compose" />
  <img src="https://img.shields.io/badge/Firebase-FFCA28?style=for-the-badge&logo=firebase&logoColor=black" alt="Firebase" />
  <img src="https://img.shields.io/badge/MVVM-Architecture-brightgreen?style=for-the-badge" alt="MVVM Architecture" />
</div>

<br/>

**Attendence** is a professional-grade, high-performance attendance and school management ecosystem designed for modern educational institutions. It provides a seamless, real-time synchronized experience between Principals and Teachers, ensuring data integrity, administrative control, and unparalleled ease of use.

## 🌟 What's New? (Recent Refinements)
We've recently evolved the app to be faster and more professional:
- **Streamlined Onboarding**: Removed the lengthy multi-step tutorial. New users now see a clean, professional "Welcome Gate" with an instant animated transition right into the app.
- **Optimized Synchronization**: Transitioned from heavy, constant real-time listeners to an intelligent, demand-driven sync model. We use local Room caching combined with manual/one-time Firestore fetches to save quotas and eliminate sync conflicts.
- **Advanced Permissions**: Implemented server-side precedence for administrative changes, meaning the Principal's rules are absolute.

## 💎 Elite Subscription Ecosystem
A multi-tiered subscription model tailored for schools of all sizes:
- **Free**: Essential attendance features for small groups.
- **Premium**: Increased limits for classes (up to 30) and students (up to 200), plus custom teacher restrictions.
- **Elite**: 2x capacity of Premium, advanced administrative controls, and school-wide holiday management.
- **Ultimate**: The complete package with unlimited scaling, priority sync, and granular teacher-access policies.

## 🛡️ Advanced Administrative Controls
Principals have total control over the school's digital footprint:
- **Granular Class Visibility**: Restrict class access to "All Teachers", "None", or "Selected Teachers" only.
- **Teacher Restriction System**: Auto-restrict new teachers in Elite/Ultimate schools to prevent unauthorized changes until vetted.
- **Attendance Lock**: Principals can toggle a global attendance lock, preventing any modifications regardless of permissions.
- **Invite Code Management**: Secure teacher onboarding with limited-use invite codes.

## 📅 Intelligent Holiday Management
- **School-Wide Scheduling**: Schedule holidays directly from the Principal dashboard.
- **Real-Time Banner**: Teachers see a prominent holiday banner on scheduled days.
- **Interaction Gating**: Attendance marking is automatically disabled on holidays to maintain record accuracy.

## 🔄 State-of-the-Art Architecture
- **Firestore + Room Synchronization**: Combines the lightning speed of local SQLite (Room) with the reliability of cloud-based Firestore.
- **Offline-First Capabilities**: Mark attendance anywhere; data syncs automatically when a connection is restored.
- **Conflict Resolution**: Robust conflict resolution ensures offline changes don't overwrite crucial administrative locks.

## 🎨 Premium UI/UX Design
- **Modern Aesthetics**: A stunning interface featuring glassmorphism, smooth gradients, and vibrant color palettes.
- **Dynamic Themes & Animations**: Interactive elements with micro-animations for an engaging user experience, including a rapid-entry Welcome Gate.
- **Role-Specific Dashboards**: Tailored, uncluttered views for Principals (Analytics & Controls) and Teachers (Speed & Efficiency).

## 🛠️ Technology Stack
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Database**: Room Persistence Library & Firebase Firestore
- **Concurrency**: Kotlin Coroutines & Flows
- **Architecture**: MVVM with Clean Architecture principles
- **Authentication**: Firebase Auth

## 📦 Installation & Deployment
1. **GitHub Release**: Download the latest signed APK from the [Releases](https://github.com/afaan13/attendance-tracker-releases/releases) page.
2. **Installation**:
   - Sideload the APK onto your Android device.
   - If prompted by Play Protect, select "Install Anyway" (App is signed with a private release key).
   - Sign up as a **Principal** to create a new school, or join an existing school using an **Invite Code**.

## 📄 License & Security
- **Privacy**: All data is encrypted in transit and stored securely on Google Cloud Infrastructure.
- **GDPR Ready**: User data is managed according to strict privacy standards.

---
*Developed with ❤️ for Educators by Afaan.*
