# Rust Tutorial Project — Principles of Programming Languages

> **สำหรับนักศึกษา:** ใช้ไฟล์นี้เป็น Template สำหรับจัดทำบทเรียน Rust ของกลุ่ม  
> **Topic No.:** `7`  
> **Topic Name:** `[Iterative Structures]`  
> **Group No.:** `7`

---

## 1. Members

| # | Name | Student ID | GitHub Username | Main Responsibility |
|---|---|---|---|---|
| 1 | `[ชื่อ-นามสกุล]` | `[รหัส]` | `@[username]` | Concept + Code |
| 2 | `[ชื่อ-นามสกุล]` | `[รหัส]` | `@[username]` | Code + Demo |
| 3 | `[ปรเมทร์ ฟองดา]` | `[670710135]` | `@[670710135]` | Rust vs Other Language + PPL |
| 4 | `[นาย ปิยวัฒน์ เดียนประไพ]` | `[670710136]` | `@[670710136]` | Exercises + Common Mistakes |

---

## 2. Learning Objectives

หลังจากศึกษา Topic นี้แล้ว ผู้เรียนสามารถ:

1. `[อธิบายแนวคิดสำคัญได้]`
2. `[เขียนโปรแกรม Rust ที่เกี่ยวข้องได้]`
3. `[วิเคราะห์พฤติกรรม/กฎของภาษาได้]`
4. `[เปรียบเทียบ Rust กับภาษาอื่นได้]`

---

## 3. Introduction

อธิบายว่า Topic นี้คืออะไร มีความสำคัญอย่างไร และใช้แก้ปัญหาอะไรในการเขียนโปรแกรม

`[เขียนเนื้อหาที่นี่]`

---

## 4. Key Concepts

### 4.1 `[Concept 1]`

**คำอธิบาย**

`[อธิบายแนวคิด]`

**ตัวอย่าง**

```rust
fn main() {
    println!("Hello, Rust!");
}
```

**Explanation**

`[อธิบายว่า code ทำงานอย่างไร]`

---

### 4.2 `[Concept 2]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.3 `[Concept 3]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.4 `[Concept 4 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

---

### 4.5 `[Concept 5 — ถ้ามี]`

`[อธิบายแนวคิด]`

```rust
// Rust code
```

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

### Example 1 — `Counter-Controlled Loop`

**Purpose:** `สาธิตวิธีการใช้งาน For loop ทั้งแบบเดินหน้าและแบบถอยหลัง`
1. เขียนลูปบวกค่าอาเรย์ตำแหน่ง 0-10 รวมตำแหน่ง 10 ด้วย

```rust
fn main(){
    let mut count = 0;
    let mut numbers = Vec::new();
    for i in 0..=10 {
        count += i;
        numbers.push(count);
        println!("numbers = ", numbers[i]);
    }
}
```

**Expected Output**

```text
numbers = 0
numbers = 1
numbers = 3
numbers = 6
numbers = 10
numbers = 15
numbers = 21
numbers = 28
numbers = 36
numbers = 45
numbers = 55
```

**Explanation**

`[อธิบาย code ทีละส่วนที่สำคัญ]`
```text
ตัวแปร count เอาไว้ใช้บวกค่าสะสมในแต่ละตำแหน่ง ส่วนตัวแปร number เป็น vector ที่สามารถเพิ่มค่าได้แบบ Dynamic
for i in 0..=10 เป็นการวนลูปจากตัวที่ 0 ถึงตำแหน่งที่ 10 สาเหตุที่ต้องมีเท่ากับเพราะ เรารวมเลข10ไปด้วย
```

