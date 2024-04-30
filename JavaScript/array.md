## some()
- 配列内の、少なくとも1つの要素が指定された条件（テスト関数）を満たすかどうかをbooleanで返す
```javascript
    //GASで書いたやつ
articlelist.forEach(function(articleItem){
    const title = articleItem.getChild('title', nameSpace).getText();
    // スプレッドシートに格納されている記事を除外（タイトルで照合）
    if(dataSheetList.some(data => data.title === title)){
      console.log('記事を除外：' + title);
      return;
    }
...
}
```
