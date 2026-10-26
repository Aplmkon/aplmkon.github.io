# Chrome

## 下载

在快捷链接页面 [Google Chrome](index.md) 包含了各平台的下载地址。

## 必装插件

1. 去除烦人的广告 [Adblock Plus](https://chrome.google.com/webstore/detail/cfhdojbkjhnklbpkdaibdccddilifddb)
2. 方便的密码管家 [LastPass](https://chrome.google.com/webstore/detail/hdokiejnpimakedhajhdlcegeplioahd)
3. 国内的网络必备 [ZeroOmega](https://chromewebstore.google.com/detail/proxy-switchyomega-3-zero/pfnededegaaopdmhkdmcofjmoldfiped)

## 搜索设置

### 让 Google 搜索不跳转到 .hk 页面

在地址栏输入 [https://www.google.com/ncr](https://www.google.com/ncr) 然后只要不清空 cookie 就会一直有效。

### 使用中文搜索

打开 [chrome://settings/searchEngines](chrome://settings/searchEngines) 页面，先选择使用其他，然后删除 `Google`,再新建 `Google Search Engine` 内容就使用下面的链接填充。

- 名称
  > Google
- 关键词
  > google.com
- 网址格式（用“%s”代替搜索字词）
  > `{google:baseURL}search?q=%s&hl=zh-CN&gl=CN`
