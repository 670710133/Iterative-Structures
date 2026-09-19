# ทำความรู้จักกับภาษา RUST
#### การติดตั้ง Rustup บน Linux ใช้คำสั่ง
```bash
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```
- คำสั่งนี้จะทำการดาวโหลด script และการติดตั้งเครื่องมือของ Rustupg เวอร์ชั่นที่ดีที่สุด

#### การติดตั้ง rustup บน window
1. เข้าไปที่ลิ้ง https://www.rust-lang.org/tools/install
2. ให้ดาวโหลด rustup-init.exe(X64) หรือ ARM64
3. เข้าไปที่ rustup-init.exe โดยที่มันจะแสดงหน้า command prompt มาให้
4. ให้เราทำการพิมเลข 1 ลงไป ระบบจะทำการดาวโหลดเครื่องมือที่ชื่อว่า Visual studio Installer
5. เข้าไปที่ Visual studio installer และทำการดาวน์โหลดเครื่องมือดังนี้ Visual Studio Community 2026
6. ให้คลิก Install และทำการเลือกหมวดหมู่ Desktop development with C++ จากนั้นกด Install ด้านล่างได้เลย
7. ถ้าทำการดาวน์โหลดเสร็จแล้วให้มาที่ powershell และพิมคำสั่งตามนี้ เพื่อเป็นการเช็คว่า rustup อยู่ในเครื่องของเราหรือยัง
```bash
rustc --version
cargo --version
```


## การใช้งาน Rust

#### การสร้าง project ใหม่
```bash
cargo new ชื่อโฟลเดอร์
```
- ระบบจะทำการสร้างโฟลเดอร์ตามชื่อที่เราพิมไว้ พร้อมทั้งโครงสร้างพื้นฐานและการตั้งค่า Git อัตโนมัติ

#### การสั่งรันโปรเจค
```bash
cargo run
```
- การบวนการทำงาน
    - compile code
    - สร้างไฟล์งานในโฟลเดอร์ target/debug/
    - แสดงผลใน Terminal ทันที

#### คำสั่งอื่นๆ
1. cargo buid --> compile code only
2. cargo check --> ตรวจสอบข้อผิดพลาดของโค้ดแบบรวดเร็ว เช็ค syntax แบบรวดเร็ว
3. cargo build --release --> คอมไพล์โปรเจกต์สำหรับใช้งานจริง (จะเปิดการ Optimize โค้ดให้รันเร็วที่สุด ไฟล์จะถูกสร้างไว้ที่ target/release/)



# คำสั่ง GitHub เบื้องต้น
1. #### ตอนแอดเข้า GitHub ครั้งแรก
```bash
git init --> เริ่มสร้าง Repository ในเครื่อง

git add ไฟล์งาน --> เพิ่มงานเข้า github แค่งานเดียว

git add . --> เพิ่มงานเข้า github ทั้งหมด

git commit -m "Text" --> ยืนยันการเอาขึ้น Repository ตามด้วยข้อความว่าเราทำงานส่วนไหนไปบ้าง สามารถพิมเป็นภาษาไทยได้

git branch -M ชื่อ Branch --> สร้าง branch ของแต่ละคน

git checkout ชื่อ branch ที่เรากำลังไป --> ใช้ในกรณีที่เราจะไป branch อื่น

git remote add origin https://... --> เชื่อมต่อ repository ในเครื่องกับ github clound

git push -u origin ชื่อ branch --> ส่งงานที่เรา add เข้าไปขึ้น github ตาม branch ที่เราสร้างขึ้น 

git pull --> ดึงโค้ดเวอร์ชั่นล่าสุดจาก Github ลงมาอัปเดตในเครื่องของเรา

git merge --> คือการรวม branch ของเราและของเพื่อนเข้าได้กัน
```