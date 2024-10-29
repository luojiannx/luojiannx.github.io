---
title: arduino uno r3驱动直流电机
date: 2024-10-29 18:57:44
tags: arduino unuo r3 直流电机
---
用deepseek几乎是一次性的通过了。但不知道为什么引脚对应错了，13号引脚才是ena！所以我所作的改动就是把下面第一行代码和第三行代码的13和11互换。然后就编译通过，并且功能正常。

要在Arduino Uno R3上通过L298N电机驱动模块控制直流电机的正转、反转和PWM调速，你可以使用以下C语言代码。假设你已经将Arduino的11、12、13号引脚分别连接到L298N的IN1、IN2和ENA引脚。

```c
// 定义引脚
const int in1 = 13;  // L298N的IN1引脚连接到Arduino的13号引脚
const int in2 = 12;  // L298N的IN2引脚连接到Arduino的12号引脚
const int ena = 11;  // L298N的ENA引脚连接到Arduino的11号引脚

void setup() {
  // 设置引脚模式
  pinMode(in1, OUTPUT);
  pinMode(in2, OUTPUT);
  pinMode(ena, OUTPUT);
}

void loop() {
  // 正转
  digitalWrite(in1, HIGH);
  digitalWrite(in2, LOW);
  analogWrite(ena, 255);  // 全速正转
  delay(2000);  // 正转2秒

  // 停止
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  delay(1000);  // 停止1秒

  // 反转
  digitalWrite(in1, LOW);
  digitalWrite(in2, HIGH);
  analogWrite(ena, 128);  // 半速反转
  delay(2000);  // 反转2秒

  // 停止
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  delay(1000);  // 停止1秒

  // PWM调速
  for (int speed = 0; speed <= 255; speed += 10) {
    analogWrite(ena, speed);  // 逐渐加速
    delay(100);
  }
  for (int speed = 255; speed >= 0; speed -= 10) {
    analogWrite(ena, speed);  // 逐渐减速
    delay(100);
  }

  // 停止
  digitalWrite(in1, LOW);
  digitalWrite(in2, LOW);
  delay(1000);  // 停止1秒
}
```

### 代码说明：
1. **引脚定义**：
   - `in1` 和 `in2` 用于控制电机的方向。
   - `ena` 用于控制电机的速度（PWM调速）。

2. **setup()函数**：
   - 设置 `in1`、`in2` 和 `ena` 引脚为输出模式。

3. **loop()函数**：
   - **正转**：将 `in1` 设置为 `HIGH`，`in2` 设置为 `LOW`，并通过 `analogWrite(ena, 255)` 全速正转。
   - **停止**：将 `in1` 和 `in2` 都设置为 `LOW`，电机停止。
   - **反转**：将 `in1` 设置为 `LOW`，`in2` 设置为 `HIGH`，并通过 `analogWrite(ena, 128)` 半速反转。
   - **PWM调速**：通过 `analogWrite(ena, speed)` 逐渐增加和减少速度，实现电机的加速和减速。

### 注意事项：
- `analogWrite(ena, speed)` 中的 `speed` 值范围是 0 到 255，其中 0 表示停止，255 表示全速。
- 你可以根据需要调整 `delay()` 的时间来改变电机的运行时间。

这段代码可以实现电机的正转、反转和PWM调速控制，你可以根据实际需求进行修改和扩展。
