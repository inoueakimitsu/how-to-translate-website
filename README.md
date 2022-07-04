# how-to-translate-website

## 概要

この記事では、CAT (computer aided translation) ツールを使用して、静的なホームページの翻訳を行う方法を説明します。

1. CAT ツールをインストールします。
   - OmegaT のインストール
   - Okapi Rainbow のインストール

2. 静的なホームページを収集します。
   - wget を使ってページを収集します。

3. CAT ツールを使用してホームページを翻訳します。
  - Okapi Rainbow で HTML を取り込み、OmegaT 用のファイルを生成します。
  - OmegaT で翻訳を行います。
  - Okapi Rainbow で OmegaT 用のファイルを開き、HTML を書き出します。

4. 翻訳したホームページを公開します。

## CAT ツールをインストールする

この記事では、OmegaT と Opkapi Rainbow という CAT ツールを使用します。

### OmegaT をインストールする

OmegaT は、Windows、Mac、Linux の 3 つのプラットフォームで動作する翻訳ツールです。

1. [OmegaT の公式サイト](https://omegat.org/ja/download)から、自分のプラットフォームに対応したインストーラをダウンロードしてください。
2. ダウンロードしたインストーラを実行してください。
3. インストール手順に従ってインストールしてください。

### Okapi Rainbow をインストールする

Okapi Rainbow は、Windows、Mac、Linux の 3 つのプラットフォームで動作する翻訳ツールです。

1. [Okapi Rainbow の公式サイト](https://okapiframework.org/wiki/index.php/Rainbow)から、自分のプラットフォームに対応したバージョンのファイルをダウンロードしてください。
2. ダウンロードしたファイルを適当な場所に解凍します。

## 静的なホームページを収集する

この記事では、Windows で wget を使ってホームページを収集します。

まず wsl を適当なフォルダで開きます。

次に以下のコマンドを実行します。

```
wget --recursive --level=inf --no-parent --html-extension --restrict-file-names=windows --directory-prefix=<ホームページのタイトル> <ホームページのドメイン>
```

このコマンドの `--directory-prefix` オプションで、ホームページを保存するフォルダ名を指定します。存在しない場合は作成されます。


## CAT ツールを使用してホームページを翻訳する

この記事では、Okapi Rainbow で HTML を取り込み、OmegaT 用のファイルを生成し、OmegaT で翻訳を行い、Okapi Rainbow で OmegaT 用のファイルを開き、HTML を書き出します。

### Okapi Rainbow で HTML を取り込む

1. Okapi Rainbow を起動します。(okapi のフォルダの rainbow.exe を起動します)

2. Language and Encodings を適切な値に設定します。

3. 先ほどホームページをダウンロードしたフォルダを画面にドラッグ アンド ドロップします。

4. Utilities の Translation Kit Creation をクリックします。

5. Package Format の Type of package to create を OmegaT Project に変更します。

6. Output Location の Name of the package を適切な名前に変更します。

7. Execute を押下し、OmegaT 用のプロジェクトを保存します。

8. Okapi Rainbow のプロジェクトを保存しておきます。

9. Okapi Rainbow を終了します。

### OmegaT で翻訳する

1. OmegaT を起動します。(スタートメニューなどから)

2. 先ほど作成した OmegaT 用のプロジェクトを開きます。

3. 翻訳対象ファイル一覧からファイルを選び、翻訳を開始します。

### Okapi Rainbow で OmegaT 用のファイルを開き、HTML を書き出す

1. Okapi Rainbow を開きます。ただし、先ほど作成した設定ファイルを開くのではないので注意してください。

2. 設定ファイルを開いていない状態で、OmegaT のプロジェクトのファイル内の `manifest.rkm` を、Okapi Rainbow のファイル追加画面にドラッグアンドドロップします。

3. Utilities の Translation Kit Post-Processing を実行します。

4. 翻訳結果が done フォルダ内に生成されます。

## TODO

- NICT のエンジンの設定方法
- パックの方法 (plugin のインストールが必要)
- 原文の変更時の対応方法
- 既に一部多言語化された原稿やホームページがある場合の流れ
  - Align Assist (http://e-trans.d2.r-cms.jp/blog_detail/id=47)
  - Matecat Aligner

## 参考資料

- https://momdo.hatenadiary.org/entry/20140406/p1
- https://omegat.sourceforge.io/user-support-archive/2016-April/038131.html
- https://omegat.sourceforge.io/user-support-archive/2015-March/034361.html


## 準備中

### NICT texTra の設定方法

[omegat-textra-plugin](https://github.com/miurahr/omegat-textra-plugin/releases) にアクセスし、jar ファイルをダウンロードします。

C:\Program Files\OmegaT\plugins または 

OmegaT に機械翻訳の設定を付与します。

### CAT ツールを使うメリット

- 同じ文を何度も訳さなくて良い
- 表記ゆれを減らせる
- 複数人で作業しやすい
- 原文の変更時の差分を自動で管理できる
- 文法チェックを行える
