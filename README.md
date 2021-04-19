# コーディングガイドライン

## インデント
スペース2個

<br>

## CSS
- 特別な場合を除き、スタイルはSassで記述しCSSを直接編集しない

### [Sass](https://sass-lang.com/)

- Sass構文ではなくSCSS構文で記述する
- コンパイルの方法は任意とする（将来的にタスクランナーに固定する）
- フォルダ構造は任意とする（将来的には共通のものにする）

### リンター

- [stylelint](https://stylelint.io/)を使用する
- [stylelint-config-recommended-scss](https://github.com/kristerkari/stylelint-config-recommended-scss)を使用する
- 以下のルールを追加する(***要検討***)

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
- [stylelint-prettier/recommended](https://github.com/prettier/stylelint-prettier)を使用する
- プロパティの並び順は[stylelint-config-recess-order](https://github.com/stormwarning/stylelint-config-recess-order)を使用する