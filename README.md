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
    
`    for ใช้สำหรับวนผ่านค่าทีละตัวจากสิ่งที่สามารถแปลงเป็น iterator ได้ เช่น array, Vec, range หรือ iterator adapter`
    
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

### 4.4 `Range — .. และ ..=`

`    while คือการวนซ้ำที่ตรวจสอบเงื่อนไขก่อนทำงานแต่ละรอบ ถ้าเงื่อนไขเป็น true จึงทำงานต่อ แต่ถ้าเป็น false จะจบลูป เหมาะกับสถานการณ์ที่ "เงื่อนไขเป็นตัวกำหนดว่าควรทำต่อหรือไม่" โดยตรง ทำให้โครงสร้างของโปรแกรมอ่านง่าย`

while ช่วยในการแก้ปัญหา

`    - การวนจนกว่าค่าจะถึงขีดจำกัด`

`    - การตรวจสอบสถานะซ้ำ ๆ`

`    - การทำงานที่จำนวนรอบขึ้นอยู่กับเงื่อนไข`

`    - ลดการเขียน loop ร่วมกับ if และ break ที่ซ้ำซ้อน`

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
4. `[แหล่งอ้างอิงเพิ่มเติม]`

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
