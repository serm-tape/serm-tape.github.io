---
title: "ข้อมูลผู้เล่นแบบย่อในโปรเจค lightstone"
description: "ตามนั้น"
date: "2017-05-07T20:32:00+07:00"
tags: ["lightstone", "education", "idea", "lightstone-progess"]
image: "/images/short-char-view.png"
---
# ข้อมูลตัวละครแบบย่อในโปรเจค LightStone
ผ่านมาจากวันหยุดแรงงาน สัปดาห์นี้ก็ได้วันหยุดอีกวันก็คือวันฉัตรมงคล ถึงแม้เค้าจะยกเลิกกันไปแล้ว แต่บริษัทเราเห็นใจพนักงานที่เล่นลายาวกันไปแล้วเลยไม่ยกเลิก ไปหักวันหยุดอื่นเอา ทำให้เราได้มีเวลาทำโปรเจค LightStone ต่ออีกหน่อย 

เนื่องจากว่าวันศุกร์หมดไปกับเกม วันเสาร์หมดไปกับวันเกิดพี่ชาย เหลือวันเดียว เลยหาอะไรเล็กๆจุ๋มๆจิ๋มๆจากที่ออกแบบไว้ในกระดาษมาดู ส่วนที่น่าจะทำได้ไม่ยากก็น่าจะเป็นส่วนหัว ที่บอกข้อมูลตัวละครผู้เล่นแบบย่อๆ ว่าชื่ออะไร เป้าหมายคืออะไร มีรูปหนึ่งรูป แล้วก็เลเวลกับค่าประสบการณ์ ทำไปสักพักก็ติดเรื่องจะให้ Element มันชิดซ้ายกับชิดกว่าพร้อมกัน เหมือนจะจำได้ลางๆว่า float left right อะไรสักอย่าง ความพลาดก็คือ เราดันไปใช้ตัวนี้ display: float แล้วก็เลยไม่เวิร์ค เราก็พยายามเล่นท่าแปลกๆอีกสองสามท่า แล้วรู้สึกว่าไม่เวิค สุดท้ายเปิดกูเกิ้ล เราก็ได้เฉลยมาว่ามันคือ float: right แล้วปาฏิหาริย์ก็บังเกิด ทุกอย่างดูดีขึ้นมาทันที
![short-char-view](/images/short-char-view.png)

รูปเราตัดสินใจใช้เป็นไอคอนของอาชีพนั้นๆ ใส่ชื่อและอาชีพในฝันลงไป ปิดท้ายด้วยเลเวลด้านขวา ส่วนด้านล่างเป็นแถบค่าประสบการณ์ ลองดูหลายๆสีแล้ว สีนี้ดูเหมาะสมที่สุดในสายตาเรา ก็เลยจัดการคอมมิท และปิดงานในวันหยุดยาวของช่วงนี้ไป