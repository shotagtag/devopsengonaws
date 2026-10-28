# コンテナでアプリケーションを起動してみましょう🚀

VS Code Server にログインし、ターミナルで以下のコマンドを順に実行します。

- web2048 を git クローンします。
```
git clone https://github.com/gabrielecirulli/2048
cd 2048
```

- Dockerfile を作成します。webサーバーのコンテナをベースとして、web2048アプリケーションを含めてビルドする手順を定義します。
```
cat << EOF > Dockerfile
FROM nginx:latest

COPY . /usr/share/nginx/html

EXPOSE 80
EOF
```

- Docker サービスを起動します。
```
sudo service docker start
```

- 以下のようにパスワードが要求されるので、VS Code Serverと同じパスワードを入力してください。

```
We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

For security reasons, the password you type will not be visible.

[sudo] password for participant: 
```

- コンテナイメージをビルドします。Dockerfileに基づき、コンテナイメージがビルドされます。
```
docker build -t web2048 .
```

- ビルドされたコンテナイメージを確認します。
```
docker images
```

- コンテナイメージからコンテナを起動します
```
docker run -d -it -p 8081:80 web2048
```

- 以下のようなブラウザで開くかどうかの通知が現れますので、クリックしアプリを開きます。
<img width="455" height="115" alt="image" src="https://github.com/user-attachments/assets/f13c3412-9236-4f95-bab9-02ea5b384740" />

