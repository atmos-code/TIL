# CSSGrid
## 明示的なグリッドの指定量を超えたアイテム配置は暗黙的なグリッド（自動配置）により配置される
- grid-template-columns（明示的なグリッド）で２列指定した上で、grid-auto-flow:column(暗黙的なグリッド）を指定した場合
- アイテムが３つ以上入った場合、３列目以降はautoで配置される
```CSS
｛
　display:grid;
 grid-template-columns: auto 1fr;
 grid-auto-flow:column;
｝
```

## アイテムのサイズを超えた画像を扱う際の注意点
- アイテムの横幅に対してオリジナルの比率で決まる高さ(min-content)が同じ行の他のセル要素より大きい場合、画像を基準としてトラックサイズが設定されてしまう
- 画像全体を表示させたい場合は問題ないが、画像は一部の切り取りで良いから余白感を整えたい場合にやっかい
- 以下のようにすると、トラックサイズ確定後にmin-heightが反映されるため、画像をサイズの確定処理から切り離すことができる。
```CSS
img｛
 height:0;
 min-height:100%;
｝
```

## CSSGridのauto
- autoは通常レイアウトのautoとは違う
- auto = minmax(auto,auto)
- CSSgridのautoはトラックに配置されたアイテムのmin-width/min-heightの中で最も大きいサイズで決まる
- いくつか条件はあるものの、minmaxの最小値がmin-contentになってしまいやすく、崩れやすい
- このため、以下のように記載するのが無難
- minmax(0,auto)
- frも考え方は同じ

## gridのposition
- グリッドの親をrelative、アイテムの一つをabsoluteとした時、そのアイテムは整列のロジックから除外される
- 親が作ったグリッドに合わせて、grid-columnなどで位置指定できる（その位置に既に要素が置かれていても、その上に重ねて配置される）

## grid-auto-rows,grid-auto-columns
- 暗黙的なグリッド（自動配置）のサイズ指定
- ２つ以上書くと、それらが交互に繰り返される
- grid-auto-rows:100px 200px →100px 200pxが繰り返される

## grid-auto-flow
### grid-auto-flow: row;行から埋める
- 左から右へ→上から下へ
- 上から下へ、１行ずつ行を埋めていく
- Z型の要素配置になる

### grid-auto-flow: column; 列から埋める
- 上から下へ→左から右へ
- 左から右へ、１列ずつ列を埋めていく
- N型の要素配置になる

### grid-auto-flow: dense; 空きスペースを埋める
- 自動配置において、複数のエリアを専有するアイテムがある場合に空きスペースが生じることがある
- 上記row,columnは空きスペースがあっても、上記ルール通りに順番に埋めていく
- denseは、空きスペースが生じた際はそれを埋めるように逆戻りして配置される
