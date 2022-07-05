# ホームページの国際化と保守のためのワークフロー

## 概要

### この文書について

この文書では、CAT (computer aided translation) ツールを用いて英語版のページを更新する手順を説明します。

### CAT ツールについて

#### ニーズ

英語版のページに関して、以下のようなニーズを満たしたいとします。

1. 英語版も日本語版と同じデザインに揃えたい
2. 今後、日本語版の更新時に英語版も追従できるようにしたい。
3. 翻訳がおかしいところは、メンバーでも気軽に直せるようにしたい。

#### 手作業の問題点

手作業で翻訳すると、上記の 2 が問題になります。

#### CAT ツール

[OmegaT](https://omegat.org/ja/) という CAT ツールで翻訳すると、以下のメリットがあり、上記の問題が解決できそうです。

1. ソースコードと翻訳を分けて管理でき、日本語版のソースコードの英語版のところだけを翻訳で置き換えられます。
2. 日本語版のソースコードに追記があった場合にも、既に翻訳した文と同じ内容は自動的に翻訳されます。追加の翻訳が必要なところだけ追記すれば、バッチ処理で更新した英語版のソースコードを生成できます。
3. Git 等のリポジトリで管理すれば、複数人で翻訳を進められます。

## 作業の流れ

### 登場人物

- ホームページ管理者

- 国際化チーム

- メンバー

### 初回の下訳の作成

ホームページ管理者が、現時点の日本語のページのソースコードを、国際化チームに渡します。

国際化チームが、CAT ツールを使用して、下訳を作成します。

国際化チームは、下訳と CAT ツールを使用して、英語版のページのソースコードを生成します。

ホームページ管理者が、英語版のページを、テスト用の URL に公開します。


### 初回の英語版固有の内容への変更

ホームページ管理者と国際化チームが、英語版固有の内容に書き換える必要のある部分を特定します。

ホームページ管理者（または国際化チーム）は、日本語のページのソースコードから、英語版固有の内容に書き換えた日本語のページのソースコードを生成するスクリプト（英語化準備済みの日本語のページのソースコード）、または手順書を作成します。

ホームページ管理者が、英語化準備済みの日本語のページのソースコードを生成します。

国際化チームは、英語化準備済みの日本語のページのソースコードから、
下訳と CAT ツールを使用して、英語版のページのソースコードを生成します。

ホームページ管理者が、新しい英語版のページを、テスト用の URL に公開します。

国際化チームは、CAT ツールのデータを共有リポジトリに公開します。

国際化チームは、CAT ツールの使用方法を社内に共有します。


### 校正作業

国際化チームが、社内 Wiki に、校正作業の進捗管理用のページを作成します。

国際化チームとホームページ管理者が、ページやセクションごとに、それが一部の人しか校正が難しいことが予想される場合、予め進捗管理用のページに担当者を記載しておきます。

国際化チームとホームページ管理者が、仮の公開日を決めておきます。

メンバーは、仮の公開日までに、各自で CAT ツールを使って修正をしていきます。特に担当者が決まっていない所は、気づいた人が直します。CAT ツールによる更新を行い、CAT ツールのデータの変更をリポジトリにコミットします。

ホームページ管理者が、可能であれば CAT ツールによる修正のたびに、テスト用の URL の内容を更新します。

ホームページ管理者が、公開日にテスト用 URL から本番環境に以降させます。

### 保守

#### 日本語版のページが更新されたタイミング

ホームページ管理者が、英語化準備済みの日本語のページのソースコードを生成します。

ホームページ管理者が、共有リポジトリに、英語化準備済みの日本語のページをコミットします。

ホームページ管理者が、CAT ツールを使用して、更新部分の訳を作成します。

ホームページ管理者が、CAT ツールを使用して、英語版のページを生成します。

ホームページ管理者が、CAT ツールのデータをリポジトリにコミットします。