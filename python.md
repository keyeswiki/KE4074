# Python


## 1. Python简介  

Python是一种跨平台的高级编程语言，以其清晰的语法和强大的功能而受到欢迎。它支持多种编程范式，包括程序式编程、面向对象编程和函数式编程。由于其可读性和易学习性，Python通常被作为初学者学习编程的首选语言。  

Python拥有丰富的标准库和第三方库，适用于数据分析、机器学习、Web开发、自动化脚本等多个领域。此外，Python也可以用于嵌入式开发，应用于微控制器和单板计算机（如Raspberry Pi）。其广泛的社区支持和大量的学习资源，使得Python成为开发者和学生的理想选择。  

## 2. 测试代码  

以下是两段Python代码示例，用于控制RGB LED的实验。  

代码1：简单的RGB LED控制  

```python  
import machine  
import utime  

led_external = machine.Pin(15, machine.Pin.OUT)  # 设置GPIO15为输出模式  
led_externa2 = machine.Pin(16, machine.Pin.OUT)   # 设置GPIO16为输出模式  
led_externa3 = machine.Pin(17, machine.Pin.OUT)   # 设置GPIO17为输出模式  

while True:  
    led_external.toggle()  # GPIO15输出高电平  
    led_externa2.low()     # GPIO16输出低电平  
    led_externa3.low()  
    utime.sleep(1)        # 延时1S  
    
    led_external.low()  
    led_externa2.toggle()  
    led_externa3.low()  
    utime.sleep(1)  
    
    led_external.low()  
    led_externa2.low()  
    led_externa3.toggle()  
    utime.sleep(1)  
```  

代码2：使用PWM控制RGB LED  

```python  
import machine  
import utime  
import urandom  

r = machine.Pin(15, machine.Pin.OUT)  
g = machine.Pin(16, machine.Pin.OUT)  
b = machine.Pin(17, machine.Pin.OUT)  

# 红、绿、蓝依次亮1秒  
for v in [(0, 1, 1), (1, 0, 1), (1, 1, 0)]:  
    r.value(v[0])  
    g.value(v[1])  
    b.value(v[2])  
    utime.sleep(1)  

pwm_r = machine.PWM(r)  
pwm_g = machine.PWM(g)  
pwm_b = machine.PWM(b)  

pwm_r.freq(1000)  
pwm_g.freq(1000)  
pwm_b.freq(1000)  

# 随机变换颜色  
def light(red, green, blue):  
    pwm_r.duty_u16(65535 - red * 255)  
    pwm_g.duty_u16(65535 - green * 255)  
    pwm_b.duty_u16(65535 - blue * 255)  

while True:  
    light(urandom.randint(0, 50), urandom.randint(0, 50), urandom.randint(0, 50))  
    utime.sleep(1)  
```  

## 3. 代码说明  

- **代码1说明**：  
  - 此代码用于简单的RGB LED控制，通过数字信号点亮LED。   
  - 使用`toggle()`方法切换状态，使LED亮灭交替进行，延迟时间设为1秒。  

- **代码2说明**：  
  - 此代码使用PWM（脉宽调制）信号控制RGB LED，使其颜色变化更加平滑和灵活。  
  - 代码首先依次点亮红、绿、蓝后，再通过PWM调制随机显示不同颜色，延迟时间为1秒。  

## 4. 测试结果  

上传测试代码1成功后，RGB LED循环显示红、绿、蓝三种颜色，每种颜色持续1秒。上传测试代码2成功后，RGB LED首先依次显示红、绿、蓝，然后随机显示其他颜色，同样间隔为1秒。




