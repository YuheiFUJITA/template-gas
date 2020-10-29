# template-gas

## このテンプレートについて
このテンプレートは、Google Apps Scriptについて以下のことを行うことができます。

* TypeScriptによるコーディング
* ローカル上での開発

## 使い方

### 環境構築
このテンプレートを使うには、 [`clasp`](https://github.com/google/clasp) が必要になります。

インストールしていない場合、 以下のコマンドからインストールしてください。

また、 [設定](https://script.google.com/home/usersettings) よりGoogle Apps Script APIを有効にする必要があります。

```
$ npm install -g @google/clasp
$ clasp login
```

### プロジェクトのセットアップ
まず、 `.clasp.json` の `scriptId` に対象のGASのスクリプトIDを設定してください。

スクリプトIDはGoogleドライブから目的のGASを開き、 `ファイル > プロジェクトのプロパティ` から表示される `スクリプト ID` から確認できます。

既存のソースコードがある場合、以下のコマンドでローカルに `pull` できます。

```
$ clasp pull
```

### ソースコードのアップロード
ローカルでコーディングしたソースコードは、以下のコマンドを実行することでGASプロジェクトに `push` できます。

```
$ clasp push
```

## 各ファイル/ディレクトリについて

### `src`
このディレクトリ配下のファイルが `clasp push` の対象になります。

GASのソースコードはこのディレクトリ内に配置してください。

変更したい場合は、 `.clasp.json` の `rootDir` を変更してください。

### `.clasp.json`
`clasp` に関する設定ファイルです。

詳しくは [こちら](https://github.com/google/clasp#project-settings-file-claspjson) を参照してください。


## 開発時の注意
`clasp` には `push` や `pull` といった `git` に似たコマンドがありますが、 `clasp` 自体に `git` のようなバージョン管理機能はありません。
`clasp push` や `clasp pull` は、純粋にローカルからGASプロジェクト（もしくはその逆）への上書きを行います。

また、 TypeScriptでコーディングされたGASを `clasp push` すると、自動的に `.gs` にトランスパイルされます。そのため、 `clasp push` したあとに `clasp pull` してしまうと、トランスパイル後のファイルでローカルのファイルが上書きされてしまいます。
