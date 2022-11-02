## モチベーション
- Dockerが何か知りたい！アプリの仮想環境を立てたい！

## ゴール
- 仮想環境という概念を理解し、Dockerの仮想サーバーについて基礎的な理解をする

## 1. Dockerについて
### Dockerとは？
Dockerとは、コンテナという概念を用いた仮想環境となります
仮想コンテナを用意することで、以下の3点のメリットがあります
① ホストOS（端末）に依存しない環境が構築できる
② 起動中、ホストOSは自由に使える
③ デプロイ手順が楽になり、環境の移行がスムーズになる

#### ① OS依存しない / ② ホストOSは自由に使える
![スクリーンショット 2022-11-02 22 30 02](https://user-images.githubusercontent.com/67848399/199503431-013259c7-c527-4c8e-a1f6-bac7b81ce6c3.png)

#### ③ デプロイが楽になる = CI/CDが構築しやすい
![スクリーンショット 2022-11-02 22 35 34](https://user-images.githubusercontent.com/67848399/199503439-7d70dceb-7a10-4de5-bb7b-01a9646743f0.png)

## 2. Dockerサービス一覧
### Docker Engine
- 特にGUIで触るものでもないですが、Dockerの仮想コンテナの土台となる部分です

### Docker CLI
`docker run`や`docker build`のような、`docker`コマンドを利用できるようになります
<img width="1030" alt="スクリーンショット 2022-11-02 22 53 34" src="https://user-images.githubusercontent.com/67848399/199507450-ff6f9c84-3511-44da-bb93-6be54c74c97d.png">

### Docker Compose
Docker CLIの拡張機能です。`docker compose ~`というコマンドで、Docker CLIのコマンドをまとめて実行してくれます

### Docker Desktop
Dockerの仮想コンテナをGUIで触れるようになります

<img width="721" alt="スクリーンショット 2022-11-02 22 54 58" src="https://user-images.githubusercontent.com/67848399/199507778-6cc7c2ed-cfe0-4d72-b176-c46cf20f36e5.png">


### Docker hub
Dockerのメリットは、`Dockerfile`や`docker-compose.yml`のようなファイルでコンテナ情報をプログラムコードで管理ができます。
Docker hubは、Docker用のGithubと捉えたら理解がしやすいと思います。
つまり、第三者がDocker Hubに投稿したコンテナ情報を使うことも可能です。

## 3. Docker基本用語
### コンテナとイメージ
![スクリーンショット 2022-11-02 23 07 16](https://user-images.githubusercontent.com/67848399/199510657-42eea494-229f-4423-8137-1419207497d5.png)


## 4. Dockerfileの作成
### Dockerfileの基本
| 命令  | 効果 |
| ------------- | ------------- |
| FROM  | ベースイメージを作成する  |
| RUN  | 任意のコマンドを実行（gitなど） |
| COPY  | ホストマシンのファイルをイメージに追加する  |
| CMD  | デフォルト命令を指定する |

その他：　https://datawokagaku.com/dockerfile_commands/

### サンプル
```Dockerfile
FROM ubuntu:20.04

RUN apt update
RUN apt install -y vim

COPY .vimrc /root/.vimrc

CMD date +"%Y/%m/%d %H:%M:%S ( UTC )"
```

### buildしてみる
```
$ docker image build     \
    --tag my-ubuntu:date \
    .
    
$ docker image ls
```

## 5. docker-compose.ymlの作成


## 6. コンテナを立ててみる



EOF;