2. เขียนลูปนับถอยหลังจาก 10 ถึง 0 และลูปที่นับทีละ 2 จาก 0 ถึง 20
```rs
fn main(){
    for i in (0..=10).rev(){
        println!("i = {}", i);
    }

    println!("===========================");

    for i in (0..=20).step_by(2){
        println!("i = {}", i);
    }
}
```
**Expected Output**
```text
i = 10
i = 9
i = 8
i = 7
i = 6
i = 5
i = 4
i = 3
i = 2
i = 1
i = 0
===========================
i = 2
i = 4
i = 6
i = 8
i = 10
i = 12
i = 14
i = 16
i = 18
i = 20
```
`[อธิบาย code ทีละส่วนที่สำคัญ]`
```text
for i in (0..=10).rev() rev() ทำหน้าที่วนลูปแบบย้อนกลับ ถ้าไม่มีส่วนนี้ loop นี้จะทำการวนลูปไปด้านหน้าอย่างเดียว
.step_by() ทำหน้าที่นับทีละ จำนวนครั้งที่เราต้อการ
```
---

### Example 2 — `Logically-Controlled Loop`

**Purpose:** `สาธิตวิธีการใช้งาน loop และ while`

1. จำลองโปรแกรม "รับค่าจนกว่าจะได้ค่าที่ติดลบ" และทำการหยุดลูป
```rust
use std::io;
    fn main(){
    let mut number: i32 = 0;

    while number >= 0 {
        let mut msg = String::new();
        println!("Enter a number (negative number to stop):");

        io::stdin()
            .read_line(&mut msg)
            .expect("Failed input");

        number = match msg.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please type a valid number!");
                0
            }
        };
            if number > 0{
            println!("Input = {}", number);
        }
    }

        println!("Stopped! You entered negative number: {}", number);
    }
```

**Expected Output**

```text
Enter a number (negative number to stop):
5
Input = 5
Enter a number (negative number to stop):
10
Input = 10
Enter a number (negative number to stop):
15
Input = 15
Enter a number (negative number to stop):
20
Input = 20
Enter a number (negative number to stop):
-1
Stopped! You entered negative number: -1
```

**Explanation**

`[อธิบาย code]`
```text
ประกาศตัวแปร number เป็น int  

io::stdin()
    .read_line(&mut msg)
    .expect("Failed input"); ส่วนนี้เราจะทำการ Error Handling เพื่อทำการรับค่าที่เป็น String


number = match msg.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please type a valid number!");
                0
            }
        };
ส่วนนี้เราจะทำการแปลง String ที่รับเข้ามาให้กลายเป็น int โดยใช้การ Error Handling
match keyword นี้จะทำการเช็คค่าที่แปลงจากข้อความมาแล้ว
0 คือการคืนค่าที่เป็น 0 ออกไป

{} ทำหน้าที่เป็นตัวแทนในปริ้นค่าภายในตัวแปรออกมา
```

### Example 3 — `Iteration`
**Purpose:** `สาธิตวิธีการใช้งาน loop แบบ for each` 
1. เขียนโปรแกรมที่พิมพ์ "Name: Bob", "Name: Carol", "Name: Ted" จากคอลเลกชันของสตริงสามตัว
```rs
fn main(){
    let names = vec!["Bob", "Carol","Ted"];

    for name in names{
        println!("Names --> {}", name);
    }
}
```
**Expected Output**
```text
Names --> Bob
Names --> Carol
Names --> Ted
```
**Explanation**

`[อธิบาย code]`
```text
ตัวแปร names กำหนดให้เป็น Vector เพื่อให้ใสค่าที่เราต้องการเข้าไปได้
loop จะทำการวนลูปตามจำนวนสมาชิกที่อยู่ใน Vector การเขียน loop แบบนี้คล้ายลูปของภาษา python
```



---

## 7. Common Mistakes

### Mistake 1 — `[argument never used]`

**Problem**

`[อธิบายปัญหา]`
```text
ปํญหานี้เกิดจากการเขียน print ที่ผิด format จากตัวภาษา Rust
```

**Incorrect Code**

```rust
// Incorrect example
fn main(){
    let mut count = 0;
    let mut numbers = Vec::new();
    for i in 0..=10 {
        count += i;
        numbers.push(count);
        println!("numbers = ", numbers[i]);
    }
}
```

**Correct Code**

