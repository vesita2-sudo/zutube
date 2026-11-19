# Zutube

**Zutube** is an open-source **HarmonyOS Web wrapper / custom mobile browser** built with HarmonyOS Stage Model (`ArkTS` + `@kit.ArkWeb`), providing a clean, chromeless, full-screen mobile web viewing experience.

---

## Legal Notice, Privacy & Non-Affiliation

1. **Independent HarmonyOS Web Wrapper / Custom Mobile Browser**
   - Zutube is solely a lightweight client-side browser container built on top of the official HarmonyOS `ArkWeb` component.
   - **No Google/YouTube IP or Binaries:** This repository contains **zero copyrighted source code or assets from Google LLC / YouTube**, does **not** use private/proprietary YouTube app APIs, does **not** bypass DRM, and does **not** distribute any Google APK or binary files.
   - **Independent Brand & Icon:** The name **Zutube** (`com.zutube.browser`) and its custom icon are completely independent and are **not affiliated with, endorsed by, or sponsored by Google LLC or YouTube**.

2. **Local-Only Privacy & Sandbox Isolation**
   - **All cookies, login sessions, DOM storage, and browser caches reside strictly inside the local `ArkWeb` sandbox on the user's own device.**
   - Zutube collects **no telemetry**, runs **no analytics**, and sends **no user data or credentials to any intermediate or third-party server**.

3. **Strictly Non-Commercial**
   - Released strictly for personal, educational, and non-commercial use.
   - **No custom ads, sponsored placements, trackers, or monetization SDKs** are included.

4. **"AS IS" Software & User Responsibility**
   - Provided under the [MIT License](./LICENSE) strictly on an **"AS IS"** basis, without warranty of any kind.
   - **End users are solely responsible** for how they use this browser and for complying with the Terms of Service of any website they choose to access.

---

## Features

- **Chromeless Edge-to-Edge UI:** Full-screen `ArkWeb` (`ASYNC_RENDER`, dynamic theme status bar sync, safe-area inset handling, zero address bar clutter).
- **Smooth Media Playback & Controls:** Native `Web` network stack (zero chunk IPC interception), automatic landscape fullscreen rotation, hold-to-2x speed gesture, and vertical swipe fullscreen toggle.
- **Background Audio & Lock-Screen Media Center:** Bridges active `<video>` playback state, duration, artwork, real-time elapsed position, and lock-screen scrubbing (`AVSession` + `AUDIO_PLAYBACK` background task).
- **Client-Side DOM Ad Cleanup:** Hides promoted feed banners/open-app prompts via CSS and skips player ad overlays safely in-page.
- **Deep Link Support:** Handles incoming `youtube.com` / `youtu.be` / `music.youtube.com` links (`ohos.want.action.viewData`) and routes outbound third-party links to the system browser.

---

## Project Structure

```text
Zutube/
├── AppScope/                       # App identity (com.zutube.browser), label ("Zutube"), custom layered icon
├── entry/
│   ├── src/main/
│   │   ├── module.json5            # Permissions (INTERNET, GET_NETWORK_INFO, KEEP_BACKGROUND_RUNNING) & deep links
│   │   └── ets/
│   │       ├── entryability/       # EntryAbility lifecycle, window immersion, deep link Want handling
│   │       ├── pages/              # Index.ets ArkWeb container & media bridge
│   │       └── services/           # DomainRules.ets, AdBlocker.ets, MediaSessionManager.ets
│   └── src/ohosTest/               # Hypium unit tests (FilterRules.test.ets)
├── hvigor/                         # Hvigor wrapper config
├── build-profile.json5             # HarmonyOS SDK 6.0.0(20) / target 6.1.1(24) config
├── LICENSE                         # MIT License ("AS IS" notice)
└── README.md
```

---

## Building from Source

Requires **DevEco Studio** (HarmonyOS SDK 20+, `JAVA_HOME`, `NODE_HOME`, `DEVECO_SDK_HOME`).

```bash
# Install dependencies (first time only)
ohpm install

# Build unsigned .hap package
hvigorw clean assembleHap --no-daemon

# Build ohosTest package
hvigorw --mode module -p module=entry@ohosTest assembleHap --no-daemon
```

The unsigned package is generated at:
`entry/build/default/outputs/default/entry-default-unsigned.hap`

Sign the `.hap` using your own DevEco Studio signing config or device installer before deploying to your HarmonyOS device.

---

## Thông tin bằng tiếng Việt (Tóm tắt)

- **Định vị:** **Zutube** là một **HarmonyOS Web wrapper / custom mobile browser** (trình duyệt di động tùy biến trên nền ArkWeb), hoàn toàn độc lập với Google/YouTube.
- **Không chứa bản quyền hay file nhị phân của Google/YouTube:** Dự án không sao chép mã nguồn APK, không phân phối bất kỳ file nhị phân nào của Google và không dùng tên/biểu tượng YouTube.
- **Riêng tư tuyệt đối tại thiết bị:** Toàn bộ cookie và phiên đăng nhập nằm hoàn toàn cục bộ trong **sandbox ArkWeb trên máy người dùng**, không gửi bất kỳ dữ liệu nào qua server trung gian.
- **Phi thương mại & Không gắn quảng cáo riêng:** Mã nguồn mở miễn phí theo giấy phép [MIT](./LICENSE) dưới dạng **"AS IS"** (không bảo đảm); người dùng tự chịu trách nhiệm khi truy cập và sử dụng theo điều khoản của website đích.
