<p align="center">
  <a href="#Project Sekai Chart Previewer"><strong>English Section</strong></a> | <a href="#プロセカ譜面プリビュー"><strong>日本語セクション</strong></a>
</p>

# Project Sekai Chart Previewer
Project SEKAI-style SUS chart previewer (Web version).

![Preview](docs/preview.jpg)

Supports pure WASM rendering for song charts and Overlay HUD (score/health/combo/PERFECT/intro info card), Unity-style native AP ending animations, local file uploads, and PWA caching.

## Page Routing

- `/`: Home page
- `/upload`: Upload custom chart page
- `/preview`: Preview page
- `/about`: About page

Notes:

- If the URL contains preview parameters such as `sus`, `cfg`, or `config`, it will automatically redirect to `/preview` even if the URL is not `/preview`.

## Feature Overview

- SUS parsing and native WebAssembly rendering
- Synchronization of audio tracks and chart layout (supports `offset`)
- Pure WebAssembly overlay HUD, background generation, and opening information layer
- AP-style ending performance (rendered natively frame-by-frame using Unity animations and particle effects; does not rely on video)
- Optional custom chart info (displays the chart icon, chart title, and chart author below the original song information)
- Local upload of SUS/BGM/song art
- Background brightness adjustment (60%–100%)
- Optional lock screen component display for easy screen recording
- PWA + Service Worker on-demand caching
- High-DPR preview support for mobile devices

## Getting Started

Environment Requirements:

- Node.js 20+
- npm 10+
- Emscripten (`emcc` executable)
- sus2json source code: [watagashi-uni/Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)

Installation and Development:

```bash
npm install
npm run dev
```

Notes:

- For daily integration testing, we recommend using `npm run dev`.
- If you need to verify the WASM output, PWA, Service Worker, or deployment results, first run `npm run build`, then run `npm run preview`.

Production Build and Preview:

```bash
npm run build
npm run preview
```

### sus2json Build Dependencies

`npm run build` compiles `SusToJsonCpp` from [Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)
into WebAssembly for use in browsers. The default directory structure is:

```text
workspace/
├── sekai-mmw-preview-web/
└── Sekai-SUS-Parser/
    └── SusToJsonCpp/
```

You can run the following command in this project directory to set up the source code:

```bash
git clone https://github.com/watagashi-uni/Sekai-SUS-Parser ../Sekai-SUS-Parser
```

If the source code is not in the default location, you can set the `SEKAI_SUS_TO_JSON_ROOT` environment variable to point to the `SusToJsonCpp` directory:

```bash
SEKAI_SUS_TO_JSON_ROOT=/path/to/Sekai-SUS-Parser/SusToJsonCpp npm run build
```

#プロセカ譜面プリビュー
プロジェクトセカイ風のSUS譜面プレビューア（Web版）。

![プレビュー](docs/preview.jpg)

楽曲チャートおよびオーバーレイHUD（スコア／ヘルス／コンボ／PERFECT／イントロ情報カード）の純粋なWASMレンダリング、UnityスタイルのネイティブAPエンディングアニメーション、ローカルファイルのアップロード、PWAキャッシュに対応しています。

## ページルーティング

- `/`: ホームページ
- `/upload`: カスタムチャートアップロードページ
- `/preview`: プレビューページ
- `/about`: についてページ

注記：

- URLに`sus`、`cfg`、`config`などのプレビューパラメータが含まれている場合、URLが`/preview`でなくても自動的に`/preview`にリダイレクトされます。

## 機能概要

- SUSの解析とネイティブWebAssemblyによるレンダリング
- オーディオトラックとチャートレイアウトの同期（`offset`に対応）
- 純粋なWebAssemblyによるオーバーレイHUD、背景生成、および情報レイヤーの表示
- APスタイルのエンディング演出（Unityのアニメーションとパーティクルエフェクトを使用してフレーム単位でネイティブにレンダリング。動画に依存しません）
- オプションのカスタムチャート情報（元の楽曲情報の下に、チャートアイコン、チャートタイトル、チャート作成者を表示）
- SUS/BGM/楽曲アートのローカルアップロード
- 背景の明るさ調整（60%～100%）
- 画面録画を容易にするロック画面コンポーネントの表示（オプション）
- PWA + Service Workerによるオンデマンドキャッシュ
- モバイルデバイス向け高DPRプレビューのサポート

## はじめに

環境要件：

- Node.js 20 以上
- npm 10 以上
- Emscripten（`emcc` 実行ファイル）
- sus2json ソースコード：[watagashi-uni/Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)

インストールと開発:

```bash
npm install
npm run dev
```

注意事項:

- 日常的な統合テストには、`npm run dev`の使用を推奨します。
- WASM出力、PWA、Service Worker、またはデプロイの結果を確認する必要がある場合は、まず`npm run build`を実行し、その後`npm run preview`を実行してください。

本番ビルドとプレビュー:

```bash
npm run build
npm run preview
```

### sus2json のビルド依存関係

`npm run build` は、[Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser) にある `SusToJsonCpp` を
ブラウザで使用できるように WebAssembly にコンパイルします。デフォルトのディレクトリ構造は以下の通りです:

```text
workspace/
├── sekai-mmw-preview-web/
└── Sekai-SUS-Parser/
    └── SusToJsonCpp/
```

このプロジェクトディレクトリで以下のコマンドを実行すると、ソースコードの設定が行えます：

```bash
git clone https://github.com/watagashi-uni/Sekai-SUS-Parser ../Sekai-SUS-Parser
```

ソースコードがデフォルトの場所にある場合は、`SEKAI_SUS_TO_JSON_ROOT` 環境変数を `SusToJsonCpp` ディレクトリを指すように設定できます：

```bash
SEKAI_SUS_TO_JSON_ROOT=/path/to/Sekai-SUS-Parser/SusToJsonCpp npm run build
```
