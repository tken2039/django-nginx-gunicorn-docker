# django-nginx-gunicorn-docker

Django+nginx+gunicornでのデプロイを一瞬で実行するdocker-composeです。

(Use docker-compose to easily deploy with Django + nginx + gunicorn.)

## How to use

### ・Clone repository
このリポジトリをクローンします。

(Clone this repository.)

```
$ git clone https://github.com/tken2039/django-nginx-gunicorn-docker.git
```
### ・Directory structure
次のようなディレクトリ構造が想定されています。

(Assume the following directory structure:)

```
django-nginx-gunicorn-docker/
      ├ nginx/
      │　└ project.conf
      ├ django/
      │  ├ Dockerfile
      │  ├ requirements.txt
      │  └ [DJANGOPROJECT]
      │     ├ manage.py
      │     ├ …
      │     └ [PROJECTNAME]
      └ docker-compose.yml
```

上記のディレクトリツリーの[DJANGOPROJECT]が、あなたのDjangoProjectになるよう配置してください。（[PROJECTNAME]は、settings.pyなどが入っているディレクトリです。）

(Place [DJANGOPROJECT] to be your DjangoProject. ([PROJECTNAME] directory contains settings.py etc.))


### ・Setting
django/Dockerfileの一部を編集します。直接編集も可能ですが、LinuxOSの方は以下のコマンドを使うと楽ちんです。

(Edit part of django/Dockerfile. For LinuxOS, use the following command.)

```
$ sed -i -e s/MYPROJECT/[PROJECTNAME]/g Dockerfile
```

Dockerfileは、デフォルトではプロジェクト名がMYPROJECTになっているので、sedコマンドであなたのプロジェクト名（[PROJECTNAME]）に書き換えています。

(Since the default Dockerfile has a project name of MYPROJECT, it is rewritten to your project name ([PROJECTNAME]) using the sed command.)

### ・Execution
`docker-compose.yml`が存在するディレクトリで以下のコマンドを実行します。

(In the directory where `docker-compose.yml` exists, execute the following command:)

```
$ docker-compose up
```

ブラウザで`localhost`を開いて、結果を確認してみましょう！ポート番号は不要です。

(Let's open `localhost` with a web browser. No port number is required.)

### ・Attention
- Djangoプロジェクト内のsettings.pyで、localhostを許可しておきましょう。（ALLOWED_HOSTSのところ）
(Edit "ALLOWED_HOSTS" in settings.py to allow 'localhost'.)
- ファイアウォールの設定で80番ポートへのアクセスを許可しておきましょう。
(Edit the firewall to allow access to port 80.)

## repletion

Djangoのプロジェクトを編集した場合は、次のコマンドで反映可能です。

(If you edit a Django project, you can reflect it with the following command:)

```
$ docker restart CONTAINERNAME
```

CONTAINERNAMEには、Djangoコンテナのコンテナ名を入れてください。

(In CONTAINERNAME, write container name of "Django Container".)



