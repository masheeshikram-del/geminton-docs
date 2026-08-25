---
title: Privacy Policy — Geminton
---

# Privacy Policy — Geminton

Last updated: August 25, 2026

This policy describes how the Geminton mobile application (“App”) handles information when you use it. Geminton is built for gemstone traders to manage inventory, records, media, backups, and related workflows.

Data controller: Mohamed Ikram  
Contact for privacy questions: masheesh.ikram@gmail.com

## Summary

- Local-first: Your gem records, preferences, and most files stay on your device unless you use optional features that send data elsewhere.
- No Geminton account: The App does not require a Geminton login. Geminton does not operate a central server that stores your inventory for you.
- Optional cloud backup: On Android, if you sign in with Google and use backup, backup files are stored in your Google Drive (in an app-specific area), under Google’s terms. On iOS, if you use backup and are signed in to iCloud with iCloud Drive enabled, backup files may be stored in your iCloud Drive under Apple’s terms.
- Certificate and business card scanning: When you scan a certificate or business card image, the image (or encoded image data) may be sent to **Google Gemini** (Gemini Flash 3.5) to suggest fields. If Gemini is unavailable, the App may fall back to **Google Cloud Vision** (OCR). That processing is governed by Google’s policies.
- Exhibition buyer contacts: Booth visitor contact details, business card images, and stone interest records are stored **locally** on your device. They may be included in **exhibition ZIP** files you export and share with colleagues (for example owner ↔ salesman). Geminton does not operate a central server for this data.
- Analytics screen: The App may download public currency exchange rates over the internet to show approximate conversions. Those requests are not used to send your gem list to the rate provider.
- Optional Pro subscription: Some features require a paid subscription. Payment is processed by Google Play or the Apple App Store; Geminton does not receive or store your card or bank details. Subscription status may be checked using RevenueCat (see section 1.7).

## 1. Information the App processes

### 1.1 Information you provide (stored locally)

The App stores information you enter or import, including for example:

- Gem details (type, weight, pricing, buyer and supplier fields, notes, certificate-related information, custom fields, and similar)
- **Exhibition buyer contacts** (for example name, company, phone, email, country, business card photo, and optional OCR text you confirm)
- **Booth stone interests** (for example which stones a visitor asked about, interest level, per-stone comments, exhibition name, and salesman name when logged at a show)
- Photos, videos, documents, and audio you attach to records
- App settings (such as field visibility, dropdown options, section order, filters, and templates)

This data is mainly stored on your device using local storage (including a local database and files on the device).

### 1.2 Files and media on your device

The App accesses files you choose to open or import (for example Excel files, ZIP backups, or images from your gallery or camera). It does not read your whole photo library by itself; it uses the system file or photo picker, or the camera, when you take action.

### 1.3 Optional cloud backup

#### Google Drive (Android)

If you turn on cloud backup and sign in with Google on Android, the App may:

- Upload backup files (for example spreadsheets and/or ZIP archives that may include media) to Google Drive, in storage tied to your Google account for this App.
- List or download backup files you already uploaded, so you can restore your data.

Google handles sign-in and Drive under Google’s Privacy Policy and terms. Geminton does not receive your Google password.

#### iCloud Drive (iOS)

If you use backup on an iPhone or iPad and are signed in to iCloud with iCloud Drive enabled, the App may:

- Upload backup files (for example spreadsheets and/or ZIP archives that may include media) to your iCloud Drive, in an app-specific area tied to your Apple ID.
- Keep a local copy on the device for quick restore when available.
- List or download backup files from iCloud Drive so you can restore your data.

Apple handles iCloud sign-in and storage under Apple’s Privacy Policy and terms. Geminton does not receive your Apple ID password. iCloud backup does not show a separate permission prompt in the App; it relies on your device’s iCloud settings.

### 1.4 Certificate and business card image analysis (Google Gemini and Google Cloud Vision)

When you use certificate capture or scan, or capture a **business card** at an exhibition, the App may send the image (or encoded image data you submit) to Google services to detect text and suggest fields (for example gem/certificate details or contact name, company, phone, and email). Only images you choose to scan through these features are involved.

- **Primary:** The App typically sends the image to **Google Gemini** (Gemini Flash 3.5 vision model) for analysis.
- **Fallback:** If Gemini is unavailable (for example timeout, network error, or missing configuration), the App may use **Google Cloud Vision** for optical character recognition (OCR) and local parsing to suggest fields.

Geminton does not operate these AI or OCR services. How Google processes that content is described in Google’s Gemini, Google Cloud, and Google APIs terms and privacy materials.

### 1.5 Exchange rates (analytics)

The App may download public currency rate data from the internet (for example from publicly hosted data feeds) to convert amounts in analytics views. Those requests are not intended to send your per-stone records to those providers.

