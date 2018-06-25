// constants won't change. They're used here to set pin numbers:
const int Sensor_Pin = 0;     // the number of the pushbutton pin
const int Relay_Pin =  2;      // the number of the Relay pin
int Sensor_Value = 0;
int Attempts_Number = 0;
int Successful_Attempts_Number = 0;


// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN as an output.
  pinMode(Relay_Pin, OUTPUT);
  // initialize serial communication at 9600 bits per second:
  Serial.begin(9600);
}


void loop() {                                                     // the loop function runs over and over again forever
  digitalWrite(Relay_Pin, HIGH);                                  // turn the LED on (HIGH is the voltage level)
  Attempts_Number = Attempts_Number + 1;                          // add 1 to the counter
  delay(1000);                                                    // wait for a second
  Sensor_Value = analogRead(Sensor_Pin);                          // read the value of the sensor:
  Serial.print("Relay_Pin State = HIGH, the Sensor_Value = ");    // print out the value you read:
  Serial.println(Sensor_Value);
  if (Sensor_Value > 200) {
    Successful_Attempts_Number = Successful_Attempts_Number + 1;
  }
  Serial.print("Total number of attempts = ");
  Serial.println(Attempts_Number);
 
  Serial.print("Total number of successful attempts = ");
  Serial.println(Successful_Attempts_Number);
 
  Serial.print("The percentage of successful operation  = ");
  Serial.println( (Successful_Attempts_Number / Attempts_Number) * 100, 2);
  delay(1000);                                                    // wait for a second

  digitalWrite(Relay_Pin, LOW);                                   // turn the LED off by making the voltage LOW
  delay(1000);                                                    // wait for a second
  Sensor_Value = analogRead(Sensor_Pin);                          // read the value of the sensor:
  Serial.print("Relay_Pin State = LOW, the Sensor_Value = ");     // print out the value you read:
  Serial.println(Sensor_Value);
  delay(1000);                                                    // wait for a second
}