```rust
// Correct example
fn main(){
    let mut count = 0;
    let mut numbers = Vec::new();
    for i in 0..=10 {
        count += i;
        numbers.push(count);
        println!("numbers = {}", numbers[i]);
    }
}
```

**Why?**

`[อธิบายสาเหตุ]`
```text
เกิดจากการสับสนเรื่องของ format ในการปริ้นค่าในตัวแปร ออกมา
```
---

### Mistake 2 — `[unnecessary parentheses around `for` iterator expression AND  invalid left-hand side of assignment]`

**Problem**

`[อธิบายปัญหา]`
```text
เกิดจากการเขียน for ถอยหลังผิด Format และการ Assign ค่า ผิดฝั่ง
```

**Incorrect Code**

```rust
// Incorrect example
fn main(){
    for i in (10..=0){
        println!("i = {}", i);
    }

    println!("===========================");

    for i in (2=..20){
        println!("i = {}", i);
    }
}
```

**Correct Code**

```rust
// Correct example
fn main(){
    for i in (0..=10).rev(){
        println!("i = {}", i);
    }

    println!("===========================");

    for i in (0..=20).step_by(2){
        println!("i = {}", i);
    }
}
```

**Why?**

`[อธิบายสาเหตุ]`
```text
ใน Rust ตัวดำเนินการ Range แบบนับถอยหลังโดยตรงด้วย 10..=0 จะ ไม่ทำงาน เพราะ Range ใน Rust โดยเริ่มต้นจะสมมติว่าค่าเริ่มต้นต้อง น้อยกว่าหรือเท่ากับ ค่าสุดท้ายเสมอ

เขียนเครื่องหมายเทียบช่วงสลับตำแหน่งกัน ใน Rust ตัวดำเนินการนับรวมตัวท้าย คือ ..= ไม่ใช่ =..
```

---

### Mistake 3 — `[mismatched types]`

**Problem**

`[อธิบายปัญหา]`
```text
ปัญหาเกิดจาก ใส่ชนิดข้อมูลไม่ครบหรือใส่ parameter ไม่ครบ เขียนผิด format และ syntax
```

**Incorrect Code**

```rust
// Incorrect example
use std::io;
fn main(){
    let  number: i32 = 0;

    while number >= 0 {
        let  msg = String::new();
        println!("Enter a number (negative number to stop):");

        io::stdin()
            .read_line(msg)
            .expect("Failed input");

        if number > 0{
            println!("Input = {}", number);
        }
    }

    println!("Stopped! You entered negative number: {}", number);
}
    
```

**Correct Code**

```rust
// Correct example
 use std::io;
    fn main(){
    let mut number: i32 = 0;

    while number >= 0 {
        let mut msg = String::new();
        println!("Enter a number (negative number to stop):");

        io::stdin()
            .read_line(&mut msg)
            .expect("Failed input");

        number = match msg.trim().parse() {
            Ok(num) => num,
            Err(_) => {
                println!("Please type a valid number!");
                0
            }
        };
            if number > 0{
            println!("Input = {}", number);
        }
    }

        println!("Stopped! You entered negative number: {}", number);
    }
```

**Why?**

`[อธิบายสาเหตุ]`
read_line() ต้องการรับค่าแบบ &mut String เพื่อเขียนข้อมูลลงในบัฟเฟอร์สตริง แต่ในโค้ดส่ง msg ไปตรงๆ ซึ่งเป็นค่าธรรมดา

ตัวแปร number มีค่าเริ่มต้นเป็น 0 และ ไม่เคยถูกอัปเดตค่าเลย ในระหว่างการทำงานของลูป เพราะไม่ได้ดึงข้อมูลจาก msg มาแปลงเป็นตัวเลข ทำให้เงื่อนไข while เป็นจริงตลอดไป ส่งผลให้เกิด Infinite Loop

ตัวแปร number ไม่ได้ประกาศเป็น mut ทำให้อัปเดตค่าไม่ได้

