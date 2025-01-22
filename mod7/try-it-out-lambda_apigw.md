# シンプルなAPIを作成してみましょう🚀

![image](https://github.com/user-attachments/assets/6c332f65-599e-4003-a02b-97a10362af61)

### 1.シンプルなLambda関数を作成しましょう。指示されていない設定箇所はデフォルトでOKです。

1. Lambda サービスに移動し、`関数を作成` をクリックします。
2. 「関数名」に `hello-function` と入力します。
3. 「デフォルトの実行ロールの変更」を展開し `SAM_Role` を選択します
     - (本来不要ですが、ラボ環境の都合上選択してください)
5. `関数の作成` をクリックします。
6. Lambda関数が作成されました。
7. これで Lambda関数が作成されました。実行すると `Hello from Lambda!`と結果を返します(権限上実行はできません🙇‍♂️)

### 2.Lambda関数をバックエンドにしたシンプルな API Gateway を作成しましょう。指示されていない設定箇所はデフォルトでOKです。

1. API Gateway サービスに移動し、`API を作成` をクリックします。
2. APIタイプ選択の画面が開きます。 「REST API」で `構築`をクリックします。
3. REST API 作成が開きます。
   - 「APIの詳細」は `新しいAPI` を選択
   - 「API名」は `hello-api` と入力
4. `APIを作成`をクリックします。

- ここからデフォルトで存在する リソース `/`に対し、HTTPメソッドと、呼び出すLambda関数を作成します。

5. `メソッドを作成`をクリックします。
6. メソッドの詳細画面が開きます。次のように設定します。
   - 「メソッドタイプ」で `GET` を選択します。
   - 「統合タイプ」で `Lambda 関数`を選択します。
   - 「Lambdaプロキシ統合」を `有効化`します。Lambdaプロキシ統合を有効化するとAPIGWが、各種リクエスト情報をjson構造化してLambdaに渡してくれます。[詳細はこちら](https://docs.aws.amazon.com/ja_jp/apigateway/latest/developerguide/set-up-lambda-proxy-integrations.html#api-gateway-simple-proxy-for-lambda-input-format)
   - 「Lambda関数」で 先ほど作成した hello_function をリストから選択します。
8. `メソッドを作成`をクリックします。
9. これで / に HTTP GETリクエストが来た時に Lambda関数を呼び出す設定ができました。

- API Gateway 設定をデプロイしていきます。
10. 右上の `APIをデプロイ`をクリックします。Deploy APIの画面が開きます。
  - 「ステージ」で `*新しいステージ*` を選択します。
  - 「ステージ名」で `dev` と入力します。
  - `デプロイ`をクリックします。
11. 「ステージの詳細」セクションから `URL を呼び出す`を見つけ、URLをコピーしてアクセスしてみてください。
12. "Hello from Lambda!"が表示されていれば成功です！
