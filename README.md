# Iterative Structures

> **Topic No.:** `7`  
> **Topic Name:** `Iterative Structures`  
> **Group No.:** `7`

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | `นายนวภูมิ ปั้นหลวง` | `670710133` | `@670710133` | Concept + Code |
| 2 | `นายปฏิภาณ นิลวงค์` | `670710134` | `@670710134` | Code + Demo |
| 3 | `นายปรเมทร์ ฟองดา` | `670710135` | `@670710135` | Rust vs Other Language + PPL |
| 4 | `นายปิยวัฒน์ เดียนประไพ` | `670710136` | `@670710136` | Exercises + Common Mistakes |

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญของโครงสร้างแบบ Iterative ได้]`
2. `[เขียนโปรแกรม Rust ที่เป็นโครงสร้างแบบ Iterative ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบโครงสร้างแบบ Iterative ของภาษา Rust กับภาษาอื่นได้]`

---

## 3. Introduction

<!-- อธิบายว่า Topic นี้คืออะไร มีความสำคัญอย่างไร และใช้แก้ปัญหาอะไรในการเขียนโปรแกรม-->

`    Iterative Structures คือโครงสร้างควบคุมที่ทำให้โปรแกรมทำคำสั่งเดิมซ้ำตามเงื่อนไขหรือข้อมูลที่กำหนด ใน Rust รูปแบบที่ใช้ทั่วไปคือ loop, while, for และ while let โดย for ทำงานร่วมกับ iterator เพื่อดึงข้อมูลทีละค่า`

`    แนวคิดนี้มาจากความต้องการลดการเขียนคำสั่งซ้ำ ๆ เช่น แทนที่จะเขียน println! หลายครั้ง เราใช้ลูปเพื่อบอกโปรแกรมว่า “ทำคำสั่งนี้กับข้อมูลทุกตัว” หรือ “ทำซ้ำจนกว่าเงื่อนไขจะเป็นเท็จ”`


- ที่มา : https://doc.rust-lang.org/book/ch03-05-control-flow.html
---

## 4. Key Concepts

### 4.1 `loop`

**คำอธิบาย**
    
`    loop คือการวนซ้ำแบบไม่กำหนดเงื่อนไขสิ้นสุดไว้ที่หัวลูป โปรแกรมจะทำงานต่อไปจนกว่าจะพบ break Rust Reference ระบุว่า loop เป็น infinite loop โดยธรรมชาติ หากไม่มี break ก็จะไม่สิ้นสุดตามปกติ`
    
`    การที่ Rust ออกแบบ loop มา เพื่อให้สามารถกำหนดจุดสิ้นสุดของการวนซ้ำจากภายในกระบวนการทำงานได้อย่างชัดเจน แทนที่จะบังคับให้เงื่อนไขอยู่ที่หัว loop เสมอ นอกจากนี้ Rust อนุญาตให้ loop คืนค่าผ่าน break value ได้ ทำให้ใช้เป็น expression ได้`

loop ช่วยในการแก้ไขปัญหา

`    - งานที่ไม่ทราบจำนวนรอบล่วงหน้า `

`    - โปรแกรมที่ต้องรอเหตุการณ์หรือข้อมูล `

`    - ลูปที่มีเงื่อนไขหยุดหลายจุด `

`    - การเขียนลูปที่ต้องคืนค่าผลลัพธ์ `

**ตัวอย่าง**

```rust
fn main() {
    let mut n = 1;

    loop {
        println!("{n}");

        if n == 3 {
            break;
        }

        n += 1;
    }
}
```

**Explanation**

`    โปรแกรมเริ่มจาก main() และกำหนด n = 1 โดยใช้ mut เพื่อให้สามารถเปลี่ยนค่าได้ จากนั้นเข้าสู่ loop เพื่อทำงานซ้ำ โดยแสดงค่าของ n แล้วตรวจสอบว่า n == 3 หรือไม่ หากยังไม่เท่ากับ 3 จะเพิ่มค่า n ทีละ 1 แล้ววนซ้ำอีกครั้ง เมื่อ n มีค่าเป็น 3 โปรแกรมจะแสดงเลข 3 แล้วทำคำสั่ง break เพื่อออกจาก loop และจบการทำงาน โดยผลลัพธ์คือ 1, 2, 3`

---

### 4.2 `while`

`    while คือการวนซ้ำที่ตรวจสอบเงื่อนไขก่อนทำงานแต่ละรอบ ถ้าเงื่อนไขเป็น true จึงทำงานต่อ แต่ถ้าเป็น false จะจบลูป เหมาะกับสถานการณ์ที่ "เงื่อนไขเป็นตัวกำหนดว่าควรทำต่อหรือไม่" โดยตรง ทำให้โครงสร้างของโปรแกรมอ่านง่าย`

while ช่วยในการแก้ปัญหา

`    - การวนจนกว่าค่าจะถึงขีดจำกัด`

`    - การตรวจสอบสถานะซ้ำ ๆ`

`    - การทำงานที่จำนวนรอบขึ้นอยู่กับเงื่อนไข`

`    - ลดการเขียน loop ร่วมกับ if และ break ที่ซ้ำซ้อน`

**ตัวอย่าง**

```rust

