# おみくじAppの作成 by dotinstall
<p>複雑なところをまとめました。</p>


## 乱数の求め方

|記法|説明|
|---|---|
|Math.random()|0以上1未満の乱数を表示<br>※0.6749728125249748　と行った具合に|
|Math.random() * 3|0以上3未満の乱数を表示|
|Math.floor(Math.random * 3)|floorメソッドを使って0/1/2の整数を表示|
|min + Mathfloor(Math.random * (max + 1 - min))|min(0以外の数を指定可)...maxの間の整数を表示|

## クリックした時に運勢を出す処理
### 1.switch文を使う

<p>※btn要素の取得とクリックイベント時の処理のみ抜粋して記載</p>

```js
    const btn = document.getElementById('btn');

    btn.addEventListener('click',() => {
       
        //乱数(0,1,2)をnに代入
        const n = Math.floor(Math.random() * 3);

        //switch文で条件分岐
        switch (n) {
            case 0:
            btn.textContent = '大吉';
            break;

            case 1:
            btn.textContent = '中吉';
            break;

            case 2:
            btn.textContent = '凶';
            break;
        }
    });

```
### 2.配列を使う

```js
    const btn = document.getElementById('btn');

    btn.addEventListener('click',() => {
        
        //配列を定義
        const results = ['大吉','中吉','凶'];

        const n = Math.floor(Math.random() * results.length);

        //配列のn番目の要素をtextに代入
        btn.textContent = results[n];
    });

```

## 確率の操作
### 1.配列を使う場合
配列の要素を増やして確率を操作する方法
```js
    const btn = document.getElementById('btn');

    btn.addEventListener('click',() => {
        
        //80%の確率で大吉 20%の確率で凶
        const results = ['大吉','大吉','大吉','大吉','凶'];

        const n = Math.floor(Math.random() * results.length);

        //配列のn番目の要素をtextに代入
        btn.textContent = results[n];
    });
```

### 2.if文を使う場合

```js
    const btn = document.getElementById('btn');

    btn.addEventListener('click',() => {
        const n = Math.random(); //0から1未満の小数
        if(n < 0.05){
            btn.textContent = '大吉'; //5%
        } else if (n < 0.2) {
            btn.textContent = '中吉'; //15%
        } else {
            btn.textContent = '凶'; //80%
        }
    });
```




