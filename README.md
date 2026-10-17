# JOMAKU — 除幕式

Pull a ceremonial cord to unveil a photo or message in a white studio setting.

**[Open JOMAKU](https://masato-nasu.github.io/JOMAKU/)** · **[MASATO LAB](https://masato-lab.pages.dev/tools/jomaku)** · **[Download the complete ZIP](https://github.com/Masato-Nasu/JOMAKU/raw/refs/heads/main/JOMAKU-complete.zip)**

![JOMAKU ceremony preview](preview.svg)

## Features

- Photographic ceremony scene with a man and woman holding braided red-and-white cords.
- A red velvet cloth deforms under gravity, gathers in front of the plinth, and settles in about two seconds.
- Cords release from the upper attachments and fall with their own motion; gold tassels sway gently.
- Custom heading, message, and optional photo. Portrait photos use a larger frame without cropping faces.
- Bright trumpet fanfare and recorded applause, with a sound toggle.
- Touch drag, mouse, tap, or keyboard controls; reset and repeat.
- Send a photo and message through a short share link; the recipient starts with a closed curtain.
- Shared content is encrypted in the browser and retained for 90 days. Anyone with the complete link can open it.
- Save a commemorative PNG image.
- One self-contained HTML file. No account, build step, or external runtime dependencies.

## Use

1. Open the app and choose **発表内容を設定** to set a heading, message, and optional photo.
2. Drag a cord downward or outward, or press **除幕する**.
3. Press **記念画像を保存** to download a PNG.
4. Press **もう一度 除幕する** to reset the ceremony.

To use a downloaded copy, extract the ZIP and open `JOMAKU/index.html` in a browser. Mobile file preview apps may not execute JavaScript; use a web browser or the hosted app. Content stays on the device until you choose **相手に送る**. Creating a link uploads an encrypted copy, including an optimized photo, for 90 days. The decryption key is carried in the link fragment and is not sent to the storage API. Keep the complete link private to your intended recipients. Links can be opened repeatedly until they expire. Creating and opening share links requires an internet connection.

## Send a ceremony

1. Set your heading, message, and optional photo with **発表内容を設定**.
2. Choose **相手に送る** to create a link.
3. Use **共有する** or **リンクをコピー** to send it through your messaging app.
4. The recipient opens the link and pulls the cord. The recipient view has no edit or send controls.

The public sharing service is at https://jomaku.sunny-seed-0354.chatgpt.site/. Its source, database schema, and migrations are included in [sharing-server-source.zip](sharing-server-source.zip). It uses a D1-backed Vinext app, bounded encrypted payloads, expiration, CORS checks, and per-IP creation limits. There is no public directory of shared ceremonies.

## 日本語

紐を引いて、大げさなくらい丁寧に発表する除幕式アプリです。

赤いベルベットの幕が落ちると、用意した言葉や写真が現れます。新しい作品の発表から、身近な小さな報告まで。文字・写真の変更、音の切替、やり直し、記念画像の保存に対応しています。内容を設定して「相手に送る」を押すと、写真付きの除幕式をURLで送れます。共有リンクは90日間有効で、相手には幕が閉じた状態で届きます。

## Implementation and validation

HTML/CSS/JavaScript with a constrained cloth mesh and independent rope simulation. Velvet texture follows the deforming mesh with WebGL lighting; Canvas2D is a fallback. Contact uses a lightweight approximation rather than full textile self-collision analysis.

Validated in Chromium at desktop, iPhone 13, and Pixel 7 viewport sizes, including emulated touch dragging, photo/text editing, repeated ceremonies, sound decoding and stop behavior, PNG export, and overflow checks. Sharing API tests cover encrypted round trips, expiry, size and origin validation, and creation limits. Physical-device Safari has not been tested.

## Audio credits

Audio files are embedded in the HTML. The trumpet fanfare and applause are CC0 assets; authors, sources, and processing details are listed in [CREDITS.txt](CREDITS.txt). Scene imagery was generated/edited for this app.

## Deploy to GitHub Pages

Publish the `main` branch, root (`/`) folder, from **Settings → Pages**. No build is required.