fn main(){
    let mut n = 1;

    while n <= 3 {
        println!("{n}");
        n += 1;
    }
}
```

**Explanation**

`    โปรแกรมเริ่มจาก main() และกำหนดค่า n = 1 โดยใช้ mut เพื่อให้สามารถเปลี่ยนค่าได้ จากนั้นใช้ while ตรวจสอบว่า n <= 3 หรือไม่ หากเป็นจริง โปรแกรมจะแสดงค่า n แล้วเพิ่มค่าขึ้นทีละ 1 จากนั้นวนกลับไปตรวจสอบเงื่อนไขอีกครั้ง เมื่อ n มีค่าเป็น 4 เงื่อนไขเป็นเท็จ จึงหยุดการทำงานของ while และจบโปรแกรม โดยผลลัพธ์คือ 1, 2, 3`

---

### 4.3 `for`

**คำอธิบาย**
    
`    for คือโครงสร้างวนซ้ำที่ใช้สำหรับนำข้อมูลแต่ละตัวในชุดข้อมูล เช่น Array, Vector หรือ Range มาประมวลผลทีละตัว โดย Rust จะนำข้อมูลนั้นมาเป็น Iterator แล้วส่งค่าออกมาทีละตัวจนกว่าข้อมูลจะหมด จึงช่วยให้เราไม่ต้องจัดการจำนวนรอบหรือ index ด้วยตนเอง`
    
`    การที่ Rust ออกแบบ loop มา เพื่อให้สามารถกำหนดจุดสิ้นสุดของการวนซ้ำจากภายในกระบวนการทำงานได้อย่างชัดเจน แทนที่จะบังคับให้เงื่อนไขอยู่ที่หัว loop เสมอ นอกจากนี้ Rust อนุญาตให้ loop คืนค่าผ่าน break value ได้ ทำให้ใช้เป็น expression ได้`

for ใช้แนวคิด iterator เพื่อให้การวนข้อมูล

`    - อ่านง่าย `

`    - ทำงานกับ collection ได้อย่างเป็นระบบ `

`    - ลดการใช้ index ด้วยตนเอง `

`    - ลดความเสี่ยงจากการเข้าถึงตำแหน่งนอกขอบเขต `

`    - ทำงานร่วมกับ ownership และ borrowing ได้อย่างปลอดภัย `

**ตัวอย่าง**

* การใช้ for กับ array
```rust
fn main() {
    let numbers = [10, 20, 30];

    for number in numbers {
        println!("{number}");
    }
}
```
**Explanation**

`    โปรแกรมเริ่มจาก main() และสร้างอาร์เรย์ numbers ที่เก็บค่า 10, 20, 30 จากนั้นใช้ for วนอ่านค่าทีละตัว โดยนำค่ามาเก็บไว้ในตัวแปร number แล้วใช้ println! แสดงค่าบนหน้าจอจนครบทุกตัว ผลลัพธ์คือ 10, 20, 30`

* การใช้ for กับ range
```rust
fn main() {
    for number in 1..=3 {
        println!("{number}");
    }
}
```

**Explanation**

`    โปรแกรมเริ่มจาก main() แล้วใช้ for วนค่าตั้งแต่ 1 ถึง 3 โดย 1..=3 หมายถึงรวมเลข 3 ด้วย ในแต่ละรอบจะนำค่า number มาแสดงผลด้วย println! จึงได้ผลลัพธ์เป็น 1, 2, 3`

---

### 4.4 `break`

`    break เป็นกลไกสำหรับ ยุติ loop ก่อนที่จะวนจนถึงจุดสิ้นสุดตามปกติ และสามารถระบุ label เพื่อออกจาก loop ชั้นนอกได้ โดย break สามารถใช้ได้กับ loop, while และ for`

`    ในบางครั้งโปรแกรมพบผลลัพธ์ที่ต้องการก่อนถึงเงื่อนไขปกติ Rust จึงนำหลักการของ break มาหยุดการทำงานของโปรแกรมทันทีแทนที่จะประมวลผลข้อมูลต่อโดยไม่จำเป็น เพื่อป้องกันการพบเงื่อนไขที่ผิดพลาด หยุดการค้นหาเมื่อพบข้อมูลที่ต้องการแล้ว และลดการทำงานที่ไม่จำเป็น`

**ตัวอย่าง**

```rust

