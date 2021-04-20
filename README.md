# ガイドライン
## 本レポジトリの使用方法
1. zip形式で本レポジトリをダウンロードする
2. zipファイルを解凍し、フォルダ名を任意のプロジェクト名に変更する
3. プロジェクトのディレクトリに移動し、```npm i```コマンドを実行してパッケージをダウンロードする
4. .gitignoreファイルの```#.vscode```から```#```を削除し.vscodeディレクトリをGitの追跡対象外とする
5. （プロジェクトをGit管理する場合）```git init```コマンドの実行または任意のGUIツールの操作により、Gitを開始する
6. フォルダ・ファイルを作成し、コーディングを開始する

<br>

## 各設定ファイルについて
- プロジェクトをGit管理する場合、特に明言されていなければこれらの設定ファイルもGitの追跡対象とする
### .vscode/settings.json
Visual Studio Codeの設定ファイル。このファイルに記述した設定はグローバルの設定を上書きし、このディレクトリ内でのみ有効となる。個人の環境に応じて編集可。**プロジェクトをGit管理する場合、.vscodeディレクトリは追跡対象としない。**
### .gitignore
Gitの追跡対象にしないファイル・ディレクトリを記述する。<br>
node_modulesと.DS_Storeは追跡対象としない。必要に応じて追記可。
### .stylelintrc.json
stylelintの設定ファイル。使用するルールについては後述。
### README.md
本ドキュメント。プロジェクトに応じて編集可。
### package-lock.json
使用するパッケージのバージョンを固定するためのファイル。
### package.json
プロジェクトで使用するパッケージを記載したファイル。

<br>

## インデント
スペース2個

<br>

## CSS
- 特別な場合を除き、スタイルはSassで記述しCSSを直接編集しない

### [Sass](https://sass-lang.com/)

- Sass構文ではなくSCSS構文で記述する
- コンパイルの方法は任意とする（将来的にはタスクランナーに固定する）
- フォルダ構造は任意とする

### リンター

- [stylelint](https://stylelint.io/)を使用する
- ベースのルールとして[stylelint-config-recommended-scss](https://github.com/kristerkari/stylelint-config-recommended-scss)を使用する
- さらに以下のルールを追加する(***要検討***)

["no-descending-specificity": null](https://stylelint.io/user-guide/rules/no-descending-specificity)<br>
詳細度の高いセレクタのあとに詳細度のより低いセレクタを定義するのを許容する。具体的には、以下のような記述を許容する。
```
// no-descending-specificityルールがオンの場合、textarea:focusが先に評価されるためエラーとなる
textarea {
  width: 100%;

  &:focus {
    outline: none;
  }
}
```

["selector-pseudo-element-colon-notation": "double"](https://stylelint.io/user-guide/rules/selector-pseudo-element-colon-notation)<br>
擬似要素の直前にコロンを2個つける。
```
// 以下は許容される
a::before {
  color: pink;
}

// 以下は許容されない
a:before {
  color: pink;
}
```

### フォーマッター

- [Prettier](https://prettier.io/)を使用する
- ベースのルールとして[stylelint-prettier/recommended](https://github.com/prettier/stylelint-prettier)を使用する
- プロパティの並び順は[stylelint-config-recess-order](https://github.com/stormwarning/stylelint-config-recess-order)を使用する


<br>

## 使用が推奨されるVisual Studio Codeプラグイン
任意だが、使用が推奨されるVisual Studio Codeプラグインを以下に挙げる。
- [stylelint](https://marketplace.visualstudio.com/items?itemName=stylelint.vscode-stylelint)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)