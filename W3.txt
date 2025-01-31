#include<SoftwareSerial.h>
SoftwareSerial Bluetooth(8,9);
int LED=12;
int Data;


void setup() {
  // put your setup code here, to run once:
Bluetooth.begin(9600);
Serial.begin(9600);
Serial.println("waiting foie command..");
Bluetooth.println("send 1 to turn on the LED");
pinMode(LED,OUTPUT);

}

void loop() {
  // put your main code here, to run repeatedly:
if (Bluetooth.available()){
  Data=Bluetooth.read();
 if(Data=='1'){
  digitalWrite(LED,HIGH);
  Serial.println("LED on!");
  Bluetooth.println("LED on!");
 }

 else if(Data=='0'){
  digitalWrite(LED,LOW);
  Serial.println("LED off!");
  Bluetooth.println("LED off!");
 }
 else{;}
 
}
delay(1000);
}

