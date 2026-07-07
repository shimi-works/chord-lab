# CLAUDE.md — Chord Lab (chord-lab)

## このプロジェクト

- Cubase風ミニDAW＋コード練習＋作曲講座（音楽系アプリはここに一本化。旧oto-labはアーカイブ済み）
- 構成: 単一HTMLファイル（3000行超の大型。セクションコメントで区画）
- **公開中**: https://shimi-works.github.io/chord-lab/ （リポジトリ `shimi-works/chord-lab`）
- 管理情報: `C:\Users\smzyt\apps\dev-os\projects\`

## 開発標準

`C:\Users\smzyt\apps\dev-os\CLAUDE.md` の「全プロジェクト共通 開発標準」に従う。

## このプロジェクト固有のルール（重要）

- **`.nojekyll` を絶対に消さない**（JSの `${}` をJekyllが誤認してPagesビルドが失敗する対策）
- **push前に必ず verify-single-html スキルを通す**。マーカーは `track-header` `pal-btn`。過去に起動不能のままpushした事故あり（2026-07-05）
- localStorage: `chordlab-v1`（現在の曲）/ `chordlab-songs-v1`（マイソング）。スキーマ変更時は読込時マイグレーションを必ず書く（実績のある方式）
- 音源: soundfont-player（jsDelivr CDN）＋合成音フォールバック。**外部音源プラグイン機構は作らない方針**（ユーザー決定）
- U-FRET取り込みのCORSプロキシ（allorigins等）は不安定前提。リトライ2周は削らない
- 単キー（数字/英字）は鍵盤演奏に予約済み。ツールのショートカットに使わない。NumpadDecimalは`ev.code`で捕捉（NumLock offでkey='Delete'になる）

## 動作確認

- 挙動の検証は実PointerEvent/clickをdispatchして結果を `document.title` で回収する方式（実績あり）
- 公開反映: `git push` 後、数十秒〜数分。キャッシュ回避は `?クエリ` 変更かシークレットウィンドウ
