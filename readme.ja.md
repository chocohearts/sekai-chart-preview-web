# sekai-mmw-preview-web

『Project SEKAI』風の譜面プレビューツール（Web版）。

![プレビュー](docs/preview.jpg)

純粋な WASM レンダリングによる譜面とオーバーレイ HUD（スコア／HP／コンボ／PERFECT／オープニング情報カード）、Unity スタイルのネイティブ AP エンディング演出、ローカルファイルのアップロード、PWA キャッシュに対応しています。

## ページルーティング

- `/`：トップページ
- `/upload`：自作譜面アップロードページ
- `/preview`：プレビューページ
- `/about`：についてページ

説明：

- URLに`sus`/`cfg`/`config`などのプレビューパラメータが含まれている場合、`/preview`でなくても自動的に`/preview`にリダイレクトされます。

## 機能概要

- SUS解析とWebAssemblyによるネイティブレンダリング
- 音源と譜面の同期（`offset`対応）
- 純粋な WASM オーバーレイ HUD、背景生成、およびオープニング情報レイヤー
- AP 終了時の演出（Unity のアニメーションとパーティクルエフェクトを用いてネイティブにフレーム単位で描画され、動画に依存しない）
- オプションで自作譜の Info 表示（原曲情報の下に譜面アイコン、譜面タイトル、譜面作者を表示）
- SUS/BGM/曲絵のローカルアップロード
- 背景の明るさ調整（60%～100%）
- 画面録画に便利なロック画面コンポーネントの表示（オプション）
- PWA + Service Worker によるオンデマンドキャッシュ
- モバイル端末の高DPRプレビュー対応

## クイックスタート

環境要件：

- Node.js 20以上
- npm 10以上
- Emscripten（`emcc` 実行ファイル）
- sus2json ソースコード：[watagashi-uni/Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)

インストールと開発：

```bash
npm install
npm run dev
```

説明：

- 日常の連携テストには `npm run dev` の使用を推奨します。
- WASM ビルド結果、PWA、Service Worker、またはデプロイ結果を検証する場合は、まず `npm run build` を実行してから、`npm run preview` を実行してください。

本番ビルドとプレビュー：

```bash
npm run build
npm run preview
```

### sus2json のビルド依存関係

`npm run build` を実行すると、[Sekai-SUS-Parser](https://github.com/watagashi-uni/Sekai-SUS-Parser)
内の `SusToJsonCpp` が、ブラウザで使用される WebAssembly にコンパイルされます。デフォルトのディレクトリ構造は以下の通りです：

```text
workspace/
├── sekai-mmw-preview-web/
└── Sekai-SUS-Parser/
    └── SusToJsonCpp/
```

本プロジェクトのディレクトリで以下のコマンドを実行し、ソースコードを準備できます：

```bash
git clone https://github.com/watagashi-uni/Sekai-SUS-Parser ../Sekai-SUS-Parser
```

ソースコードがデフォルトの場所にある場合は、`SEKAI_SUS_TO_JSON_ROOT` を `SusToJsonCpp` ディレクトリに設定してください：

```bash
SEKAI_SUS_TO_JSON_ROOT=/path/to/Sekai-SUS-Parser/SusToJsonCpp npm run build
```

##

DeepL.com（無料版）で翻訳しました。