การเรียกใช้ io::stdin() จำเป็นต้องดึงโมดูล std::io เข้ามาก่อน
---

### Mistake 4 — `[Option<&&str>` doesn't implement `std::fmt::Display]`

**Problem**

`[อธิบายปัญหา]`
```text
เกิดจากการใส่ พารามิเตอร์ไม่ครบ เขียนปริ้นผิด Format
```

**Incorrect Code**

```rust
// Incorrect example
fn main(){
    let names = vec!["Bob", "Carol","Ted"];
    for i in 0..3{
         println!("Names --> {}", names.get(i));
    }
}
```

**Correct Code**

```rust
// Correct example
fn main(){
    let names = vec!["Bob", "Carol","Ted"];
    for i in 0..3{
         println!("Names --> {}", names.get(i).unwarp());
    }
}
```

**Why?**

`[อธิบายสาเหตุ]`
```text
เมธอด .get(i) ในภาษา Rust ไม่ได้คืนค่าเป็นสตริงตรงๆ แต่จะคืนค่าเป็นชนิดข้อมูล Option<&str>
{} มีไว้สำหรับพิมพ์ข้อมูลระดับพื้นฐานทั่วไป แต่ Option ไม่ได้อิมพลีเมนต์ Display Trait ไว้ ทำให้ Error
```
---

## 8. Exercises

> จัดทำแบบฝึกหัด **2 ข้อ** ที่สอดคล้องกับ Topic และมีระดับความยากเหมาะสม

### Exercise 1 — `[เกมทายตัวเลข]`

**Problem**

`[เขียนโจทย์]`
```text
โปรแกรมสุ่มเลขลับ (ใช้ค่าคงที่แทนการสุ่มก็ได้ เช่น 37) แล้วให้ผู้เล่นทายจากชุดคำตอบที่กำหนดไว้ล่วงหน้า (เช่น 50, 25, 40, 37)

ข้อกำหนด

1. ทุกครั้งที่ทาย ต้องบอกว่า "มากไป" "น้อยไป" หรือ "ถูกต้อง"
2. ต้องทายอย่างน้อยหนึ่งครั้งเสมอ
3. จำกัดจำนวนครั้งที่ทายได้สูงสุด 5 ครั้ง
4. เมื่อจบเกม ให้แสดงว่าชนะหรือแพ้ และใช้ไปกี่ครั้ง
```

**Hint**

`[คำใบ้]`
1. โจทย์ต้องการ "ทำก่อน แล้วค่อยตรวจเงื่อนไข"
2. เงื่อนไขหยุดมี 2 อย่าง คือ "ทายถูก" หรือ "ครบ 5 ครั้ง" ต้องเช็กทั้งคู่
3. ระวังกรณีชุดคำตอบสั้นกว่า 5 ตัว ถ้าดึงเกินขอบเขตโปรแกรมจะ panic

**Solution**

```rust
// Solution code
use std::cmp::Ordering;

fn main() {
    let secret = 37;
    let guesses = [50, 25, 40, 37];
    let max_tries = 5;
    let limit = max_tries.min(guesses.len()); 

    let mut tries = 0;
    let mut won = false;

    loop {
        let guess = guesses[tries];
        tries += 1;

        match guess.cmp(&secret) {
            Ordering::Greater => println!("ครั้งที่ {}: ทาย {} -> มากไป", tries, guess),
            Ordering::Less => println!("ครั้งที่ {}: ทาย {} -> น้อยไป", tries, guess),
            Ordering::Equal => {
                println!("ครั้งที่ {}: ทาย {} -> ถูกต้อง!", tries, guess);
                won = true;
            }
        }

        if won || tries >= limit {
            break;
        }
    }

    if won {
        println!("ชนะ! ใช้ {} ครั้ง", tries);
    } else {
        println!("แพ้! ใช้ครบ {} ครั้งแล้ว", tries);
    }
}
```

**Explanation**

