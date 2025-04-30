# DarQ homepage

- [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) で静的 HTML を生成します。マークアップ言語は Markdown です。

## 初期設定

1. [poetry](https://python-poetry.org/docs/#installation), [pyenv](https://github.com/pyenv/pyenv#unixmacos) のインストール
2. venv の作成

```bash
$ poetry install --no-root
```

## build

以下のコマンドを実行すると、`site` へ静的 HTML が生成されます

```bash
$ poetry run mkdocs build
```

## Github Pages への deploy 方法

GitHub Actions により、`main` branch への push (含 merge) が行われると、
`mkdocs gh-deploy --force` による静的 HTML 生成と、成果物の `gh-pages` branch への push が行われます。

repo の `settings>Pages` から `gi-pages` branch (の ROOT(/)) を GitHub Pages の source として設定すると、生成された HTML が Pages として表示されます。

## 編集方法

1. topic branch を切る
2. `docs` 以下へ Markdown ファイル作成 or 更新する
3. `mkdocs.yml` の `nav:` を更新して、ページ構成（目次）を調整する
4. 手元環境で静的 HTML を生成して、表示を確認
   - `poetry run mkdocs server` や、VSCode の [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer) plugin などを利用して、手元のブラウザから HTML を閲覧できます
5. topic branch を push して Pull Request を作成する
6. `main` branch へマージいただく
7. `main` branch へのマージをトリガに GitHub Actions が動き、GitHub Pages が更新される
