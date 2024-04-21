
# 明示的なグリッドの指定量を超えたアイテム配置は暗黙的なグリッド（自動配置）により配置される
- grid-template-columns（明示的なグリッド）で２列指定した上で、grid-auto-flow:column(暗黙的なグリッド）を指定した場合
- アイテムが３つ以上入った場合、３列目以降はautoで配置される
｛
　display:grid;
 grid-template-columns: auto 1fr;
 grid-auto-flow:column;
｝
