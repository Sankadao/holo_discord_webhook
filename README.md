# ホロライブP 配信開始通知Discord Webhook Bot

![image](https://hanano.hiromin.xyz/content/discordbot/holo_discord_webhook.png)

## 紹介

ホロジュールの配信予定時刻表示を読み取り、配信の10分前に告知するDiscord向けWebhookボットです。

## 参考サイト

[ホロライブメンバーの配信予定を取得して配信開始時刻に通知するDiscord botを作った](https://qiita.com/wak_t/items/4796d0e80097f93af656)

## 必要環境

Python 3以降
(テスト環境はPython 3.10.5)

## インストールが必要なPythonライブラリ

- Requests
- Beautiful Soup 4

```
pip install requests
pip install bs4
```

## 初期セットアップ

まずはDiscordのWebhook URLを取得してください。
1. 自分の所有する（または権限のある）サーバー設定を開きます。
2. 連携サービス、ウェブフックの確認を開きます。
3. 新しいウェブフックを押し、ウェブフックを新規作成します。
4. 新規作成されたウェブフックを選択し、管理しやすい名前に変更、配信告知を投稿するチャンネルを選択します。
5. 最後に「ウェブフックURLをコピー」を押し、URLを取得します。

次にボットの編集です。
コンフィグファイルは無いので本体を直接編集します。
ダウンロード後「holo_discord_webhook.py」をテキストエディタで開き、8行目を確認します。

```
webhook_url_Hololive = ''
```

「''」の間に先ほどコピーしたURLをペーストします。

ペーストした後は保存し、準備完了です。
起動方法は環境によるため割愛します。

## 更新間隔

ホロジュールにアクセスし、情報を取る間隔は10分ごとになっています。
アクセスする間隔を変更する場合は最下層にある、以下の部分を書き換えてください。

```
    if(now_time.minute % 10 == 0 and now_time.second == 0):
```

例えば2時間ごとなら以下の通りにします。

```
    if(now_time.hour % 2 == 0 and now_time.second == 0):
```
