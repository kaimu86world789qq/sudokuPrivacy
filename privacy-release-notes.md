# ナンプレのプライバシーポリシー調整メモ

更新日：2026年10月20日

## 今回の変更

- 記憶力チャレンジ用の日本語版・英語版・案内ページをナンプレ / Sudoku用に変更。
- Jekyllのサイト名・説明も変更。公開やGitへのpushは実施していません。
- ナンプレのコードを確認し、盤面・メモ・取り消し履歴・経過時間・ヒント・難易度別記録・問題履歴・問題ストック・言語・操作音・環境音選択・音量・広告頻度管理・直近100件のローカル診断記録を記載。
- ランダム生成・ヒント計算は端末内、環境音は同梱音源の再生であることを記載。
- AdMobのバナー・リワード・インタースティシャルを記載。UMPの地域・管理画面設定に依存する同意管理も記載。
- 記録削除はクリア数・ベストタイムのみを削除する実装に合わせて修正。
- 自動バックアップ無効という元アプリの説明を削除。ナンプレのManifestでは無効化されていないため、OS等のバックアップが適用される可能性を記載。

## 元の文書から引き継いだ運営方針

- 運営者：Trierr（トリエラ）、連絡先：dokuostyktusdfire45gnbr1988@gmail.com。
- 対象：16歳以上。日本・英語圏・EUへの配信予定。Google Play・Amazonアプリストア向け。
- これらは元文書の方針を引き継いだもので、ストア登録内容やAdMob管理画面の設定を今回確認したものではありません。対象年齢はストアのコンテンツレーティングそのものを示すものではありません。

## 公開時の接続

- ナンプレ用の公開URLは未設定です。元アプリのMemoryGamePrivacy公開URLは流用していません。
- 公開先を決めてページを公開した後、アプリのPRIVACY_POLICY_URLとストアのポリシーURLへ設定します。現在のconfig/admob.json等はURLが空欄です。
- AdMobのプライバシーとメッセージで、対象アプリのメッセージ設定・ポリシーURLを実際の配信方針とそろえます。SDK実装だけではメッセージ公開完了を意味しません。
- 元アプリの公開・実機同意テスト完了の記録は、このナンプレに対する実績ではないため置き換えました。

## 実装の確認箇所

- lib/data/storage.dart：SQLite保存、記録削除、出題履歴、広告頻度、診断記録。
- lib/game/session.dart、lib/game/controller.dart：盤面、メモ、取り消し、時間、ヒント、報酬の状態。
- lib/audio/ambient_audio.dart：同梱音源、環境音・音量の復元。
- lib/ads/ad_service.dart、lib/ui/app.dart：3種類の広告、UMP、広告プライバシー設定。
- android/app/src/main/AndroidManifest.xml、pubspec.yaml：権限、バックアップ設定、SDK構成。

## 確認した公式資料

- [Google Mobile Ads SDKのデータ開示](https://developers.google.com/admob/android/privacy/play-data-disclosure)
- [Flutter UMPの実装・管理画面設定](https://developers.google.com/admob/flutter/privacy)
- [Android自動バックアップ](https://developer.android.com/identity/data/autobackup)

Googleの開示資料は最新版SDKを対象としているため、ストア申請時は実際にリリースするSDK・管理画面設定と合わせて確認してください。
