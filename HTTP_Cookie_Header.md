## Issues 
1. Warning `WARNING: Invalid cookie header: "Set-Cookie: dsc=6780cff8cfba3746284bf8e239dc3e82cda6d39c330346cb2e85fca26545f953; Path=/; Expires=Sat, 08 Oct 2016 05:04:50 GMT; Secure". Invalid 'expires' attribute: Sat, 08 Oct 2016 05:04:50 GMT`.

## Possible Solutions
1. [Set Cookie](http://stackoverflow.com/questions/13302245/getting-set-cookie-header). Reference as below: 
```
        RequestConfig globalConfig = RequestConfig.custom()
                .setCookieSpec(CookieSpecs.DEFAULT)
                .build();
        CloseableHttpClient httpClient = HttpClients.custom()
                .setDefaultRequestConfig(globalConfig)
                .build();
        RequestConfig localConfig = RequestConfig.copy(globalConfig)
                .setCookieSpec(CookieSpecs.STANDARD)
                .build();
        HttpGet httpGet = new HttpGet(url);
        httpGet.setConfig(localConfig); 

        // Request
        CloseableHttpResponse response = httpClient.execute(httpGet);
```
.
2. 