Rates may be cached on your device for a period of time to reduce data use.

### 1.6 Other apps and websites (WhatsApp, WeChat, email, browser)

The App can open other apps or websites when you choose (for example to share text, open a link, send an exhibition ZIP, or start a buyer follow-up message). For WhatsApp or WeChat follow-up, the App may pre-fill a phone number or message text you can edit before sending. Geminton does not control those services. Anything you send or post there is covered by their policies.

### 1.7 Pro subscription and payments

Geminton offers a free tier and an optional **Pro** subscription (monthly, auto-renewing).

- **Free trial:** New subscribers may receive a free trial period (for example three months), as shown in the App and in the store listing. After the trial, the subscription renews at the published monthly price unless the user cancels in **Google Play** or **App Store** subscription settings before the trial ends.
- **Payment processing:** All payments are handled by Google or Apple under their privacy policies and terms. Geminton does not process or store payment card or bank details.
- **Subscription status:** The App checks with Google Play and/or the App Store, and may use **RevenueCat, Inc.** as a subscription management service, to determine whether Pro features are active. That process may involve purchase and subscription identifiers linked to your store account or an anonymous app user identifier. Geminton does not receive your full gem inventory as part of billing.
- **Cancellation and refunds:** Manage or cancel subscriptions in your device’s store subscription settings. Uninstalling the App does not cancel billing. Refunds are handled by Google or Apple according to their policies.
- **RevenueCat:** When used, RevenueCat receives subscription and purchase events from the stores to provide entitlement status to the App. See [RevenueCat’s privacy policy](https://www.revenuecat.com/privacy/) for how they handle that data.

### 1.8 Exhibition packages (owner and salesman)

When you use **Exhibition** features, the App can create or read **ZIP packages** on your device that may include gem records, images, templates, **buyer contacts**, **business card images**, and **booth stone interests**.

- **Export:** You choose when to create and share a package (for example with a salesman before a show, or feedback back to the owner after the show). Sharing may use WhatsApp, WeChat, email, or other apps you select.
- **Import:** You choose when to import a package from your device or from a file received through another app.
- **No Geminton cloud:** These packages move between people and devices only through actions you take. Geminton does not receive or store exhibition packages on its own servers.

Treat exhibition packages as **business-sensitive** if they contain visitor contact details or pricing information.

## 2. Permissions

Depending on your device and how you use the App, you may be asked for permissions such as:

- Internet — for currency rates, Google services used by the App (such as Gemini, Cloud Vision, or Drive), iCloud backup on iOS, and general network use.
- Network state — to understand connectivity.
- Camera — for example QR scanning, certificate capture, or photographing business cards at exhibitions.
- Storage or photo library — when you pick or save files through the system.
- Bluetooth (optional) — only if you choose **Print with Niimbot (Bluetooth)** from Gem Library. The App uses Bluetooth to discover and connect to your Niimbot label printer on your device. Geminton does not use Bluetooth for location tracking or advertising.

The exact wording and timing of permission requests are controlled by your operating system.

## 3. Analytics-style features, ads, and diagnostics

- The App can show summaries and charts based on your data on your device. That is not the same as sending your full inventory to a Geminton analytics service.
- The current release of the App does not include third-party advertising software development kits for ads.
- The current release of the App does not use Firebase Analytics or Firebase Crashlytics.

If that changes in a future release, this policy will be updated.

## 4. How long we keep data and how you can remove it

- On your device: Data stays until you delete it in the App (including buyer contacts and booth interests where the App provides delete or edit controls), clear the App’s data, or uninstall the App. Uninstalling usually removes the App’s local data; exact behavior depends on your device.
- Exhibition ZIP files you saved or shared outside the App remain wherever you stored them (for example chat apps or cloud storage) until you delete them there.
- Google Drive: Backups remain until you delete them in Google Drive or through the App’s backup features, according to Google’s rules.
- iCloud Drive: Backups remain until you delete them in the Files app, iCloud Drive, or through the App’s backup features, according to Apple’s rules.
- Exchange rate cache: Stored on the device and may be updated or cleared as the App runs.

## 5. Security

No electronic system is perfectly secure. The App is intended for everyday business use. You should protect your device and your Google or Apple account, and treat backups as sensitive if they contain business or personal information.

## 6. Children

The App is meant for business users and is not aimed at children. If you think information from a child has been collected by mistake, email masheesh.ikram@gmail.com and we will respond appropriately.

## 7. International users

If you use Google, Apple iCloud, or other global services, data may be processed in different countries. See those providers’ policies for details.

## 8. Changes to this policy

We may update this policy when the App or the law changes. When we do, we will change the Last updated date at the top. For important changes, we may also tell you in the App or in release notes.

Questions about this policy: masheesh.ikram@gmail.com

Use of the App is also governed by our [Terms of Use](terms-of-use.html).
