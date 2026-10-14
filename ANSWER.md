# ANSWER — พัฒน์นรี เรืองดิษฐ์ 671540005025-5

- Platform: Vercel
- Production URL: https://ksu-coffee-671540005025-5-ljei4riwp-plewmobile06-webs-projects.vercel.app/

## คำตอบ

1. เลือกแพลตฟอร์ม Vercel ซึ่งรันโค้ดด้วยโมเดลแบบ Serverless Functions บน production ไฟล์ server.js ไม่ได้ถูกใช้งานโดยตรงแบบเซิร์ฟเวอร์ปกติตลอดเวลา แต่ Vercel จะแปลงโครงสร้าง API ให้เป็น Serverless Endpoint ตามสถาปัตยกรรมของแพลตฟอร์ม

2. ตั้งค่า STUDENT_ID บน Vercel ที่เมนู Settings > Environment Variables ห้าม commit ไฟล์ .env เพราะมีข้อมูลความลับที่ไม่ควรเปิดเผยสาธารณะ หาก /api/info แสดง NOT SET เกิดจากการลืมตั้งค่า Environment Variable บนแพลตฟอร์ม หรือตั้งค่าแล้วแต่ยังไม่ได้ทำการ Deploy ใหม่

3. ครั้งแรก 0.45 วินาที / ครั้งที่สอง 0.08 วินาที — ครั้งแรกใช้เวลานานกว่าเพราะเกิด Cold Start เนื่องจาก Serverless Instance เพิ่งถูกเรียกใช้งานเป็นครั้งแรก ส่วนครั้งที่สอง Instance ทำงานอยู่แล้ว (Warm Start) จึงตอบสนองได้เร็วกว่ามาก

4. เมื่อสั่ง git push ทาง GitHub จะส่ง Webhook ไปแจ้ง Vercel ให้ทำการดึงโค้ดล่าสุดไป Build และ Deploy ให้อัตโนมัติ ทำให้หน้าเว็บเปลี่ยนเป็น Menu v2 และค่า commit ใน /api/info ตรงกับ git log ล่าสุด

5. นำระบบในข้อ 1 มา deploy บน Vercel ตรง ๆ ไม่ได้ เพราะ Vercel รองรับเฉพาะ Web App/Static/Serverless ไม่รองรับการรัน Docker Compose Daemon แบบ Multi-container ที่ต้องรันค้างไว้ หากต้องการใช้ Compose ต้องไป deploy บนแพลตฟอร์มประเภท Container/VM เช่น Render หรือ Railway