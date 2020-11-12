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
