#include <ESP8266WiFi.h>
#include <WiFiClient.h>
const char* ssid = "WIFI_DO_SERVER"; 
const char* password = "SENHA_DO_WIFI";
const char* host = "192.168.4.1";                                       //Configs do PA/host


void setup() 
{
  Serial.begin(115200);                                                 
  delay(10);                                                            
  pinMode(13,INPUT);      
  pinMode(2, OUTPUT);                                            
  WiFi.mode(WIFI_STA);                                                  
  WiFi.begin(ssid, password);                                            
  
  while (WiFi.status() != WL_CONNECTED) 
  {                                                                  
     delay(500);                                                        
     Serial.print(".");                                                                                                                
  }
    Serial.println("");
    Serial.println("WiFi connected");
    Serial.println("IP address: ");
    Serial.println(WiFi.localIP());                                    
}

void loop() 
{
    if(digitalRead(13)==0)                                             
    {   
      digitalWrite(2,LOW);                                             
      Serial.print("Conectando a ");                                      
      Serial.println(host);
      WiFiClient client;                                                  
    
      const int Port = 80;
      if (!client.connect("192.168.4.1", Port))
      {Serial.println("Falha na Conexão");return;}

      String pack = "/MESA=5";                                        
      client.print(String("GET ") + pack +" HTTP/1.1\r\n" + "Host: " + host + "\r\n" + "Connection: close\r\n\r\n");    //Requisição
      delay(10);
                                                  
      while(client.available())                                       
      {
      String line = client.readStringUntil('\r');
      Serial.println(line);
      digitalWrite(2,HIGH);                                                 
      }
     }

    if(digitalRead(12)==0)     //REQUISIÇÃO PARA "PEDIR A CONTA"
    {   
      digitalWrite(2,LOW);                                                   
      Serial.print("Conectando a ");                                        
      Serial.println(host);
      WiFiClient client;                                                    
    
      const int Port = 80;
      if (!client.connect("192.168.4.1", Port))
      {Serial.println("Falha na Conexão");return;}

      String pack = "/MESA=5C";                                        
      client.print(String("GET ") + pack +" HTTP/1.1\r\n" + "Host: " + host + "\r\n" + "Connection: close\r\n\r\n");    //Requisição
      delay(10);
                                                  
      while(client.available())                                       
      {
      String line = client.readStringUntil('\r');
      Serial.println(line);
      digitalWrite(2,HIGH);         //GPIO_2
      }
    }
}