`[อธิบายแนวทางแก้]`
```text
secret คือเลขลับที่ใช้เทียบ
guesses คืออาเรย์คำตอบที่กำหนดล่วงหน้า (แทนการรับค่าจากผู้เล่นจริง)
max_tries คือจำนวนครั้งสูงสุดที่ทายได้ ตามโจทย์คือ 5
limit คือจำนวนครั้งที่ทายได้จริง โดย .min(...) เลือกค่าที่น้อยกว่าระหว่าง 5 กับความยาวอาเรย์เพื่อกันไม่ให้ดึงคำตอบเกินขอบเขตอาเรย์แล้ว panic

tries นับจำนวนครั้งที่ทายไปแล้ว และใช้เป็นดัชนีดึงคำตอบจากอาเรย์ด้วย
won เป็นธงบอกว่าทายถูกหรือยัง
ทั้งสองต้องมี mut เพราะค่าเปลี่ยนในลูป

loop คือลูปไม่รู้จบที่ไม่มีเงื่อนไขที่หัวลูป จึงทำงาน อย่างน้อยหนึ่งรอบเสมอ แล้วค่อยตรวจเงื่อนไขหยุดที่ท้ายลูป

guess.cmp(&secret) คืนค่า enum Ordering ซึ่งมี 3 ค่าเท่านั้น
match ของ Rust บังคับให้ครอบคลุมทุกกรณี ถ้าลืมกรณีใดคอมไพเลอร์จะไม่ยอมให้คอมไพล์ ต่างจาก switch ของ C ที่ถ้าไม่มี default จะไม่ทำอะไร

เงื่อนไขหยุดลูป ยุดเมื่อ อย่างใดอย่างหนึ่ง เป็นจริง คือทายถูกแล้ว หรือทายครบจำนวนที่กำหนด

สรุปผลหลังลูป
```
---

### Exercise 2 — `[ตารางสูตรคูณ]`

**Problem**

`[เขียนโจทย์]`
สร้างตารางสูตรคูณแม่ 1 ถึง 9 คูณ 1 ถึง 9

ข้อกำหนด
1. ข้ามการแสดงผลลัพธ์ที่เป็นจำนวนคี่ (ใช้ continue)
2. หยุดพิมพ์ทั้งตารางทันทีเมื่อพบผลคูณที่มากกว่า 50 เป็นครั้งแรก (ใช้ labeled break)
3. นับว่าพิมพ์ผลคูณไปทั้งหมดกี่ค่า และแสดงผลรวมของค่าที่พิมพ์

**Hint**

`[คำใบ้]`
1. ต้องใช้ for ซ้อนกันสองชั้น ช่วง 1 ถึง 9 ทั้งคู่
2. ลำดับการเช็กในลูปในสำคัญมาก ลองคิดว่าควรเช็ก "มากกว่า 50" ก่อนหรือหลังเช็ก "เป็นเลขคี่"
3. ผลคูณที่ทำให้หยุดจะไม่ถูกพิมพ์หรือนับ ตรวจให้แน่ใจว่าตรงกับที่โจทย์ต้องการ

**Solution**

```rust
// Solution code
fn main() {
    let mut count = 0;
    let mut sum = 0;

    'outer: for i in 1..=9 {
        for j in 1..=9 {
            let product = i * j;

            if product > 50 {
                break 'outer; 
            }
            if product % 2 != 0 {
                continue; 
            }

            println!("{} x {} = {}", i, j, product);
            count += 1;
            sum += product;
        }
    }

    println!("พิมพ์ทั้งหมด {} ค่า, ผลรวม = {}", count, sum);
}
```

**Explanation**

`[อธิบายแนวทางแก้]`
```text
count นับจำนวนผลคูณที่ถูกพิมพ์ และ sum เก็บผลรวมของค่าที่พิมพ์
ใส่ mut เพราะค่าเปลี่ยนในลูป และประกาศไว้นอกลูปทั้งสองชั้น

1..=9 คือช่วงแบบ รวมค่าปลายทาง

'outer: คือ label ตั้งชื่อให้ลูปนี้เพื่อให้ลูปในอ้างถึงได้

product = i * j คำนวณผลคูณ

ถ้าผลคูณมากกว่า 50 ให้ break 'outer ซึ่งออกจาก ทั้งสองลูปทันที
```
---

