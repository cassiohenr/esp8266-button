#include <ESP8266WiFi.h>
#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "NOME_DO_WIFI"; 
const char* password = "SENHA"; 
ESP8266WebServer server(80);                          //PORTA TCP

void setup() 
{
    delay(200);                                 //Tempo para wifi estabilizar
    Serial.begin(115200);                       //Baud serial
    pinMode(16, OUTPUT);                        //GPIO_16 NO ESP STANDALONE
    pinMode(5, OUTPUT);                         //GPIO_5 NO ESP STANDALONE
    pinMode(4, OUTPUT);                         //GPIO_4 NO ESP STANDALONE
    pinMode(0, OUTPUT);                         //GPIO_0 NO ESP STANDALONE
    pinMode(2, OUTPUT);                         //GPIO_2 NO ESP STANDALONE
    
    pinMode(15, OUTPUT);                        //OUTPUT DO BUZZER 
    
    WiFi.softAP(ssid, password);                //Conf. Modo PA com senha e SSID
    IPAddress myIP = WiFi.softAPIP();           //IP no host
    Serial.println("IP do PA: ");
    Serial.print(myIP);                        //Mostra o IP host
    server.on("/MESA=1", MESA_1);              //Checa conexão com cliente específico ID = /led=1 .... /led=2...
    server.on("/MESA=1C", MESA_1);             //Checa conexão com cliente específico ID = /led=1 .... /led=2...
    server.on("/MESA=2", MESA_2);              //Checa conexão com cliente
    server.on("/MESA=2C", MESA_2);             //Checa conexão com cliente
    server.on("/MESA=3", MESA_3);              //Checa conexão com cliente específico ID = /led=1 .... /led=2...
    server.on("/MESA=3C", MESA_3);             //Checa conexão com cliente específico ID = /led=1 .... /led=2...
    server.on("/MESA=4", MESA_4);              //Checa conexão com cliente
    server.on("/MESA=4C", MESA_4);             //Checa conexão com cliente
    server.on("/MESA=5", MESA_5);              //Checa conexão com cliente específico ID = /led=1 .... /led=2...
    server.on("/MESA=5C", MESA_5C);        
    server.begin();                             //Dá run no server
    Serial.println("Server Rodando...");
}

void loop()
{server.handleClient();}
//--------------------------------------------------
void MESA_1()
{
 digitalWrite(16, HIGH);                                                                    
 bip_simples();      
 String s = "ALE_MESA_1"; server.send(200,"text",s); Serial.println("ALE_MESA_1");    
}
void MESA_1C()
{
 bip_duplo();
 digitalWrite(16,LOW);delay(500);digitalWrite(16,HIGH);delay(500);digitalWrite(16,LOW);delay(500);digitalWrite(16,HIGH);delay(500);           
 String s = "ALE_MESA_1_CONTA"; server.send(200,"text",s); Serial.println("ALE_MESA_1_CONTA");    
}
//-------------------------------------------------
void MESA_2()
{
 digitalWrite(5, HIGH);                                                             
 bip_simples();                                             
 String s = "ALE_MESA_2"; server.send(200,"text",s); Serial.println("ALE_MESA_2");       
}
void MESA_2C()
{
 bip_duplo();
 digitalWrite(5,LOW);delay(500);digitalWrite(5,HIGH);delay(500);digitalWrite(5,LOW);delay(500);digitalWrite(5,HIGH);delay(500);           
 String s = "ALE_MESA_2_CONTA"; server.send(200,"text",s); Serial.println("ALE_MESA_2_CONTA");       
}
//-------------------------------------------------
void MESA_3()
{
 digitalWrite(4, LOW);        
 bip_simples();
 String s = "ALE_MESA_3"; server.send(200,"text",s); Serial.println("ALE_MESA_3");       
}
void MESA_3C()
{
 bip_duplo();
 digitalWrite(4,LOW);delay(500);digitalWrite(4,HIGH);delay(500);digitalWrite(4,LOW);delay(500);digitalWrite(4,HIGH);delay(500);    
 String s = "ALE_MESA_3_CONTA"; server.send(200,"text",s); Serial.println("ALE_MESA_3_CONTA");       
}
//-------------------------------------------------
void MESA_4()
{
 digitalWrite(0, LOW);        
 bip_simples();                                                                
 String s = "ALE_MESA_4"; server.send(200,"text",s); Serial.println("ALE_MESA_4");       
}

void MESA_4C()
{
 bip_duplo();
 digitalWrite(0,LOW);delay(500);digitalWrite(0,HIGH);delay(500);digitalWrite(0,LOW);delay(500);digitalWrite(0,HIGH);delay(500);    
 String s = "ALE_MESA_4_CONTA"; server.send(200,"text",s); Serial.println("ALE_MESA_4_CONTA");       
}
//-------------------------------------------------
void MESA_5()
{
 digitalWrite(2, LOW);            
 bip_simples();
 String s = "ALE_MESA_5"; server.send(200,"text",s); Serial.println("ALE_MESA_5");       
}
void MESA_5C()
{
 bip_duplo();
 digitalWrite(2,LOW);delay(500);digitalWrite(2,HIGH);delay(500);digitalWrite(2,LOW);delay(500);digitalWrite(2,HIGH); delay(500);    
 String s = "ALE_MESA_5_CONTA"; server.send(200,"text",s); Serial.println("ALE_MESA_5_CONTA");       
}
//-------------------------------------------------
void bip_duplo()
{digitalWrite(15,LOW);delay(500);digitalWrite(15,HIGH);delay(500);digitalWrite(15,LOW);delay(500);digitalWrite(15,HIGH);delay(500);}

void bip_simples()
{digitalWrite(15,LOW);delay(500);digitalWrite(15,HIGH);delay(500);}
