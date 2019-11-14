### Youtube 링크

https://youtu.be/xpp5GMU8USU

### 회로도

![10](https://user-images.githubusercontent.com/50912987/68826657-23ba2a00-06e2-11ea-9751-21efd3ac6bde.JPG)
![11](https://user-images.githubusercontent.com/50912987/68826680-3af91780-06e2-11ea-8ef4-86c5db221bb0.JPG)

* 인식거리가 너무 넓고 저항값이 부족하다 생각되어 1KΩ을 10kΩ으로 변경

![12](https://user-images.githubusercontent.com/50912987/68826834-e1451d00-06e2-11ea-85d5-6b508b7ec267.jpg)


### 소스코드

```
#include <Servo.h>                        
Servo servoLeft;                           
Servo servoRight;
 
void setup()                                 
{
  pinMode(10, INPUT);  pinMode(9, OUTPUT);  
  pinMode(3, INPUT);  pinMode(2, OUTPUT);   

  servoLeft.attach(13);                     
  servoRight.attach(12);                    
}  
 
void loop()                                  
{
  int irLeft = irDetect(9, 10, 38000);      
  int irRight = irDetect(2, 3, 38000);       

  if((irLeft == 0) && (irRight == 0))      
    backward(1000);                          
    turnLeft(800);                          
  }
  else if(irLeft == 0)                      
  {
    backward(1000);                         
    turnRight(400);                         
  }
  else if(irRight == 0)                      
  {
    backward(1000);                          
    turnLeft(400);                          
  }
  else                                      
  {
    forward(20);                             
  }
}

int irDetect(int irLedPin, int irReceiverPin, long frequency)
{
  tone(irLedPin, frequency, 8);             
  delay(1);                                 
  int ir = digitalRead(irReceiverPin);      
  delay(1);                                  
  return ir;                                
}  

void forward(int time)                      
{
  servoLeft.write(1700);        
  servoRight.write(1300);       
  delay(time);                              
}

void turnLeft(int time)                     
{
  servoLeft.write(1300);         
  servoRight.write(1300);       
  delay(time);                               

void turnRight(int time)                    
{
  servoLeft.write(1700);         
  servoRight.write(1700);        
  delay(time);                               
}

void backward(int time)                     
{
  servoLeft.write(1300);        
  servoRight.write(1700);       
  delay(time);                               
}
```
