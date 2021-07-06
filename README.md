# Controlling-6-servos-service-evaluation-robot
In this repository i designed a circuit to control the service evaluation robot's arm, where i used an Arduino Uno as microcontroller and 6 servos for the arms 3 servo each.

**Tinkercad Link:**  https://www.tinkercad.com/things/ae56idbvjNn-dazzling-hango/editel?tenant=circuits


**Circuit diagram**

![image](https://user-images.githubusercontent.com/5675794/124623557-c2ca0180-de84-11eb-9f71-b824a6b0f7a5.png)


**Code**

```ruby
#include <Servo.h>;

int echoPin = 4;// attach pin D2 Arduino to pin Echo
int trigPin = 2;//attach pin D3 Arduino to pin Trig 
int ServoR1 = 6;
int ServoR2 = 5;
int ServoR3 = 3;
int ServoL1 = 11;
int ServoL2 = 10;
int ServoL3 = 9;
int time ;

Servo ServoR1_Object;
Servo ServoR2_Object;
Servo ServoR3_Object;
Servo ServoL1_Object;
Servo ServoL2_Object;
Servo ServoL3_Object;



void setup() {
  
  initialPosition();

  Serial.begin(9600);
  ServoR1_Object.attach(ServoR1);
  ServoR2_Object.attach(ServoR2);
  ServoR3_Object.attach(ServoR3);
  ServoL1_Object.attach(ServoL1);
  ServoL2_Object.attach(ServoL2);
  ServoL3_Object.attach(ServoL3);
  
  Serial.println("Please type the number of the move u want");
  Serial.println("(1) if you want the Welcome move");
  Serial.println("(2) if you want the GoodBye move");
  Serial.println("(3) if you want the Come Here move");
  Serial.println("(4) if you want the Happy move");
  Serial.println("(5) if you want the Sad move");

}
void loop() {
  
  if (Serial.available() > 0)
  {
    int input = Serial.read();
    
    // first condition. if user pressed 1
    if (input == '1')
    {
     Serial.println('\n');
     Serial.println("Doing Welcome Move...");
  
      ServoR1_Object.write(180);
      ServoR2_Object.write(0);
      ServoR3_Object.write(0);
      delay(850);
      ServoR3_Object.write(45);
      delay(850);
      ServoR3_Object.write(0);
      delay(1500);
      
      initialPosition();
      Serial.println("Done");
      
    }
    // second conndition. if user presses 2
    else if (input == '2')
    {
     Serial.println('\n');
     Serial.println("Doing GoodBye Move...");
        
      ServoR1_Object.write(180);
      ServoR2_Object.write(90);
      ServoR3_Object.write(40);
      delay(1500);
      
      initialPosition();
      Serial.println("Done");
    
    }// third condition. if user pressed 3
    else if (input == '3')
    {
    Serial.println('\n');
    Serial.println("Doing Come Here Move...");
      
      ServoR1_Object.write(90);
      ServoR2_Object.write(90);
      ServoR3_Object.write(0);
      
      ServoL1_Object.write(90);
      ServoL2_Object.write(90);
      ServoL3_Object.write(0);
      
      delay(850);
      ServoR2_Object.write(0);
      delay(850);
      ServoR2_Object.write(90);
      delay(1500);
      
      initialPosition();
      Serial.println("Done");
    }
    // fourth condition. if user pressed 4
    else if (input == '4')
    {
    Serial.println('\n');
    Serial.println("Doing Happy Move...");
    
      ServoR1_Object.write(90);
      ServoR2_Object.write(90);
      ServoR3_Object.write(0);
      
      ServoL1_Object.write(90);
      ServoL2_Object.write(90);
      ServoL3_Object.write(0);
      
      delay(1500);
      
      initialPosition();
      Serial.println("Done");

      
    }// fourth condition. if user pressed 5
    else if (input == '5')
    {
    Serial.println('\n');  
    Serial.println("Doing Sad Move...");
      
      ServoR1_Object.write(90);
      ServoR2_Object.write(90);
      ServoR3_Object.write(0);
      
      ServoL1_Object.write(90);
      ServoL2_Object.write(90);
      ServoL3_Object.write(0);
      
      delay(1500);
      
      initialPosition();
      Serial.println("Done");
      
    }
  }
  }
 

void initialPosition(){
  
       ServoR1_Object.write(0);
       ServoR2_Object.write(0);
       ServoR3_Object.write(0);
       ServoL1_Object.write(0);
       ServoL2_Object.write(0);
       ServoL3_Object.write(0);
}
```
