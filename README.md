# SMOKE-DEDUCTION-BY-LED
In conclusion, LED-based photoelectric smoke detectors play a vital role in fire safety by utilizing the principle of light scattering to detect smoke particles, offering timely alerts, especially for smoldering fires
#define MQ2_DO 2        // Digital output pin of MQ-2
#define MQ2_AO A0       // Analog output (optional, for serial)
#define LED_PIN 8       // LED pin

int SensorDigitalOutput;
int SensorAnalogOutput;

void setup() {
  Serial.begin(9600);
  Serial.println("MQ-2 Smoke Detector Ready...");

  pinMode(MQ2_DO, INPUT);
  pinMode(LED_PIN, OUTPUT);

  delay(20000); // MQ-2 warm-up time
}

void loop() {
  // Read sensor values
  SensorDigitalOutput = digitalRead(MQ2_DO);
  SensorAnalogOutput = analogRead(MQ2_AO);

  // Serial monitor values
  Serial.print("Digital Output: ");
  Serial.println(SensorDigitalOutput);
  Serial.print("Analog Output: ");
  Serial.println(SensorAnalogOutput);

  // If smoke/gas detected (LOW signal)
  if (SensorDigitalOutput == LOW) {
    digitalWrite(LED_PIN, HIGH);           // LED ON
    Serial.println("Smoke detected!");
  } else {
    digitalWrite(LED_PIN, LOW);            // LED OFF
  }

  delay(200); // Small delay just to keep serial monitor readable
}
