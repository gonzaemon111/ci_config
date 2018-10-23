# ci_config

自分のciやdockerのconfigation用リポジトリ


## Rails用travis

` rails_travis.yml `
基本的にこれでいける

### docker - Rails

* ディレクトリ構成
```
    アプリケーションの中にDockerfileを配置し、その一個上の階層にdocker-sync.ymlとdocker-compoose.ymlを配置！

    {application_name}-docker
    │   ├-- {application}
    │   │       ├-- app
    │   │       ├-- bin
    │   │       └-- ...
    │   └-- Dockerfile
    ├-- docker-compose.yml
    └-- docket-sync.yml
```

* デフォルト設定
```
    DB  : MySQL 出力ポート 13306
    Web : Application 出力ポート 20000
```

`$ bundle exec rails s -b 0.0.0.0` を行なっているため、`localhost:20000`でアクセス可能！

## Nuxt.js用

### docker - nuxt

基本的な使い方
まずは、ディレクトリ構成

```
    asstesやcomponentsたちと同じ階層にdocker-compose.ymlとDockerfileを配置

    {application_name}
    ├-- assets
    ├-- components
    ├-- Dockerfile
    ├-- docker-compose.yml
    └ ...

```

* コマンド

```
 $ docker-compose build (Dockerfileかdocke-compose.ymlをいじった場合)
 $ docker-compose up
 $ dockerc-compose exec {container名} exec ash  
```
* 注) node:alpineというlinuxベースのimageをdocker-hubからとってきているが、bashコマンドが使えないらしい、、、
    だから、Railsと違って`bash`で入らずに`ash`というシェルで中に入る
* あとは、新しくアプリを作るときは、 必ず、docker-compose.ymlのserviceのすぐ下にあるnuxt_web、つまり{コンテナ名}を変更する。
* あとは、出力ポートも！デフォルトでは3333で出力になっている。 -> localhost:3333でアクセス可能