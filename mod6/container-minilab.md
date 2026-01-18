# コンテナでアプリケーションを起動してみましょう🚀

VS Code Server にログインし、ターミナルで以下のコマンドを順に実行します。

- ラボ権限の関係で root ユーザに昇格します。
```
sudo su -
```

- 必要なソフトウェアをインストールします。
```
yum -y install docker git
```

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
service docker start
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

