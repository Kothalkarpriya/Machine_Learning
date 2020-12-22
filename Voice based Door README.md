tring voice;

#define lockPin 12
#define unlockPin 11
void setup() 
{                                            // put your setup code here, to run once:
  Serial.begin(9600);
  pinMode(lockPin, OUTPUT);
  pinMode(unlockPin, OUTPUT);
 
}
void loop() {
 
  while (Serial.available())   //Check if there is an available byte to read
  {                            
  delay(10);                   //Delay added to make thing stable
  char c = Serial.read();      //Conduct a serial read
  voice += c;                  //Shorthand for voice = voice + c
  } 

  if (voice.length() > 0) {
    Serial.println(voice);
  if(voice == "door lock")//                             
     {
   
     digitalWrite(lockPin,HIGH);
     delay(3000);
     digitalWrite(lockPin,LOW);
    
     }  
  else if(voice == "door unlock")//                              
     {
    
    digitalWrite(unlockPin,HIGH);
     delay(3000);
     digitalWrite(unlockPin,LOW);
     }
 voice="";                                                       //Reset the variable after initiating
  }}
