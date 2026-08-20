# 無料でWebサーバを構築する方法

GoogleCloudの無料枠(Always Free)でWebサーバを構築する

# 1. 前提条件

- Googleアカウントを持っている
- Google Cloudにプロジェクト作成、クレジットカード登録済み

# 2. VMインスタンス作成

| 項目 | 設定                                                             |
| --- |----------------------------------------------------------------|
| 名前 | 任意                                                             |
| リージョン | `us-central1` （アイオワ）<br>`us-east1`（サウスカロライナ）<br>`us-west1`（オレゴン） |
| ゾーン | 任意                                                             |
| マシンタイプ | **e2-micro**                                                   |
| OS | Ubuntu                                                         |
| OSバージョン | Ubuntu 24.04 LTS                                               |
| ブートディスク | Standard Persistent Disk （標準永続ディスク）                            |
| ディスク容量 | **30GB** 以下                                                    |
| ファイアウォール | HTTP トラフィックを許可する<br>HTTPS トラフィックを許可する                          |

---

# 3. SSHでログイン

---

# 4. Nginxをインストール

```bash
sudo apt update
```

```bash
sudo apt install nginx -y
```

Nginxを起動

```bash
sudo systemctl enable nginx
```

```bash
sudo systemctl start nginx
```

状況確認

```bash
sudo systemctl status nginx
```

`active (running)` となっていればOK

---

# 5. ブラウザで確認

VMの外部IPをブラウザのURL欄に貼り付けてアクセス

外部IPが

```
34.xxx.xxx.xxx
```

の場合、ブラウザで

```
http://34.xxx.xxx.xxx
```

を開く。

```
Welcome to nginx!
```

と表示されれば成功。

---

# 6. ドキュメントを配置

ドキュメントルート作成

```
/var/www/docs
```

の場合

```bash
sudo mkdir -p /var/www/docs
```

所有者変更

```bash
sudo chown -R $USER:$USER /var/www/docs
```

`/var/www/docs` 内に `index.html` 作成

```bash
nano /var/www/docs/index.html
```

例）

```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <title>社内ドキュメント</title>
</head>
<body>
    <h1>社内ドキュメント</h1>

    <ul>
        <li><a href="/manual/">社内マニュアル</a></li>
        <li><a href="/development/">開発ドキュメント</a></li>
        <li><a href="/operation/">運用手順</a></li>
    </ul>
</body>
</html>
```

### Nginxをドキュメント用に設定

例えば、

```bash
sudo nano /etc/nginx/sites-available/docs
```

として、

```bash
server {
    listen 80;
    server_name _;

    root /var/www/docs;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```

とする。

有効化する

```bash
sudo ln -s /etc/nginx/sites-available/docs /etc/nginx/sites-enabled/docs
```

デフォルト設定を削除する

```bash
sudo rm /etc/nginx/sites-enabled/default
```

設定を確認

```bash
sudo nginx -t
```

問題なければリロード

```bash
sudo systemctl reload nginx
```

```bash
http://34.xxx.xxx.xxx/
```

にアクセスして `index.html` の内容が表示されればOK

---