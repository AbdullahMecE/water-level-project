//water-level-project

// Pin for sensor
const int sensorPin = A0;

// LED pins
const int redLED = 2;
const int yellowLED = 3;
const int greenLED = 4;

int sensorValue = 0;

void setup() {
  Serial.begin(9600);

  pinMode(redLED, OUTPUT);
  pinMode(yellowLED, OUTPUT);
  pinMode(greenLED, OUTPUT);
}

void loop() {
  // Read water level sensor
  sensorValue = analogRead(sensorPin);
  Serial.print("Water Level Value: ");
  Serial.println(sensorValue);
  delay(100);

  // LOW LEVEL: 100–400
  if (sensorValue >= 100 && sensorValue <= 400) {
    digitalWrite(redLED, HIGH);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, LOW);
  }

  // MEDIUM LEVEL: 401–700
  else if (sensorValue > 400 && sensorValue <= 700) {
    digitalWrite(redLED, HIGH);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(greenLED, LOW);
  }

  // HIGH LEVEL: above 700
  else if (sensorValue > 700) {
    digitalWrite(redLED, HIGH);
    digitalWrite(yellowLED, HIGH);
    digitalWrite(greenLED, HIGH);
  }

  // NO WATER / BELOW RANGE
  else {
    digitalWrite(redLED, LOW);
    digitalWrite(yellowLED, LOW);
    digitalWrite(greenLED, LOW);
  }
}
