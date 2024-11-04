# موضوع آزمایش: امواج فراصوت 

## گزارش کار 
سنسورهای اولتراسونیک دو بخش دارند: فرستنده و گیرنده. فرستنده سیگنال فراصوتی ارسال می‌کند که اگر به مانع برخورد کند و برگردد، گیرنده آن را دریافت می‌کند و زمان رفت و برگشت را محاسبه می‌کند. با استفاده از سرعت صوت (340 متر بر ثانیه) و فرمول زیر می‌توان فاصله را محاسبه کرد:

فاصله = (زمان رفت و برگشت / 2) * سرعت صوت

---

### کد برنامه

```cpp
#include <LiquidCrystal.h>

LiquidCrystal lcd(12, 11, 7, 6, 5, 4);
int trig = 10;
int echo = 9;
int duration = 0;
int distance = 0;

void setup() {
  lcd.begin(16, 2);
  pinMode(trig, OUTPUT);
  pinMode(echo, INPUT);
}

void loop() {
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  duration = pulseIn(echo, HIGH);
  distance = (duration / 2) * 0.0343;

  lcd.print("Distance = ");
  lcd.setCursor(11, 0);
  lcd.print(distance);
  delay(500);
  lcd.clear();
}
```

### تصویر مدار


![pic micro](/pic/microprocessor1.jpg)
---

### شماتیک مدار 

![pic micro](/pic/schematic_10.jpg)


