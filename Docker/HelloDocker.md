# DockerでPHPの開発環境を整える
## Dockerのインストール
[dockerhub](https://hub.docker.com/)からインストール。  
今回は[Docker Desktop for Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)を使用した。  
※インストールにはdockerhubのアカウントが必要となる。  
### インストールが成功したかどうか確認
起動中のコンテナ一覧を表示するコマンドを実行し、インストールが成功したことを確認。
```
$ docker container ls
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES

```
## PHPの開発環境を作る
以下のコマンドを実行してPHPの開発環境を作成
```
$ mkdir php-book
$ cd php-book
$ docker container run -d --name php-book -v $(pwd):/var/www/html -p 80:80 php:7.2-apache
```
以下のコマンドでコンテナに入る
```
$ docker container exec -it php-book bash
root@a3cc95a81953:/var/www/html#
// コンテナから出るときはControl + P Control + Q を実行
```
phpinfo()を作成し、http://localhost/ にアクセスしてphpinfo()の内容が表示されればOK
```
echo '<?php phpinfo();' > index.php
```
## Dockerコマンドとか
