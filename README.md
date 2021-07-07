# CALCULADORA_ARDUINO
PROYECTO_ CALCULADORA_FUNCIONAL_TEAM_SAVE.THE.SEMESTER.COFFEE
//calculadora basica
//realiza operaciones basicas con cuatro digitos...
#include <LiquidCrystal.h>
/* LCD RS     PIN 13
 * LCD ENABLE PIN 12
 * LCD D4     PIN 11
 * LCD D5     PIN 10
 * LCD D6     PIN 9
 * LCD D7     PIN 8
 * LCD R/W    PIN GROUND 
 * 10K 
 * +5V 
 * LCD V0 PIN3
 */
LiquidCrystal lcd(13,12,11,10,9,8);
int fila1=2,fila2=3,fila3=4,fila4=5,col1=A0,col2=A1,col3=A2,col4=A3;
int g=0,w=0,n=0,c=0,pr=0,op=0,fd=0;
int express=00000,resto=00;
float number1=00000.00,number2=00000.00;
double resultado=00000.00;
int f0=0000,fra=0000,fra2=0000;
boolean dos=false;
int key=0;
int botones[4][4]={{1,2,3,'A'},
                   {4,5,6,'B'},
                   {7,8,9,'C'},
                   {'*',0,'#','D'}
                   };
 ///////////////////////////////////////////////////////////////////
 ////// porcion de codigo editada por francisco ////////////////////
 void barrido(int w); 
void asignacion(int g); 
void calcular (int c); 
long var(int y);        
void setup(){
  Serial.begin(9600);
  pinMode(fila1,OUTPUT);
  pinMode(fila2,OUTPUT);
  pinMode(fila3,OUTPUT);
  pinMode(fila4,OUTPUT);
  pinMode(col1,INPUT);
  pinMode(col2,INPUT);
  pinMode(col3,INPUT);
  pinMode(col4,INPUT);
  lcd.begin(16,2);
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("Proyecto Calculadora");
  lcd.setCursor(0,1);
  lcd.print("  Arduino Uno   ");
    //lcd.setCursor(21,0);
    //lcd.autoscroll();
    //lcd.print(" ");
  for(int i=0;i<16;i++){
    lcd.scrollDisplayLeft();
    delay(200);
    }
   for(int i=0;i<16;i++){
    lcd.scrollDisplayRight();
    delay(200);
    }
  lcd.clear();
  }
///////////////////////////////////////////////////////////////////
/////////////////////SEGMENTO DE CODIGO DE SUAREZ//////////////////
*******************************************************************
void loop(){
  for(int i=0;i<4;i++){
     barrido(i);
     asignacion(i);
    }
  }
void barrido(int w){
  switch(w){
   case 0 :  digitalWrite(fila1,HIGH);
             digitalWrite(fila2,LOW);
             digitalWrite(fila3,LOW);
             digitalWrite(fila4,LOW);
             break;
    case 1 : digitalWrite(fila1,LOW);
             digitalWrite(fila2,HIGH);
             digitalWrite(fila3,LOW);
             digitalWrite(fila4,LOW);
             break;
    case 2 : digitalWrite(fila1,LOW);
             digitalWrite(fila2,LOW);
             digitalWrite(fila3,HIGH);
             digitalWrite(fila4,LOW);
             break;
    case 3 : digitalWrite(fila1,LOW);
             digitalWrite(fila2,LOW);
             digitalWrite(fila3,LOW);
             digitalWrite(fila4,HIGH);
             break;
    default : break;    
    }
  }  
///////////////////////////////////////////////////////////////////