fn main(){
    for n in 1..=10 {
        if n == 5 {
            break;
        }
        println!("{n}");
    }
}
```

**Explanation**

`    โปรแกรมใช้ for วนค่าตั้งแต่ 1 ถึง 10 และตรวจสอบว่า n เท่ากับ 5 หรือไม่ หากยังไม่ถึง 5 จะแสดงค่า n ออกทางหน้าจอ แต่เมื่อ n เท่ากับ 5 จะทำคำสั่ง break เพื่อหยุดการวนซ้ำทันที ดังนั้นผลลัพธ์คือ 1, 2, 3, 4`

---

### 4.5 `continue`

**คำอธิบาย**
    
`    continue ใช้สำหรับ ข้ามการทำงานที่เหลือของรอบปัจจุบัน แล้วส่งการควบคุมกลับไปที่หัวของ loop เพื่อเริ่ม iteration ถัดไป เพื่อให้สามารถข้ามข้อมูลบางรายการโดยไม่ต้องหยุด loop ทั้งหมด`

continue ช่วยในการแก้ไขปัญหา

`    - ข้ามข้อมูลที่ไม่ต้องการประมวลผล `

`    - กรองค่าบางประเภท `

`    - ลดระดับการซ้อนของโค้ด `

`    - ทำให้เงื่อนไขผิดปกติจบเร็ว `

**ตัวอย่าง**

```rust
fn main() {
    for number in 1..=5 {
        if number % 2 == 0 {
            continue;
        }

        println!("{number}");
    }
}
```

**Explanation**

`    โปรแกรมเริ่มจาก main() ใช้ for วนค่าตั้งแต่ 1 ถึง 5 และตรวจสอบว่า number เป็นเลขคู่หรือไม่ด้วย number % 2 == 0 หากเป็นเลขคู่จะใช้ continue เพื่อข้ามรอบนั้นไป แต่ถ้าเป็นเลขคี่จะแสดงค่าบนหน้าจอ ดังนั้นผลลัพธ์คือ 1, 3, 5`

---

### 4.6 `Nested Loops`

`    Nested Loop คือการเขียนลูปไว้ภายในลูปอีกชั้นหนึ่ง โดยทุกครั้งที่ outer loop ทำงาน 1 รอบ inner loop จะทำงานตามที่กำหนด นอกจากนี้ยังสามารถใช้ทั้ง break และ continue ได้ โดยถ้าไม่ระบุ label คำสั่งทั้งสองจะมีผลกับ ลูปชั้นในสุด ที่ครอบคำสั่งนั้นอยู่ หากต้องการควบคุมลูปชั้นนอก ให้ใช้ loop label เช่น 'outer `

