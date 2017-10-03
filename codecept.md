# 安裝 codecept

想練習一下 TDD 開發模式，所以嘗試安裝了 codecept。

第一次安裝失敗是因為記憶體不夠（？）。以 AWS 後台重開機解決。

之後在根目錄執行

```bash
composer require "codeception/codeception" --dev
```

第一次執行 codecept 的時候，會要求執行

```
vendor/bin/codecept bootstrap
```

以開啟 codecept。

之後會顯示

```bash
 Codeception is installed for acceptance, functional, and unit testing
```

下一步，執行

```
vendor/bin/codecept run
```

由於我們什麼測試都沒有放，會顯示：

```bash
Acceptance Tests (0) -----------------------------------------------------------
--------------------------------------------------------------------------------

Functional Tests (0) -----------------------------------------------------------
--------------------------------------------------------------------------------

Unit Tests (0) -----------------------------------------------------------------
--------------------------------------------------------------------------------


Time: 81 ms, Memory: 11.00MB

No tests executed!
```



