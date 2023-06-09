const int M1=2;
const int M2=3;
const int M3=2;
const int M4=4;
const int M5=5;
const int M6=6;
const int LS1=7;
const int LS2=8;
const int WS1=9;
const int WS2=10;
const int Steamer=11;
const int Dryer=12;


void setup() {
  // put your setup code here, to run once:
//-------------------------------------OUTPUT
  pinMode(M1, OUTPUT);
  pinMode(M2, OUTPUT);
  pinMode(M3, OUTPUT);
  pinMode(M4, OUTPUT);
  pinMode(M5, OUTPUT);
  pinMode(M6, OUTPUT); 
  pinMode(Steamer, OUTPUT);
  pinMode(Dryer, OUTPUT);
//-------------------------------------INPUT
  pinMode(LS1, INPUT);
  pinMode(LS2, INPUT);
  pinMode(WS1, INPUT);
  pinMode(WS2, INPUT);     
}

void loop() {
  // put your main code here, to run repeatedly:
//-------------------------------------Startup
    if (digitalRead(LS1) == HIGH) {                                 
      digitalWrite(M1, LOW);
      digitalWrite(valve1,HIGH);
      digitalWrite(M2,HIGH); 
    }
    else{
      digitalWrite(M1, HIGH);
      digitalWrite(valve1, LOW);
      digitalWrite(M2, LOW);    
    }   
//-------------------------------------Steamer
    if (digitalRead(WS1) == High) {
      delay (3000);
      digitalWrite(M2, LOW);
      digitalWrite(Steamer, HIGH);    
      analogWrite(M3, 255);
      delay (1500);
      analogWrite(M3, 0);
      delay (3000);
      analogWrite(M3, 255);
      delay (2000);   
//-------------------------------------Dryer
      digitalWrite(Dryer, HIGH);
      analogWrite(M3, 100);
    }
    else{
      digitalWrite(M2, HIGH);
    }
//-------------------------------------store
    if (digitalRead(LS2) == High) {
      digitalWrite(M1, LOW);
      digitalWrite(valve1,LOW);      
      digitalWrite(M2, LOW);
      analogWrite(M3, 0);
      digitalWrite(Steamer, LOW);
      digitalWrite(Dryer, LOW);
    }
    else{
      digitalWrite(M1, HIGH);
    }
//-------------------------------------Packing
    if (digitalRead(WS2) == LOW){
      digitalWrite(valve2,HIGH);
      digitalWrite(M4, LOW);
      digitalWrite(M5, LOW);
      delay(2000);
      digitalWrite(M6, LOW);
    }
    else{
      digitalWrite(valve2,LOW);
      digitalWrite(M6, HIGH);
      delay(1000);
      digitalWrite(M5, HIGH);
      delay(1000);
      digitalWrite(M4, HIGH);
    }
}
