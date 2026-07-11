# DjangoでWebアプリケーション作成課題に取り組む

この課題では「Django本格入門」で学んだ内容以外の知識も必要になります。それらについては [Django公式ドキュメント](https://docs.djangoproject.com/ja/5.2/contents/) や事業所にある以下の本を参考にしてください。

- 現場で使えるDjangoの教科書：基礎編
- 現場で使えるDjangoの教科書：実践編

以下に開発時のヒントや該当する資料の場所を載せておきますので、参考にしてください。

## プロジェクトの作成

プロジェクトを作成する時は「現場で使えるDjangoの教科書：基礎編 3.4 ベストプラクティス1：分かりやすいプロジェクト構成」に従ってください。

## Userモデルおよび認証方法の変更

Djangoが提供しているUserモデル自体を変更することはできないため、下記を参考にしてUserモデルを拡張し、メールアドレスで認証するように変更してください。一度マイグレーションを行うとデフォルトのUserモデルで認証機能が用意されてしまうため、**この作業はマイグレーション前に行ってください。**

- 「現場で使えるDjangoの教科書：基礎編 3.3 よくあるプロジェクト構成」
- 「現場で使えるDjangoの教科書：基礎編 6.9 ベストプラクティス3：User モデルを拡張する」
- 「現場で使えるDjangoの教科書：実践編 1.4 拡張ユーザーモデルを利用するためのカスタマイズ」
- 「現場で使えるDjangoの教科書：実践編 1.5 メールアドレスとパスワードで認証するためのカスタマイズ」

下記のサイトも参考になります。
- [Django Admin カスタムユーザーの作成方法](https://tech-lab.sios.jp/archives/40417)
- [Django の認証方法のカスタマイズ](https://docs.djangoproject.com/ja/5.2/topics/auth/customizing/#a-full-example)

## Bootstrapの導入

「現場で使えるDjangoの教科書：実践編 第2章 開発のヒント（Bootstrap4対応）」を参考にしてBootstrapを導入してください。ただし現在はBootstapのバージョンは5系になっているため、django-bootstrap4ではなくdjango-bootstrap5を導入します。導入時の違いは以下です。使用方法は変わりません。

- インストールコマンド
    ```
    (venv) $ pip install django-bootstrap5
    ```

- 設定ファイル(setting.py)に追加
    ```
    INSTALLED_APP = [
        ...
        'django_bootstrap5',
    ]
    ```

- テンプレートに追加
    ```
    {% load django_bootstrap5 %}
    {% bootstrap_css %}
    {% bootstrap_javascript %}
    ```

## 作業一覧表示機能

この機能に限りませんが、関数ベースではなくすべてクラスベースビューで作成してください。

## 検索機能

ListViewに検索機能を追加するには下記が参考になります。

- [動的なフィルタリグ](https://docs.djangoproject.com/ja/5.2/topics/class-based-views/generic-display/#dynamic-filtering)

## 作業登録機能

「現場で使えるDjangoの教科書：基礎編 第8章 フォーム (Form)」を読んでおきましょう。

## 完了状態切替機能

現在の完了状態と反対の状態（完了→未完了or未完了→完了）に更新します。基本のビュー(django.views.View)に`SingleObjectMixin`を組み合わせてみましょう。

## 作業削除機能

論理削除はモデルの`delete`メソッドをオーバーライドし、削除フラグ(is_deleted)を立てて保存しましょう。
