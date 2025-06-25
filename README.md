#include <Wire.h> 
#include <LiquidCrystal_I2C.h>

int rs=2;
int m1=3;
int m2=4;
LiquidCrystal_I2C lcd(0x27,16,2);

void setup() {
  // put your setup code here, to run once:
pinMode(rs,INPUT);
pinMode(m1,OUTPUT);
pinMode(m2,OUTPUT);

  lcd.init();                      // initialize the lcd 
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Smart Car Window");
  lcd.setCursor(0,1);
  lcd.print("Viper via Sensor");
  delay(1500);  
}
void sweeper(){
digitalWrite(m1,1);
digitalWrite(m2,0);
delay(3750);
digitalWrite(m1,0);
digitalWrite(m2,0);
delay(100);
digitalWrite(m1,0);
digitalWrite(m2,1);
delay(3750);
digitalWrite(m1,0);
digitalWrite(m2,0);
delay(100);

}
void loop() {
  // put your main code here, to run repeatedly:
if(digitalRead(rs)==0){
  lcd.init();                      // initialize the lcd 
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Rain Detected");
  lcd.setCursor(0,1);
  lcd.print("Viaper on");

sweeper();
}
else{
  lcd.init();                      // initialize the lcd 
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0,0);
  lcd.print("Waiting for rain");
  lcd.setCursor(0,1);
  lcd.print("Viaper off");
delay(1000);
}

}




