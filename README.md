#include <SD.h> // need to include the SD library
#define SD_ChipSelectPin 10 //connect pin 4 of arduino to cs pin of sd card
#include <TMRpcm.h> //Arduino library for asynchronous playback of PCM/WAV files
#include <SPI.h> //  need to include the SPI library

TMRpcm tmrpcm; // create an object for use in this sketch

int temp=1;
int next=8;

void setup()
{ 
 pinMode(next,INPUT_PULLUP);
 pinMode(9, OUTPUT);
 
 tmrpcm.speakerPin = 9; //5,6,11 or 46 on Mega, 9 on Uno, Nano, etc
 Serial.begin(9600);
 if (!SD.begin(SD_ChipSelectPin)) // returns 1 if the card is present
 {
  Serial.println("SD fail");
  return;
 }

 tmrpcm.setVolume(5); //
 tmrpcm.play("1.wav"); 
  Serial.println ("Playing");//the sound file "song" will play each time the arduino powers up, or is reset
                          //try to provide the file name with extension
                     
}


void loop()
{  
  while(digitalRead(next)==0)
  {
    if(digitalRead(next)==0)
    {
      if(temp<10)//temp should be lesser than no. of songs 
      temp=temp+1;
      while(digitalRead(next)==0);
      delay(200);
      song();
    }
  }
}


void song (void)
{
       if(temp==1)
  {
    tmrpcm.play("1.wav");  
  }
  else if(temp==2)
  {
    tmrpcm.play("2.wav");  
  }
  else if(temp==3)
  {
    tmrpcm.play("3.wav");  
  }
  else if(temp==4)
  {
    tmrpcm.play("4.wav");  
  }
  else if(temp==5)
  {
    tmrpcm.play("5.wav");  
  }
  else if(temp==6)
  {
    tmrpcm.play("6.wav");  
  }
  else if(temp==7)
  {
    tmrpcm.play("7.wav");  
  }
  else if(temp==8)
  {
    tmrpcm.play("8.wav");  
  }
  else if(temp==9)
  {
    tmrpcm.play("9.wav");  
  }
  else if(temp==10)
  {
    tmrpcm.play("10.wav");  
  }
}
