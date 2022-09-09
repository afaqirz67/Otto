# Otto

## Code
```C

#include <Servo.h>

Servo rightLeg;
Servo leftLeg;
Servo rightFoot;
Servo leftFoot;

void setup() {
 rightFoot.attach(6);
 leftFoot.attach(5);
 rightLeg.attach(4);
 leftLeg.attach(3);
 Serial.begin(9600);
 neutral();

}

void loop() { 
//tipToes(); 
upDown();
neutral();
delay(250);
tipToes();
tipToes();
tipToes();
delay(250); }

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
  delay(250);
  //leftLeg.write(30);
  // leftFoot.write(120);
  //delay(250);

  rightFoot.write(120);
  delay(250);
  rightLeg.write(70);
  delay(250);

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

``
