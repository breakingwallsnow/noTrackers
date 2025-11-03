# noTrackers Android App

A privacy-focused Android app that removes tracking parameters from URLs and unwraps redirector links. Features a sleek matte black/silver theme designed for privacy-conscious users.

## Features

- **Share Menu Integration**: Appears in Android share menu for any text/URL content
- **Standalone App**: Can be opened directly from app drawer for manual URL cleaning
- **Comprehensive Tracking Removal**: Removes 100+ tracking parameters across major platforms
- **Redirector Unwrapping**: Automatically extracts real URLs from Facebook, Google, Reddit, LinkedIn, and other redirector services
- **Domain-Specific Rules**: Intelligent parameter filtering that preserves legitimate functionality (e.g., YouTube video IDs, GitHub refs)
- **URL Normalization**: Converts YouTube shorts to watch URLs, normalizes Amazon product links, removes AMP indicators
- **Sleek UI**: Matte black background with silver accents and cyan highlights
- **Privacy-First**: All processing happens locally on your device, no internet required

## How to Build and Install

### Prerequisites

1. **Install Java Development Kit (JDK) 8 or higher**
   - Download from: https://www.oracle.com/java/technologies/downloads/
   - Or use OpenJDK: https://adoptium.net/
   - Make sure JAVA_HOME is set in your environment variables

2. **Install Android Studio**
   - Download from: https://developer.android.com/studio
   - This includes the Android SDK and build tools

### Building the APK

#### Option 1: Using Android Studio (Recommended)
1. Open Android Studio
2. Select "Open an existing Android Studio project"
3. Navigate to this folder and open it
4. Wait for Gradle sync to complete
5. Go to Build → Build Bundle(s) / APK(s) → Build APK(s)
6. The APK will be created in `app/build/outputs/apk/debug/`

#### Option 2: Using Command Line
1. Open Command Prompt or PowerShell in this directory
2. Run: `.\gradlew.bat assembleDebug`
3. The APK will be created in `app/build/outputs/apk/debug/`

### Installing the APK

1. Enable "Unknown sources" or "Install from unknown sources" in your Android device settings
2. Transfer the APK file to your Android device
3. Open the APK file on your device to install
4. Grant necessary permissions when prompted

## How to Use

### Via Share Menu
1. When you want to share a URL from any app (browser, social media, etc.)
2. Tap the "Share" button
3. Select "noTrackers" from the share menu
4. The app automatically cleans the URL and displays it
5. Use the **Copy** or **Share** buttons to use the cleaned URL

### Standalone Mode
1. Open noTrackers from your app drawer
2. Paste or enter a URL in the input field
3. Tap "Secure my privacy" to clean the URL
4. Use the refresh button to clear and start over

### Additional Options
- **Copy URL**: Copy the cleaned URL to clipboard
- **Share**: Share the cleaned URL with optional promotional text
- **Report Error**: Send feedback if a URL wasn't cleaned correctly

## Supported Tracking Parameters

The app removes tracking parameters using comprehensive global and domain-specific rules:

### Global Parameters (All Sites)
- Google Analytics: `utm_*` variants, `_ga`, `ga_*`
- Facebook: `fbclid`, `fb_*`, `_fb`
- Google Ads: `gclid`, `dclid`, `gbraid`, `wbraid`
- Microsoft: `msclkid`
- Twitter/X: `twclid`
- TikTok: `ttclid`
- Instagram: `igshid`, `ig_rid`
- Mailchimp: `mc_cid`, `mc_eid`
- HubSpot: `_hsenc`, `_hsmi`, `hs_*`
- And 50+ more tracking parameters

### Domain-Specific Rules
- **YouTube**: Removes tracking while preserving video IDs, timestamps, playlists
- **Instagram**: Removes tracking, cleans trailing slashes
- **Amazon**: Removes affiliate tags while preserving product identifiers
- **GitHub/GitLab**: Preserves `ref` and `at` parameters (functional for repos)
- **News Sites**: Removes tracking while preserving article links
- **And 20+ more platforms** with intelligent parameter handling

### Redirector Unwrapping
Automatically extracts real URLs from:
- Facebook (`l.facebook.com`, `lm.facebook.com`)
- Google (`google.com/url`, `google.com/imgres`)
- Reddit (`out.reddit.com`)
- LinkedIn (`lnkd.in`, safety redirects)
- Medium, Hacker News, DuckDuckGo, Slack, and mail/newsletter redirectors

## Project Structure

```
noTrackers/
├── app/
│   ├── src/main/
│   │   ├── AndroidManifest.xml   # App configuration and intents
│   │   ├── java/com/notrackers/app/
│   │   │   ├── MainActivity.java # Main activity and UI logic
│   │   │   └── UrlCleaner.java  # Core URL cleaning engine
│   │   └── res/
│   │       ├── layout/
│   │       │   └── activity_main.xml # UI layout
│   │       ├── values/
│   │       │   ├── colors.xml    # Theme color definitions
│   │       │   └── strings.xml   # App strings
│   │       └── drawable/         # Theme drawables (buttons, backgrounds)
│   ├── build.gradle              # App-level build configuration
│   └── proguard-rules.pro       # Code obfuscation rules
├── build.gradle                 # Project-level build configuration
├── settings.gradle              # Project settings
├── gradle.properties            # Gradle properties
├── THEME_README.md              # Theme documentation for reuse
└── gradlew.bat                  # Gradle wrapper for Windows
```

## Customization

Tracking parameter removal is handled by the `UrlCleaner` class, which supports comprehensive global and domain-specific rules. Modify `UrlCleaner.java` to customize tracking parameter removal behavior.

## Privacy

This app:
- Does not collect any data
- Does not require internet access
- Processes URLs locally on your device
- Only removes tracking parameters, preserving the core URL functionality

## License

MIT License

Copyright (c) 2024 noTrackers

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.