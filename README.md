 const int trigPin = 9; // Trig pin of the sensor
const int echoPin = 10; // Echo pin of the sensor

void setup() {
  // Initialize serial communication
  Serial.begin(9600);
  
  // Set trigPin as OUTPUT and echoPin as INPUT
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);

  Serial.println("Ultrasonic Sensor Test");
}

void loop() {
  // Clear the trigPin
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);

  // Trigger the sensor by setting the trigPin HIGH for 10 microseconds
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  // Read the echoPin and calculate the distance
  long duration = pulseIn(echoPin, HIGH);
  float distance = (duration * 0.0343) / 2; // Convert to cm

  // Print the distance to Serial Monitor
  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  delay(500); // Wait 500 ms before the next measurement
}
