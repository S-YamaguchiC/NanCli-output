# Nanchatte-Clicker-output

## 説明しよう！
NanCli-outputとは、[これ](https://github.com/S-YamaguchiC/NanchatteClicker)の入力と出力を分けたうちの出力の部分である。以上  

## なんくり（出力）の処理の流れ
1. 起動します
2. ``HomePage.vue``の``fillData()``が呼ばれます
3. axiosで、あるサーバー上のCGIに非同期通信をして、JSONデータ？をもらってきます
4. 非同期通信で``response``が正常に受け取れたら、``then()``のなかで``stringify()``を使ってエンコします
5. エンコした値を、チャートに使う値に代入します
6. チャートが描画されます
7. おわり
