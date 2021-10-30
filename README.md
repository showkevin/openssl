# Private Key (私鑰)

>產生私鑰 (PEM 格式)
```
openssl genrsa -out private.key 2048
```

# Public Key (公鑰)

>產生公鑰 (PEM 格式)
```
openssl rsa -in  private.key -pubout -out public.key
```

# CSR 文件

>產生CSR 文件 (PEM 格式)
```
openssl req -new -key private.key -out csr.pem
```

- Country Name (2 letter code) [AU]:TW
- State or Province Name (full name) [Some-State]:Taiwan
- Locality Name (eg, city) []:Taipei
- Organization Name (eg, company) [Internet Widgits Pty Ltd]:TW ABC LTD
- Organizational Unit Name (eg, section) []: (可空白)
- Common Name (eg, your name or your server's hostname) []:www.twabc.com.tw
- Email Address []:(可空白)

>CSR 說明
- Country name: 二字元國碼。
- State or Province Name: 地區或洲的名稱; 請不要用縮寫。
- Locality Name: 城市名稱。
- Organization Name: 您的組織 (公司) 英文名稱，此欄位在 標準型 SSL 憑證 非必要 ，但是 進階型 與 商業型 SSL 憑證則是必要欄位。
- Organization Unit Name: 您的部門名稱，例如資訊部。
- Common Name: 您要簽署的名稱。
- Email Address: 您的電子信箱位址。此欄位為非必要，但是建議填寫。
- A challenge password: 建議保留空白即可。
- An optional company name: 建議保留空白即可。

# 憑證

>生成自簽憑證
```
openssl x509 -req -days 365 -in csr.pem -signkey private.key -out abc.crt
```



# 轉憑證格式

>DER To PEM
```
openssl x509 -inform DER -in abc.cer -outform PEM -out abc.pem
```

>查看憑證內容
```
openssl x509 -text -in abc.pem -noout
```