`    Nested Loop เหมาะกับข้อมูลสองมิติ เช่น ตาราง, กระดานเกม, matrix, แถว–คอลัมน์ หรือการเปรียบเทียบข้อมูลเป็นคู่`

**ตัวอย่าง**

```rust
fn main() {
    for row in 1..=2 {
        for column in 1..=3 {
            println!("Row : {row}, Column : {column}");
        }
    }
}
```

**Explanation**

`    โปรแกรมใช้ for ซ้อนกัน 2 ชั้น โดย row วนค่าตั้งแต่ 1 ถึง 2 และในแต่ละรอบ column จะวนค่าตั้งแต่ 1 ถึง 3 จากนั้นแสดงค่า row และ column ออกทางหน้าจอ ทำให้แต่ละ row แสดง column ครบทั้ง 3 ค่า ผลลัพธ์คือ 6 บรรทัด ได้แก่ Row 1 Column 1–3 และ Row 2 Column 1–3`

---


## 5. Important Syntax / Rules

| Syntax / Rule | Meaning | Example |
|---|---|---|
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |
| `[syntax/rule]` | `[ความหมาย]` | `[ตัวอย่าง]` |

### Important Rules

1. `[กฎสำคัญข้อที่ 1]`
2. `[กฎสำคัญข้อที่ 2]`
3. `[กฎสำคัญข้อที่ 3]`

---

## 6. Runnable Code Examples

> **ข้อกำหนด:** Code ทุกตัวต้อง Compile และ Run ได้จริงก่อนนำมาใส่ในเอกสาร

### Example 1 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code ทีละส่วนที่สำคัญ]`

---

### Example 2 — `[ชื่อ Example]`

**Purpose:** `[ต้องการสาธิตอะไร]`

```rust
fn main() {
    // Write your runnable Rust code here
}
```

**Expected Output**

```text
[expected output]
```

**Explanation**

`[อธิบาย code]`

---

## 7. Common Mistakes

### Mistake 1 — `[ชื่อข้อผิดพลาด]`

**Problem**

`[อธิบายปัญหา]`

**Incorrect Code**

```rust
// Incorrect example
```

**Correct Code**

```rust
// Correct example
```

**Why?**

`[อธิบายสาเหตุ]`

---

### Mistake 2 — `[ชื่อข้อผิดพลาด]`

**Problem**

`[อธิบายปัญหา]`

**Incorrect Code**

```rust
// Incorrect example
```

**Correct Code**

```rust
// Correct example
```

**Why?**

`[อธิบายสาเหตุ]`

---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

---

### Exercise 2 — `[ชื่อโจทย์]`

**Problem**

`[เขียนโจทย์]`

**Hint**

`[คำใบ้]`

**Solution**

```rust
// Solution code
```

**Explanation**

`[อธิบายแนวทางแก้]`

---

## 9. PPL Perspective

> **ส่วนนี้เป็นหัวใจของรายวิชา Principles of Programming Languages**

วิเคราะห์ Topic นี้ในมุมมองของ Programming Languages

### 9.1 Syntax

`[Topic นี้เกี่ยวข้องกับ syntax อย่างไร]`

### 9.2 Semantics

`[คำสั่ง/construct เหล่านี้มีความหมายหรือพฤติกรรมอย่างไร]`

### 9.3 Type System

`[เกี่ยวข้องกับ type system อย่างไร ถ้ามี]`

### 9.4 Memory / Resource Management

`[เกี่ยวข้องกับ memory หรือ resource management อย่างไร ถ้ามี]`

### 9.5 Abstraction / Other PPL Concepts

`[อธิบาย abstraction, scope, binding, paradigm หรือแนวคิด PPL อื่นที่เกี่ยวข้อง]`

### 9.6 Why Rust?

`[Rust ใช้แนวคิดนี้เพื่อเพิ่ม safety, reliability หรือ performance อย่างไร]`

---

