Codigo: 
 
#include <Thermistor.h> //importando a biblioteca thermistor.h 
 
int motorPin = 3; // Motor ligado na porta 3 
const int pinoSensor = 0; //sensor de temperatura ligado na porta analogica 0 
double valorSensor = 0; // criando um double e atribuindo um valor 
Thermistor therm(pinoSensor); // atribuindo o calculo da biblioteca ao sensor de temperatura 
 
void setup() 
{ 
  Serial.begin(9600); 
  pinMode(motorPin, OUTPUT); // declarando o motor de giro como saida 
} 
void loop() 
{ 
   
  valorSensor = therm.getTemp(); // atribuindo o valor calculado no getTemp para o double  criado 
  Serial.print("Valor do Sensor = "); //imprimindo uma string no serial monitor 
  Serial.println(valorSensor);// imprimindo o valor do getTemp atribuido ao double criado 
  delay(1000); 
 
   if(valorSensor > 27.0) // criando uma condiçao para se o double maior que 27 
  { 
    analogWrite(motorPin, 1023); //ligando o motor de giro na rotaçao maxima 
  } 
  else 
    analogWrite(motorPin, 0);// desliga o motor de giro, ou mantem ele inativo 
   
} 
