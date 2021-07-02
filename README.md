# regularEX
Regular expression in some condition


### php 匯出 excel 時，內容含有香港文字
造成.xls檔案無法開啟，上傳google雲端後用google試算表開啟也會有亂碼

```php
    // 過濾 標準unicode 以外的字符
    private function filter($text)
    {
        $exception = preg_replace('/[\x{0020}-\x{FFEF}]+/u', '_', $text);
        return ($exception === '_') ? $text : str_replace(explode('_', $exception), '', $text);
    }
```


### 判斷 ig 的貼文留言內容是否有標記其他用戶
因 ig api 尚未提供被標記的用戶資訊，僅能以文字中的 @xxx 來判斷是否為有效標記

```php
    // 判斷留言中的 @xxx 數量
    private function countTagMan(string $commentText)
    {
        $tagMen = [];
        preg_match_all('/(^|\s)@[a-zA-Z0-9_][a-zA-Z0-9_.]+/', $commentText, $tagMen);

        return count($tagMen[0]);
    }
```
