---
title: "https ด้วย certbot บน express"
description: "จดไว้ กันลืม หลังๆนี่ได้ทำบ่อย"
date: "2019-09-08T17:30:00+07:00"
tags: ["node.js", "express", "certbot"]
image: "/images/certbot.svg"
---
![certbot](/images/certbot.svg)
# HTTPS ด้วย certbot บน express
พอดีว่าพักหลังๆได้เซทเซิฟเวอร์แล้วต้องทำ https พอจะมาทำอีกรอบก็ลืมไปแล้วว่าต้องทำอะไรบ้าง เลยจัดไว้ในนี้เลยละกัน เผื่อลืม

## install certbot
ก่อนจะทำการสร้าง certificate ก็ต้องดาวน์โหลด certbot มาใช้ก่อน เพื่อเป็น Agent ในการยืนยันโดเมนและเซิฟเวอร์ของเรา
ติดตั้ง epel (extra packages for enterprise linux), yum-utils และสุดท้าย พระเอกของเรา certbot
```bash
~$ yum install epel-release
~$ yum install yum-utils
~$ yum install certbot
```

## แล้วเว็บเซิฟเวอร์เราล่ะ
ด้วย ACME protocol ที่ agent ตัวนี้ใช้นั้น ต้องใช้ http server ในการยืนยันด้วย แน่นอนว่า certbot เองก็รู้ดีว่าเราขี้เกียจกันขนาดไหน เพียงแค่เรารันด้วย `--standalone` โหมด http server ก็จะถูกเปิดขึ้นใช้เฉพาะกิจเพื่อการยืนยันโดยเฉพาะ จากนั้นก็กรอกรายละเอียดสำหรับ Public key ของเรา เป็นอันเสร็จสิ้น

```bash
~$ certbot certonly --standalone
```

แต่ถ้ามีเซอร์วิสรันที่พอร์ท 80 อยู่แล้วก็ต้องปิดไปก่อน เพราะบอทของเราจะใช้ แต่ถ้าปิดไม่ได้จริงๆก็ให้ใช้แบบ webroot ยืนยันแทน ก็คือให้ยืนยันผ่านทาง static path ของเราที่สร้างขึ้นนั่นเอง
```bash
~$ certbot certonly --webroot ./well-known/acme
```

## รันแล้วไปไหน
หลังจาก certbot ทำการยืนยันโดเมนและเซิฟเวอร์เราเรียบร้อยแล้ว cert จะกองอยู่ที่ `/etc/letsencrypt/live/${domain}/` โดยเราจะใช้ `fullchain.pem` กับ `privkey.pem` ไปใส่ใน app ของเรา จะใช้ link หรืออะไรก็แล้วแต่สะดวกเรา

## express โลด
เอา path `privkey` `fullchain` ของเราไปใส่ในคอนฟิกของ express server ก็เป็นอันเสร็จสิ้น
```js
const privateKey  = fs.readFileSync(API_CONFIG.ssl_key, 'utf8')
const certificate = fs.readFileSync(API_CONFIG.ssl_cert, 'utf8')
const credentials = {key: privateKey, cert: certificate}

let httpsServer = https.createServer(credentials, app)
httpsServer.listen(
    API_CONFIG.port_https,
    API_CONFIG.listen_host,
    () => console.log(`https listen on port ${API_CONFIG.port_https}`)
)
```

## เหมือนจะเสร็จ แต่ยังไม่เสร็จ
cert ตัวนี้อายุสั้นเพียงสามเดือน เพราะฉะนั้นต้องคอยรีนิวเรื่อยๆ ก็ใช้ `certbot renew` แล้วใส่ cron แบบมักง่ายก็ได้

## อ้างอิง
 - [certbot](https://certbot.eff.org/lets-encrypt/centosrhel7-other) 
 - [how it works](https://letsencrypt.org/how-it-works/)
และ stack overflow อีกหลายมู้ที่จำไม่ได้แล้ว