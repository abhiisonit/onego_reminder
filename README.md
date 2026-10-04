<div align="center">

![Reminders Repository Cover](./repo_cover.jpg)

# Reminders for Android

**Stay on top of your day.**  
A minimalist, distraction-free personal reminder application inspired by Apple Reminders and built natively for Android with **Kotlin** and **Jetpack Compose**.

[![Platform](https://img.shields.io/badge/Platform-Android-3DDC84?style=flat-square&logo=android&logoColor=white)](#)
[![Kotlin](https://img.shields.io/badge/Kotlin-2.0+-7F52FF?style=flat-square&logo=kotlin&logoColor=white)](#)
[![Jetpack Compose](https://img.shields.io/badge/UI-Jetpack%20Compose-4285F4?style=flat-square&logo=jetpackcompose&logoColor=white)](#)
[![Room Database](https://img.shields.io/badge/Persistence-Room%20SQLite-007AFF?style=flat-square)](#)
[![Offline First](https://img.shields.io/badge/Privacy-100%25%20Offline-success?style=flat-square)](#)
[![API](https://img.shields.io/badge/API-26%2B%20(Android%208.0%2B)-orange?style=flat-square)](#)

[Download Latest APK](./reminders.apk) • [Promotional Website](./index.html) • [Features](#-features) • [Architecture](#-architecture--tech-stack) 

</div>

---

## ✨ Overview

**Reminders** is crafted for clarity, speed, and reliability. Instead of bloated productivity dashboards, cloud sign-ups, or subscription walls, it focuses entirely on helping you capture and complete tasks with zero friction.

Every reminder is stored locally on your device using **Room SQLite** and scheduled through Android's native **AlarmManager** so alerts fire on time—even when your phone is idle or restarts.

---

## 🚀 Features

- **🛡️ 100% Offline & Private** — No cloud accounts, no internet permission, no analytics, and zero tracking. Your data never leaves your device.
- **⏰ Exact Time Alerts** — Uses `AlarmManager` (`setExactAndAllowWhileIdle`) with graceful Android 12+ (`SCHEDULE_EXACT_ALARM`) handling to deliver notifications right on schedule.
- **🔄 Smart Repeating Schedules** — Set tasks to repeat **Daily**, **Weekly**, or **Monthly**. When a repeating reminder triggers or is completed, the next occurrence is automatically calculated and scheduled.
- **🔔 Interactive Notifications** — Mark a reminder **Complete** or **Snooze (10m)** directly from the Android notification shade without opening the app.
- **⚡ Survives Device Reboots** — A dedicated `BootReceiver` listens for system startup (`BOOT_COMPLETED`, `LOCKED_BOOT_COMPLETED`, `MY_PACKAGE_REPLACED`) and automatically restores all active alarms.
- **🎨 Minimalist Light & Dark Themes** — Engineered with an iOS-inspired color palette (`#F8F8FA` paper white and `#101010` deep dark mode), crisp typography, and animated circular completion checkboxes.
- **🗂️ Intelligent Grouping** — Automatically organizes active tasks into **Overdue** (with red time accents), **Today**, and **Upcoming** sections, plus a dedicated **Completed** history tab.

---

## 📲 Download & Promotional Landing Page

This repository includes a ready-to-deploy promotional website and pre-built APK inside the [`root`](./) folder:

- **Direct APK File:** [`reminders.apk`](./reminders.apk)
- **Promotional Webpage:** [`index.html`](./index.html)
- 
---

## 🏗️ Architecture & Tech Stack

The project follows **MVVM (Model-View-ViewModel)** and **Clean Architecture** principles with reactive Kotlin `StateFlow` streams:

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **UI Layer** | Jetpack Compose + Material 3 | Declarative UI, custom circular checkboxes, bottom sheets, date/time pickers, edge-to-edge layout |
| **Navigation** | Navigation Compose | Smooth tab switching between **Reminders**, **Completed**, and **Settings** |
| **State Management** | `AndroidViewModel` + `StateFlow` | Reactive categorization into *Overdue*, *Today*, and *Upcoming* lists |
| **Local Persistence** | Room Database (`KSP`) | Offline SQLite storage with `Flow` queries and `RepeatType` converters |
| **Background & Alarms** | `AlarmManager` + `BroadcastReceiver` | Exact alarm scheduling, notification actions (`Complete`, `Snooze 10m`), and boot restoration |

---

## 🔐 Permissions Used

| Permission | Reason |
| :--- | :--- |
| `POST_NOTIFICATIONS` | Displays reminder alerts on Android 13+ (API 33+). Requested gracefully via an in-app banner. |
| `SCHEDULE_EXACT_ALARM` | Ensures reminders trigger at the exact minute selected by the user. |
| `RECEIVE_BOOT_COMPLETED` | Restores scheduled reminder alarms automatically when the device restarts. |

---

## 📄 License

This project is open source and available under the [MIT License](LICENSE).
