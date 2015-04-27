
nvalidr
================================

日本語用のバリデータ/ノーマライザ。
個人的に好みのものが npm に見つからなかったもので( ; ˘ω˘)。
n は日本の N！ そして normalize の N です。
文字列の正規化とバリデーションが同時に行えます。


    var text = '　 アカサタナハマヤラワ漢字';
    var errmsg = null;
    text = nvalidr(text).trim().hiragana(function() {
      errmsg = 'ひらがなで入力してください。';
    }).s

## メソッド

* 基本
    * normalize  --  replace/validate を同時に行う
    * validate  -- 値のチェックとエラーハンドルコールバックのコール
    * replace -- 文字列の置換
    * trim -- トリム
    * ltrim -- 左トリム
    * rtrim -- 右トリム
* ユーテリティ
    * date -- 日付正規化とバリデーション
    * hiragana -- ひらがな正規化とバリデーション
    * katakana -- カタカナ正規化とバリデーション
    * number -- 数値正規化とバリデーション
    * phone -- 電話番号正規化とバリデーション
    * email -- Email正規化とバリデーション





## 使い方（ちょっとだけ）

### ひらがな

    var text = 'アカサタナハマヤラワ';
    text = nvalidr(text).hiragana().s

    console.log(text); // 'あかさたなはまやらわ'


### 電話番号

    var text = '０１２３−４５６７ー８９０漢字'; //これでも通ります
    text = nvalidr(text).phone().s

    console.log(text); // '0123-4567-890'


### 連結

    var text = ' 　	アカサタナハマヤラワ	  　';
    text = nvalidr(text).trim().hiragana().s

    console.log(text); // 'あかさたなはまやらわ'


### バリデーションエラーのハンドル

    var text = '　 アカサタナハマヤラワ漢字';
    var errmsg = null;
    text = nvalidr(text).trim().hiragana(function() {
      errmsg = 'ひらがなで入力してください。';
    }).s

    console.log(errmsg) // 'ひらがなで入力してください。'


