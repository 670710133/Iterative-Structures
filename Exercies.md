# แบบฝึกหัด
### Counter-Controlled Loop
1. เขียนลูปบวกค่าอาเรย์ตำแหน่ง 0-10 รวมตำแหน่ง 10 ด้วย
```rs
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
- ที่มา: https://www.w3schools.com/rust/rust_loops_for.php

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
- ที่มา: https://users.rust-lang.org/t/reverse-for-loops/53856
- ที่มา: https://stackoverflow.com/questions/27893223/how-do-i-iterate-over-a-range-with-a-custom-step


### Logically-Controlled Loop
3. จำลองโปรแกรม "รับค่าจนกว่าจะได้ค่าที่ติดลบ" และทำการหยุดลูป
    1. Pre-test
    ```rs
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
    - ที่มา: https://doc.rust-lang.org/rust-by-example/flow_control/loop.html
    - ที่มารับค่า: https://medium.com/@fennsaji/day-1-input-and-output-i-o-in-rust-with-examples-be6f9478d133



    2. Post-test
    ```rs
    use std::io;
        fn main(){
    
            loop{
                let mut msg = String::new();
                io::stdin()
                    .read_line(&mut msg)
                    .expect("Failed input");

                let numbers: i32 = match msg.trim().parse(){
                    Ok(num) => num,
                    Err(_) => {
                        println!("Please type a valid number!");
                        continue;
                    }
                };

            if numbers < 0{
                println!("Stopped! Entered negative numbers: {}",  numbers);
                break;
            }    

            println!("Input numbers: {}", numbers);
        }
    }
    ```
- ที่มา: https://www.w3schools.com/rust/rust_loops_while.php


### Iteration
4. เขียนโปรแกรมที่พิมพ์ "Name: Bob", "Name: Carol", "Name: Ted" จากคอลเลกชันของสตริงสามตัว
```rs
let names = vec!["Bob", "Carol","Ted"];

    for name in names{
        println!("Names --> {}", name);
    }
```
ที่มา: https://doc.rust-lang.org/rust-by-example/flow_control/for.html



## Common Mistasks
#### Counter-Controll loop
```rs
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

```rs
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


#### Logically-Controlled Loop
```rs
loop{
       let mut msg = String::new();
        io::stdin()
           .read_line(&mut msg)
            .expect("Failed input");
   

        println!("Input numbers: {}", numbers);
    }
```

```rs
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
```


#### Iterations
```rs
let names = vec!["Bob", "Carol","Ted"];

for i in 0..3{
         println!("Names --> {}", names.get(i));
}
```