## 9. PPL Perspective

> วิเคราะห์เรื่อง **Iterative Structures (โครงสร้างการวนซ้ำ)** ในมุมมองของรายวิชา Principles of Programming Languages

### 9.1 Syntax
ภาษา Rust มีคำสั่งวนซ้ำ 3 รูปแบบหลักให้เลือกใช้ตามความเหมาะสมของงาน:
1. `loop` : การวนลูปแบบไร้ขีดจำกัด (Infinite Loop) วนทำงานไปเรื่อยๆ จนกว่าจะมีคำสั่งหยุด
2. `while` : การวนลูปตามเงื่อนไข (Conditional Loop) ทำงานตราบใดที่เงื่อนไขยังเป็นจริง
3. `for` : การวนลูปผ่านองค์ประกอบในชุดข้อมูล (Iterator Loop)

**จุดเด่นทาง Syntax:** Rust ตัดการใส่เครื่องหมายวงเล็บ `()` ล้อมรอบเงื่อนไขออก ทำให้ไวยากรณ์สะอาด อ่านง่าย และลดความซ้ำซ้อนในโค้ด

### 9.2 Semantics
บล็อกคำสั่ง `loop` ใน Rust มีพฤติกรรมพิเศษคือเป็น **Expression** (บล็อกคำสั่งที่คืนค่าผลลัพธ์ออกมารับไว้ที่ตัวแปรได้) ผ่านคำสั่ง `break value;`
* แตกต่างจากภาษาทั่วไปที่มองลูปเป็นเพียง **Statement** (สั่งให้ทำงานได้อย่างเดียว แต่ส่งค่าคืนออกมาที่ตัวแปรโดยตรงไม่ได้)

### 9.3 Type System
การวนลูปด้วย `for` ใน Rust ทำงานร่วมกับระบบ Type System ผ่าน Trait ที่ชื่อว่า `IntoIterator`
* คอมไพเลอร์จะตรวจสอบและระบุชนิดข้อมูล (Type) ของสมาชิกทุกตัวในลูปอย่างแม่นยำตั้งแต่ช่วง **Compile-time** ช่วยป้องกันข้อผิดพลาดจาก Type Mismatch ก่อนนำโปรแกรมไปรันจริง

### 9.4 Memory / Resource Management
การวนลูปเพื่ออ่านชุดข้อมูล (Collection) ใน Rust ถูกควบคุมอย่างเข้มงวดด้วยกฎ **Ownership & Borrowing**:
* `for item in &collection` : **Immutable Borrow** — ขอ "ยืมอ่าน" ข้อมูลอย่างเดียว (ปลอดภัยที่สุด)
* `for item in &mut collection` : **Mutable Borrow** — ขอ "ยืมเพื่อแก้ไข" ข้อมูลภายในลูป
* `for item in collection` : **Move Ownership** — "ย้ายสิทธิ์ความเป็นเจ้าของ" มายังลูป (เมื่อวนลูปจบ ข้อมูลเดิมจะถูกลบ)

**ประโยชน์:** ป้องกันปัญหาคลาสสิกอย่าง **Iterator Invalidation** (การแอบแก้ไขหรือลบข้อมูลใน Collection ขณะที่ลูปกำลังวนอ่านอยู่) และ **Data Race** ในโปรแกรมแบบ Concurrent

### 9.5 Abstraction / Other PPL Concepts
Rust ใช้แนวคิด **Zero-cost Abstractions** ในการจัดการการวนซ้ำ
* แม้เราจะเขียนโค้ดในรูปแบบระดับสูง (High-level Iterator) ที่อ่านง่าย แต่เมื่อถูก Compile แล้ว จะแปลงเป็น Machine Code ที่มีความเร็วสูงโดยไม่มี Runtime Overhead หรือ Garbage Collector มาคอยดึงประสิทธิภาพโปรแกรมให้ช้าลง

