# Arduino


## 1. Arduino简介  

Arduino是一种开源电子原型平台，提供了硬件和软件的整合，使知识产权和创意的塑造变得简单。它由Arduino开发板和Arduino IDE构成，开发者可轻松实现交互式项目。由于其易于使用的编程语言和丰富的社区支持，Arduino成为了教育、艺术和DIY电子项目的热门选择。  

Arduino的特点包括：  
- **易于学习和使用**：适合初学者，具有直观的开发环境。  
- **开放源代码**：拥有庞大的社区，用户可以自由获取、修改和分享代码。  
- **兼容多种硬件**：支持多种传感器和模块，能够扩展功能以满足不同项目需求。  
- **强大的社区支持**：用户可访问大量文档、教程和示例，快速积累知识。  

Arduino使得电子实验及项目的实现变得更加易于掌握，从简单的LED灯控制到复杂的传感器应用，它在教育和创客运动中的应用十分广泛。  

## 2. 接线图  

![接线图](media/7779235ecace300ed503db806d99ed8e.png)  

## 3. 测试代码  

以下是两段使用Arduino控制RGB LED的代码示例。  

代码1：基本RGB LED轮流点亮  

```cpp  
int redPin = 9; //定义红色接D9  
int greenPin = 10; //定义绿色接D10  
int bluePin = 11; //定义蓝色接D11  

void setup() {  
    //设置三个管脚为输出模式  
    pinMode(redPin, OUTPUT);  
    pinMode(greenPin, OUTPUT);  
    pinMode(bluePin, OUTPUT);  
}  

void loop() {  
    //红色  
    digitalWrite(redPin, HIGH);  
    digitalWrite(greenPin, LOW);  
    digitalWrite(bluePin, LOW);  
    delay(1000); // 延迟1秒  

    //绿色  
    digitalWrite(redPin, LOW);  
    digitalWrite(greenPin, HIGH);  
    digitalWrite(bluePin, LOW);  
    delay(1000); // 延迟1秒  

    //蓝色  
    digitalWrite(redPin, LOW);  
    digitalWrite(greenPin, LOW);  
    digitalWrite(bluePin, HIGH);  
    delay(1000); // 延迟1秒  
}  
```  

代码2：使用PWM控制RGB LED  

```cpp  
int redPin = 9; //定义红色接D9  
int greenPin = 10; //定义绿色接D10  
int bluePin = 11; //定义蓝色接D11  

void setup() {  
    //设置三个管脚为输出模式  
    pinMode(redPin, OUTPUT);  
    pinMode(greenPin, OUTPUT);  
    pinMode(bluePin, OUTPUT);  
}  

void loop() {  
    //红色  
    analogWrite(redPin, 255);  
    analogWrite(greenPin, 0);  
    analogWrite(bluePin, 0);  
    delay(1000); // 延迟1秒  

    //绿色  
    analogWrite(redPin, 0);  
    analogWrite(greenPin, 255);  
    analogWrite(bluePin, 0);  
    delay(1000); // 延迟1秒  

    //蓝色  
    analogWrite(redPin, 0);  
    analogWrite(greenPin, 0);  
    analogWrite(bluePin, 255);  
    delay(1000); // 延迟1秒  

    //黄色  
    analogWrite(redPin, 255);  
    analogWrite(greenPin, 255);  
    analogWrite(bluePin, 0);  
    delay(1000); // 延迟1秒  

    //紫色  
    analogWrite(redPin, 255);  
    analogWrite(greenPin, 0);  
    analogWrite(bluePin, 255);  
    delay(1000); // 延迟1秒  

    //白色  
    analogWrite(redPin, 255);  
    analogWrite(greenPin, 255);  
    analogWrite(bluePin, 255);  
    delay(1000); // 延迟1秒  
}  
```  

## 4. 代码说明  

代码1说明：  
1. 在代码1中，`redPin`, `greenPin`, `bluePin`分别定义了控制RGB LED中红、绿、蓝灯的管脚，接线分别为D9、D10、D11。  
2. 该代码循环控制LED依次显示红色、绿色、蓝色，每种颜色持续1秒。  

代码2说明：  
1. 代码2中使用PWM（脉宽调制）以调整每个颜色的亮度。通过设置不同的输出值（0-255），可以控制LED显示各种颜色。  
2. 该代码实现了红、绿、蓝、黄、紫、白六种颜色的切换，每种颜色持续1秒。  

## 5. 测试结果  

通过上传测试代码1，成功后，RGB LED模块将循环显示红、绿、蓝三种颜色，间隔时间为1秒。上传测试代码2成功后，RGB LED模块会依次显示红、绿、蓝、黄、紫、白六种颜色，间隔时间也是1秒。这些实验展示了如何通过Arduino简单地控制RGB LED，实现丰富的光色变化。



