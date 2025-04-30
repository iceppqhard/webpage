# DarQ homepage

- homepageは [ここ](https://iceppqhard.github.io/webpage/) で公開されます。
- [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) で静的 HTML を生成します。マークアップ言語は Markdown です。

## 基本的な使い方

- このレポジトリーにあるMarkdownファイルを編集して、変更をmainブランチにマージすると自動的にWebページも変更されます。

### 典型的な編集方法

1. 自分のアカウントにForkする。
2. `docs` 以下へ Markdown ファイル作成 or 更新する
3. `mkdocs.yml` の `nav:` を更新して、ページ構成（目次）を調整する
4. 手元環境で静的 HTML を生成して、表示を確認 (以下を参照)
5. Githubにpushして Pull Request を作成する
6. iceppqhardユーザーにマージしてもらう
7. `main` branch へのマージをトリガに GitHub Actions が動き、GitHub Pages が更新される

## ローカルでHTMLファイルを生成する方法

### 初期設定

1. [poetry](https://python-poetry.org/docs/#installation), [pyenv](https://github.com/pyenv/pyenv#unixmacos) のインストール
2. venv の作成

```bash
$ poetry install --no-root
```

### build

以下のコマンドを実行すると、`site` へ静的 HTML が生成されます

```bash
$ poetry run mkdocs build
```

## Github Pages の 設定方法 (すでに設定済み)

GitHub Actions により、`main` branch への push (含 merge) が行われると、
`mkdocs gh-deploy --force` による静的 HTML 生成と、成果物の `gh-pages` branch への push が行われます。

repo の `settings>Pages` から `gh-pages` branch (の ROOT(/)) を GitHub Pages の source として設定すると、生成された HTML が Pages として表示されます。