## 10. Rust vs. Other Language

**Comparison Language:** `[Python / C / C++ / Java / Kotlin / ...]`

| Aspect | Rust | Other Language |
|---|---|---|
| Syntax | `[อธิบาย]` | `[อธิบาย]` |
| Semantics / Behavior | `[อธิบาย]` | `[อธิบาย]` |
| Type System | `[อธิบาย]` | `[อธิบาย]` |
| Memory Management | `[อธิบาย]` | `[อธิบาย]` |
| Safety | `[อธิบาย]` | `[อธิบาย]` |

### Rust Example

```rust
// Rust code
```

### `[Other Language]` Example

```python
# Other language code
```

### Analysis

`[อธิบายความแตกต่างที่สำคัญ และเหตุผลด้านการออกแบบภาษา]`

---

## 11. Teach Your Topic

การนำเสนอมีสมาชิก **4 คน คนละประมาณ 5 นาที**

| Member | Responsibility | Time |
|---|---|---:|
| Member 1 | Concept + Short Code Illustration | 5 min |
| Member 2 | Detailed Code + Live Demo | 5 min |
| Member 3 | Rust vs Other Language + PPL Analysis | 5 min |
| Member 4 | Exercises + Common Mistakes + Challenge | 5 min |

### Individual Contribution

**Member 1**

`[สิ่งที่รับผิดชอบ]`

**Member 2**

`[สิ่งที่รับผิดชอบ]`

**Member 3**

`[สิ่งที่รับผิดชอบ]`

**Member 4**

`[สิ่งที่รับผิดชอบ]`

> สมาชิกทุกคนต้องสามารถอธิบาย Code ของกลุ่มได้ ไม่ใช่เฉพาะส่วนที่ตนเองเขียน

---

## 12. References

> แนะนำให้มีอย่างน้อย **4 แหล่งอ้างอิง** และควรใช้เอกสารทางการเป็นหลัก

1. `[The Rust Programming Language — Rust Book]`
2. `[Rust by Example / Rust Reference]`
3. `[Official documentation ที่เกี่ยวข้องกับ Topic]`
   
<!-- ของเราเพิ่มเติม (เคิร์ส) / บางอันที่ใส่ตรงที่มาในหัวข้อมารวมที่นี้ -->

4. https://doc.rust-lang.org/reference/expressions/loop-expr.html
5. https://doc.rust-lang.org/book/ch03-05-control-flow.html
6. https://mitaa.github.io/rust/doc/book/loops.html

---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
|---|---|---|
| `[เช่น ChatGPT]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |
| `[AI tool]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |

### Declaration

- [ ] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [ ] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
|---|---:|---:|---:|---:|---|
| Member 1 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 4 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |

### Teamwork Reflection

**How did your team collaborate?**

`[อธิบายกระบวนการทำงานร่วมกัน]`

**Problems encountered**

`[ปัญหาที่พบ]`

**How did you solve them?**

`[วิธีแก้ปัญหา]`

---

## 15. Final Checklist

- [ ] Learning Objectives ครบ 3–4 ข้อ
- [ ] Key Concepts ครบถ้วน
- [ ] Syntax / Rules
- [ ] Runnable Code Examples
- [ ] Code Compile และ Run ได้จริง
- [ ] Common Mistakes
- [ ] Exercises 2 ข้อ พร้อม Solutions
- [ ] PPL Perspective
- [ ] Rust vs Other Language
- [ ] References อย่างน้อย 4 แหล่ง
- [ ] AI Usage Declaration
- [ ] GitHub Contribution
- [ ] สมาชิกทั้ง 4 คนมีส่วนร่วม
- [ ] สมาชิกทั้ง 4 คนพร้อมนำเสนอคนละ 5 นาที
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ของกลุ่มได้

---

## Submission Information

**Repository:** `[GitHub repository URL]`

**Chapter Path:** `[เช่น chapters/01-introduction/]`

**Final PR:** `#[PR number]`

**Submitted by:** `[Group XX]`

**Date:** `[YYYY-MM-DD]`
