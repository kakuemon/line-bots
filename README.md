# LINE BOT

## HOW TO USE

### 1-messagingAPI.ipynb
1. 最上位セルの `user_id` および `access_token` を入力する
    - 各種credntialsはLINE Developersのチャネル基本設定を参照
1. あとは各セルを実行するだけでメッセージを送信できる


### 2-webhook.ipynb
1. 最上位セルの`access_token`および`channel_secret`を入力する
    - 各種credntialsはLINE Developersのチャネル基本設定を参照
1. 上から順にオウム返しセルまで実行する
    - ブラウザ上で `http://127.0.0.1:5000/`にアクセスし、 `hello world!`と表示されるのを確認
1. ターミナル上で下記コマンドを実行し、ローカルサーバーを起動する
    ```shell
    python -m http.server 5000
    ```
1. 別ターミナルでngrokを起動する
    ```shell
    ngrok http 5000
    ```
1. 以下のような結果が返ってくるので、Forwardingの前部分（下記の例では `http://7c4d4d83.ngrok.io`)をコピーする
    ```shell
    ngrok by @inconshreveable                                                                        (Ctrl+C to quit)

    Session Status                online                                                                                              
    Session Expires               7 hours, 58 minutes                                                                                 
    Version                       2.3.34                                                                                              
    Region                        United States (us)                                                                                  
    Web Interface                 http://127.0.0.1:4040                                                                               
    Forwarding                    http://7c4d4d83.ngrok.io -> http://localhost:5000                                                   
    Forwarding                    https://7c4d4d83.ngrok.io -> http://localhost:5000                                                  

    Connections                   ttl     opn     rt1     rt5     p50     p90                                                         
                                  0       0       0.00    0.00    0.00    0.00   
    ```
1. LINE Developersのチャネルの基本設定画面で、Webhook URLに先ほどコピーしたURL(`http://7c4d4d83.ngrok.io`) + `/callback`を指定する
    <img width="1421" alt="image.png" src="https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/490709/f4dd7429-4d8b-7edc-04fa-c185406961ad.png">

    - もしWebhook送信の設定が「利用しない」になっている場合は、「利用する」に編集
1. LINEでメッセージを送信すると、オウム返しされることを確認する
