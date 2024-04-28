## .exec() 
- 正規表現と一致するものを検索し、結果の配列を返す
### 配列のプロパティ
- [0]　対象を包含するパターンを含む全文
- [1] 対象（複数あれば、以下連番で続く）
- index　インデックス
- input 入力値
- indices
- groups
```javascript
const regex = /<p>(.*?)<\/p>/s;
const match = regex.exec(description);
```