### 9.6 Why Rust?
Rust ออกแบบ Iterative Structures มาเพื่อขจัดข้อผิดพลาดร้ายแรงของผู้เขียนโปรแกรม เช่น **Off-by-one Error** และ **Out-of-bounds Access** ได้อย่างเด็ดขาดในขั้นตอน Compile-time โดยไม่ต้องพึ่งพา Runtime Garbage Collection

---

## 10. Rust vs. Other Language

**Comparison Language:** `Python`

| Aspect (ด้านการเปรียบเทียบ) | Rust | Python |
|---|---|---|
| **Syntax** | ใช้ `loop`, `while`, `for ... in ...` ไม่ต้องมีวงเล็บ `()` ล้อมรอบเงื่อนไข | ใช้ `while`, `for ... in ...` กำหนดบล็อกด้วย Indentation (การย่อหน้า) และมีโครงสร้างพิเศษอย่าง `else` ต่อท้ายลูป |
| **Semantics / Behavior** | `loop` เป็น Expression คืนค่าออกมารับไว้ที่ตัวแปรได้ผ่าน `break val;` | ลูปเป็น Statement ไม่คืนค่าออกมาโดยตรง (ต้องใช้ List Comprehension หรือสร้างตัวแปรรับค่าเอง) |
| **Type System** | Static Typing — ตรวจสอบ Type ของ Iterator และข้อมูลตั้งแต่ช่วง Compile-time | Dynamic Typing / Duck Typing — ตรวจสอบการวนลูป (`__iter__`) ตอน Runtime |
| **Memory Management** | ควบคุมการเข้าถึงด้วย **Ownership & Borrowing** โดยไม่มี Garbage Collector (Zero-cost) | ใช้ **Garbage Collector (GC)** คอยจัดการ Memory มีภาระภายนอก (Runtime Overhead) ในทุกการวนลูป |
| **Safety** | Borrow Checker ป้องกันการแก้ไข Collection ขณะวนอ่านลูปตั้งแต่อยู่ในระดับ Compile-time | หากแก้ไข Collection ระหว่างวนลูป อาจเกิดพฤติกรรมผิดพลาด (Logical Bug) หรือแจ้งเตือน `RuntimeError` |

### Rust Example
```rust
fn main() {
    let numbers = vec![10, 20, 30];

    // 1. วนลูปอ่านค่าอย่างปลอดภัยด้วยการ "ยืม" (&numbers)
    for num in &numbers {
        println!("Number: {}", num);
    }

    // 2. loop ที่เป็น Expression สามารถส่งค่าผลลัพธ์ออกมาเก็บในตัวแปรได้
    let mut count = 0;
    let result = loop {
        count += 1;
        if count == 5 {
            break count * 2; // ส่งค่า 10 ออกมาเก็บไว้ใน result
        }
    };
    println!("Result from loop expression: {}", result);
}

### `[Other Language]` Example

```python
numbers = [10, 20, 30]

# 1. วนลูปผ่าน List ใน Python (ใช้ Iterable protocol)
for num in numbers:
    print(f"Number: {num}")

# 2. การหาผลลัพธ์จากลูปต้องใช้ตัวแปรภายนอกมารับค่า (ไม่มี loop expression)
count = 0
while True:
    count += 1
    if count == 5:
        result = count * 2
        break
print(f"Result from loop: {result}")

# 3. ตัวอย่างความเสี่ยงของการแอบแก้ไข List ระหว่างวนลูปใน Python (เกิดข้อผิดพลาดตอน Runtime)
# for num in numbers:
#     numbers.remove(num)  # ข้อมูลจะถูกลบข้ามองค์ประกอบไปเรื่อยๆ โดยที่คอมไพเลอร์ไม่เตือนก่อนรัน
```

### Analysis

`Python ออกแบบการวนลูปโดยเน้นความสะดวกสบายและอ่านง่ายของผู้เขียนโปรแกรม (Developer Ergonomics) ผ่าน Dynamic Typing แต่ต้องแลกมาด้วย Runtime Overhead จากการทำงานของ Garbage Collector และความเสี่ยงที่โปรแกรมจะทำงานผิดพลาดขณะรันหากมีการแก้ไขข้อมูลขณะวนลูป

