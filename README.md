```C

#include <Servo.h>

Servo rightLeg;
Servo leftLeg;
Servo rightFoot;
Servo leftFoot;
int echo = 8;
int trig = 9;
int num;



void setup() {
 rightFoot.attach(6);
 leftFoot.attach(5);
 rightLeg.attach(4);
 leftLeg.attach(3);
 Serial.begin(9600);
 neutral();
 pinMode(echo, INPUT);
 pinMode(trig, OUTPUT);
num = random(1,100);
}

void loop() { 
  float distance = getDistance();
Serial.println(distance);

if(distance < 50){
  
  num = random(1,6);
  if( num ==1){
    Serial.println("WALK");
    walk();
    walk();
    walk();
    
  }
  if(num== 2){
    Serial.println("Tip Toes!!!!");
    tipToes();
    tipToes();
    tipToes();
  }
  if(num == 3){
    Serial.println("UpDown.");
    upDown();
    neutral();
    delay(250);
    upDown();
    neutral();
    delay(250);
  }
  if(num == 4){
    Serial.println("LeapLeapLeap");
    leap();
    leap();
    leap();
  }
  if(num == 5){
    Serial.println("DANCE PARTAY!!!!");
    dance();
    dance();
    dance();
    dance();
    dance();
  }
  
  

}
else{
  randomSeed(millis());
}
neutral();
delay(250);

}

void tipToes(){
rightFoot.write(60);
leftFoot.write(120);
delay(500);
neutral();
delay(500);
}

void neutral(){

rightFoot.write(85);
leftFoot.write(87);
rightLeg.write(80);
leftLeg.write(80);
}

void dance(){
  neutral();
  delay(250);
  rightLeg.write(120);
  rightFoot.write(60);
  delay(250);
  leftLeg.write(120);
  leftFoot.write(120);
  rightLeg.write(80);
  rightFoot.write(85);
  delay(250);
}

float getDistance(){
  digitalWrite(trig, LOW);
  delayMicroseconds(2);
  digitalWrite(trig, HIGH);
  delayMicroseconds(10);
  digitalWrite(trig, LOW);

  float duration = pulseIn(echo, HIGH);
  float distance = duration * 0.034 / 2;
  return distance;
}

/*
void walk(){ 
// neutral();
delay(250);
//stick out heels
rightLeg.write(150);
rightFoot.write(100);
leftLeg.write( delay(250);
//leftLeg.write(30);
// leftFoot.write(120);
//delay(250);
rightLeg.write(70);
rightFoot.write(60);
delay(250);
//rightFoot.write(120);
delay(250);
} 
*/

void walk(){
rightLeg.write(110);
leftLeg.write(110);
delay(250);

rightFoot.write(85);
leftFoot.write(120);
delay(250);

rightLeg.write(50);
leftLeg.write(50);
delay(250);

rightFoot.write(60);
leftFoot.write(80);
delay(250);

}

void leap(){
  neutral();
  delay(250);
//stick out heels 
  rightLeg.write(150);
  rightFoot.write(60);
  delay(500);
  //leftLeg.write(30);
  // leftFoot.write(120);
  //delay(250);

  rightFoot.write(120);
  delay(500);
  rightLeg.write(70);
  delay(500);

}

void upDown(){
  int leftPos = 87;
  for(int i = 85; i >= 20; i--){
    leftPos++;
    rightFoot.write(i);
    leftFoot.write(leftPos);
    delay(25);
} 
delay(1000);
for(int i = 20; i <= 85; i++){
  leftPos--;
  rightFoot.write(i);
  leftFoot.write(leftPos);
  delay(25);
  }
}
```
