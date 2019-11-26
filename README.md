# django-nginx-gunicorn-docker

Django+nginx+gunicornでのデプロイを一瞬で実行するdocker-composeです。
ポートのリンク設定は下図を参照してください。

## How to use

### Clone repository
このリポジトリをクローンします。

```
$ git clone https://github.com/tken2039/django-nginx-gunicorn-docker.git
```
### Directory structure
次のようなディレクトリ構造が想定されています。

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


### Setting
django/Dockerfileの一部を編集します。直接編集も可能ですが、linuxOSの方は以下のコマンドを使うと楽ちんです。

```
$ sed -i -e s/MYPROJECT/[PROJECTNAME]/g Dockerfile
```

Dockerfileは、デフォルトではプロジェクト名がMYPROJECTになっているので、sedコマンドであなたのプロジェクト名（[PROJECTNAME]）に書き換えています。

### Execution
`docker-compose.yml`が存在するディレクトリで以下のコマンドを実行します。

```
$ docker-compose up
```









