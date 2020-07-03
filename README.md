int push1=2;
int buzz=12;
int push2=3;
int estadoA=LOW;
int estadoB=LOW;

void setup()
{
  pinMode(9,OUTPUT);
  pinMode(10,OUTPUT);
  pinMode(11,OUTPUT);
  pinMode(buzz,OUTPUT);
  pinMode(push1,INPUT);
  pinMode(push2,INPUT);
  attachInterrupt(digitalPinToInterrupt(push1),buzzer,RISING);
  attachInterrupt(digitalPinToInterrupt(push2),change,RISING);
}
void loop()
{
  leds();
    
  if(estadoA==HIGH)
  {
   delay(3000);
   digitalWrite(buzz,LOW);
   estadoA=LOW;
  }
  
  if(estadoB==HIGH)
  {
   delay(5000);
   estadoB=LOW;
  }  
}

void leds()
{
  for(int pin=9;pin<12;pin++)
  {
   digitalWrite(pin,HIGH);
   delay(500);
   digitalWrite(pin,LOW);
  }
}

void buzzer()
{
  estadoA=!estadoA;
  digitalWrite(buzz,estadoA);
}


void change()
{
 estadoB=!estadoB;
 digitalWrite(9,LOW);
 digitalWrite(10,LOW);
 digitalWrite(11,LOW);
}
