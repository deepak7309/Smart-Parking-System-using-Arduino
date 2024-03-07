# Smart-Parking-System-using-Arduino
The Arduino-powered Smart Parking System transforms urban parking management by monitoring and guiding drivers to available spaces in real-time, reducing congestion and optimizing traffic flow.
The Smart Parking System using Arduino in Tinkercad is a project aimed at revolutionizing urban parking management by dynamically monitoring and guiding drivers to available parking spaces. This project showcases the integration of Arduino microcontroller technology with virtual sensors and actuators in Tinkercad, a web-based platform for simulating electronics projects.


**Features:**


Real-time monitoring of parking spaces

Dynamic guidance for drivers to available parking spots

Alleviation of congestion and optimization of traffic flow

Seamless integration of technology with urban infrastructure

**Introduction:**
The Smart Parking System project aims to address the challenges of urban parking management by leveraging Arduino technology in Tinkercad, a web-based platform for simulating electronics projects. This report outlines the design, implementation, and functionality of the Smart Parking System.

**Design:**
The Smart Parking System consists of Arduino microcontroller boards, virtual sensors, and actuators simulated within the Tinkercad environment. The system is designed to monitor parking spaces in real-time and guide drivers to available spots.
The design is attached below:

![t725](https://github.com/deepak7309/Smart-Parking-System-using-Arduino/assets/132645894/fba424e9-8a9a-441f-815e-e5e2d25959be)

**Implementation:**
The implementation involves creating a virtual circuit in Tinkercad, which includes Arduino boards, ultrasonic sensors to detect vehicle presence, LEDs to indicate parking space availability, and a buzzer for alarm notification. The Arduino code is written to read sensor data and control the LEDs and buzzer based on parking space occupancy.

**Code:**
#include<LiquidCrystal.h>
#include<Servo.h>

Servo S1,S2;
#define IR_Slot1 7
#define IR_Slot2 8
#define IR_entry 6
#define IR_exit 13

int pos=0;
LiquidCrystal lcd(12, 11, 5, 4, 3, 2);
void setup()
{
  S1.attach(10);
  S2.attach(9);
  
  S1.write(pos);
  S2.write(pos);
  
  pinMode(IR_Slot1,INPUT);
  pinMode(IR_Slot2,INPUT);
  pinMode(IR_entry,INPUT);
  pinMode(IR_exit,INPUT);
  
  lcd.begin(16, 2);
  lcd.print("Smart Parking");
  lcd.setCursor(0,1);
  lcd.print("    System");
  delay(2000);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Slot 1=A");
  lcd.setCursor(0,1);
  lcd.print("Slot 2=A");
   delay(2000);
} 
  void loop()
  {
    if(digitalRead(IR_Slot1)==HIGH)
    {
      lcd.setCursor(0,0);
      lcd.print("Slot 1=NA");
    }
    else
    {lcd.setCursor(0,0);
      lcd.print("Slot 1=A");
    }
    if(digitalRead(IR_Slot2)==HIGH)
    {
      lcd.setCursor(0,1);
      lcd.print("Slot 2=NA");
    }
    else
    {lcd.setCursor(0,1);
      lcd.print("Slot 2=A");
    }
    if(digitalRead(IR_entry)==HIGH)
    {
      S1.write(pos+90);
    }
    else
    {
      S1.write(pos);
    }
    if(digitalRead(IR_exit)==HIGH)
    {
      S2.write(pos+90);
    }
    else
    {
      S2.write(pos);
    }
  }

  
**Functionality:**
Upon simulation, the Smart Parking System monitors parking spaces and updates the status of each space dynamically. When a vehicle enters a parking space, the corresponding LED turns red, indicating occupancy. Conversely, when the space is vacant, the LED turns green. Additionally, if the parking space is full, the system triggers the buzzer to alert drivers.

**Conclusion:**
The Smart Parking System using Arduino in Tinkercad demonstrates an effective solution for urban parking management. By providing real-time monitoring and guidance to available parking spaces, the system helps optimize traffic flow and enhance user convenience. This project exemplifies the seamless integration of Arduino technology with virtual simulation platforms for practical applications.

**Future Enhancements:**
Future enhancements to the Smart Parking System could include the integration of wireless communication modules for remote monitoring, the implementation of machine learning algorithms for predictive analysis of parking space availability, and the development of a mobile application for user interaction and feedback.

Overall, the Smart Parking System project showcases the potential of Arduino-based solutions in addressing urban infrastructure challenges and improving the efficiency of parking management systems.
