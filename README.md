# 公開鍵管理システム ログインノード用クライアント

## デプロイ方法

- Ubuntuの場合、以下のパッケージをインストール
  - `mariadb-client`
  - `python3-ldap3`
  - `python3-mysql.connector`
  - `python3-yaml`
- 本プログラムを`/etc/ssh/get_pubkeys`に配置し、パーミッションを `700 / root:root` とする
- ローカルユーザでも本システムで管理した公開鍵でログインしたい場合、 `/etc/ssh/local_user_mapping.yml` ・ `/etc/ssh/get_pubkeys_config.yml` を作成 (パーミッションは `600 / root:root`)
- `/etc/ssh/sshd_config` に以下の2行を追記して、sshdを再起動

```
AuthorizedKeysCommand /etc/ssh/get_pubkeys
AuthorizedKeysCommandUser root
```
