# Contador-con-2-sensores
#include <LiquidCrystal.h> 
LiquidCrystal lcd(13,12,11,10,9,8); //rs,e,d4,d5,d6,d7

 int Pinsensor_1 ;
 int Pinsensor_2 ;
#define pin_1 25
#define pin_2 26
int cont = 0;

void setup() {
  Serial.begin(9600);
  lcd.begin(20,4);
  pinMode(pin_1, INPUT);
  pinMode(pin_2, INPUT);
  lcd.print("objetos");

}

void loop() {
  
  Pinsensor_1 = digitalRead(Pinsensor_1);
  Pinsensor_2 = digitalRead(Pinsensor_1);

  if(Pinsensor_1 == LOW && Pinsensor_2 == HIGH){
    cont = cont;
    Serial.println("");
    while(Pinsensor_1 == LOW && Pinsensor_2 == LOW);
    cont = cont +1;
    Serial.println("paso objeto");
  }
    if(Pinsensor_1 == HIGH && Pinsensor_2 == LOW){
    cont = cont;
    Serial.println("Detecto objeto");
    while(Pinsensor_1 == LOW && Pinsensor_2 == LOW);
    cont = cont -1;
    Serial.println("regreso objeto");
  }
      lcd.setCursor(7,1);         //Coorddenadas LCD (x,y)
      lcd.print(cont);

      if(cont > 20){
      lcd.clear();
      lcd.print("objetos");
      cont=0;
   }
delay (2000);
}
