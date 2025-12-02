# TRADING PLATFORM  
## Space Function Specification  
ระบบเทรด Bitcoin แบบ Minute Trading (Private Trading Space)

**วันที่เขียน**: 2 ธันวาคม 2568  

---

## 1. User Management Module

| Function            | รายละเอียด                                                                       
|---------------------|-----------------------------------------------------------------------------------------------------------------------------
| Register            | สมัครสมาชิก email + password (bcrypt)              
| Login               | ล็อกอิน → ได้ JWT Access + Refresh Token                                    
| Logout              | ลบ refresh token ออกจากระบบ                                                 
| Forgot Password     | ส่งลิงก์ reset password ทางอีเมล                                             
| Reset Password      | รีเซ็ตรหัสผ่านด้วย token                                                                            
| Profile Management  | แก้ไขชื่อ, รูป, เปลี่ยนรหัสผ่าน, เปิด/ปิด 2FA (Google Authenticator)          

---

## 2. Wallet Module

| Function               | รายละเอียด                                                                                
|------------------------|---------------------------------------------------------------------------------------------------------------------------
| Deposit (Fiat)         | ฝากเงินบาทผ่าน (MOCKUP)                                           
| Withdraw (Fiat)        | ถอนเงินบาทเข้าบัญชีธนาคาร  (MOCKUP)                                                             
| Balance                | แสดงยอดเงินในกระเป๋า                                                
| Transaction History    | รายการฝาก-ถอน-เทรดทั้งหมด                                                                
| Profit/Loss Report     | รายงานกำไร-ขาดทุน รายวัน/สัปดาห์/เดือน

---

## 3. Trading Interface & Engine (Minute Trading)

| Function              | รายละเอียด                                                                
|-----------------------|----------------------------------------------------------------------------------------------------------------------------
| Real-time Chart       | กราฟแท่งเทียน 1 นาทีอัพเดทแบบ real-time                                    
| Trade                 | ระบบเทรดซื้อขาย 
| Trade History         | ประวัติคำสั่งซื้อขายทั้งหมด
---

## 4. Bitcoin Price Feed (3 Sources + Recovery)

| Function           | API / WebSocket                                                   
|--------------------|----------------------------------------------------------------------
| Fetch Price Feed   | หาแหล่งดึงราคา Bitcoin หลากหลายแหล่งเพื่อนำราคา Bitcoin มาเก็บในระบบ
| Recovery Failed    | หา Solution เมื่อแหล่งดึงราคาล้มเหลว ป้องกันไม่ให้ราคาสูญหาย
---

## 5. Admin & Backoffice Module (ระบบหลังบ้าน)

| Function                    | รายละเอียด |
|-----------------------------|------------------------------------------------------------|
| Admin Login                 | แยก route `/admin` มี 2FA บังคับ + IP Whitelist (optional) 
| User Management             | ค้นหา/ระงับ/ปลดระงับบัญชี, ดูประวัติการล็อกอิน, บังคับรีเซ็ตรหัสผ่าน 
| Wallet Management           | ปรับยอดเงินมือ (credit/debit), เหตุผล + audit log       
| Transaction Monitoring      | ดูรายการฝาก-ถอนทั้งหมด, อนุมัติ/ปฏิเสธการถอน (MOCKUP หรือจริง) 
| Trade Monitoring            | ดูออเดอร์ทั้งหมดแบบ real-time
| System Configuration        | ตั้ง % Fee, เลเวอเรจสูงสุด, Maintenance Mode              
| Audit Log                   | บันทึกทุกการกระทำของ Admin (who, what, when, IP)        

---