ในทางกลับกัน ภาษา Rust เลือกใช้ระบบ Borrow Checker และ Zero-cost Abstractions ในการจัดการการวนซ้ำ ทำให้ได้ทั้งความปลอดภัยสูงสุดตั้งแต่ขั้นตอน Compile-time และประสิทธิภาพความเร็วที่เหนือกว่าโดยไม่ต้องพึ่งพา Garbage Collector`

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

`[Rust, Other Language, PPL Analysis]`

**Member 4**

`[Exercies, Common Mistakes, Challenge]`

> สมาชิกทุกคนต้องสามารถอธิบาย Code ของกลุ่มได้ ไม่ใช่เฉพาะส่วนที่ตนเองเขียน

---

## 12. References

> แนะนำให้มีอย่างน้อย **4 แหล่งอ้างอิง** และควรใช้เอกสารทางการเป็นหลัก

1. `[The Rust Programming Language — Rust Book]`
2. `[Rust by Example / Rust Reference]`
3. `[Official documentation ที่เกี่ยวข้องกับ Topic]`
4. `[https://www.w3schools.com/rust/rust_loops_for.php]`
5. `[https://users.rust-lang.org/t/reverse-for-loops/53856]`
6. `[ https://medium.com/@fennsaji/day-1-input-and-output-i-o-in-rust-with-examples-be6f9478d133]`
7. `[https://www.w3schools.com/rust/rust_loops_while.php]`

---

## 13. AI Usage Declaration

สามารถใช้ AI เป็นเครื่องมือช่วยเรียนรู้และพัฒนาได้ แต่สมาชิกทุกคนต้องเข้าใจและสามารถอธิบายผลงานของกลุ่มได้

| AI Tool | Purpose | How the Result Was Verified |
|---|---|---|
| `[Claude]` | `[คิดโจทย์ challenge และ โจทย์ Example]` | `[https://claude.ai/chat/80a72dbd-c254-4693-8492-9b4aafd4d969]` |
| `[AI tool]` | `[ใช้เพื่ออะไร]` | `[ตรวจสอบอย่างไร]` |

### Declaration

- [X] Code ทุกส่วนที่นำเสนอได้รับการ Compile และทดสอบแล้ว
- [ ] สมาชิกทุกคนสามารถอธิบาย Code ที่นำเสนอได้
- [ ] ตรวจสอบข้อมูลจากแหล่งอ้างอิงที่น่าเชื่อถือแล้ว
- [X] ระบุการใช้ AI อย่างโปร่งใส

**รายละเอียดการใช้ AI**

`[อธิบายว่าใช้ AI ในขั้นตอนใด และสมาชิกตรวจสอบผลลัพธ์อย่างไร]`

---

## 14. GitHub Contribution

| Member | Issues | Commits | Pull Requests | Code Reviews | Contribution |
|---|---:|---:|---:|---:|---|
| Member 1 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 2 | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[จำนวน]` | `[รายละเอียด]` |
| Member 3 | `[0]` | `[1]` | `[1]` | `[1]` | `[docs: update PPL anaiysis and Rust vs Python comparison]` |
| Member 4 | `[0]` | `[1]` | `[4]` | `[0]` | `[รายละเอียด]` |

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
- [X] Runnable Code Examples
- [X] Code Compile และ Run ได้จริง
- [X] Common Mistakes
- [X] Exercises 2 ข้อ พร้อม Solutions
- [ ] PPL Perspective
- [X] Rust vs Other Language
- [X] References อย่างน้อย 4 แหล่ง
- [X] AI Usage Declaration
- [X] GitHub Contribution
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
