// Pin motor kiri
#define IN1 12
#define IN2 13
#define ENA 25  // PWM motor kiri

// Pin motor kanan
#define IN3 14
#define IN4 15
#define ENB 26  // PWM motor kanan

// Channel PWM untuk ESP32
#define CHANNEL_A 0
#define CHANNEL_B 1

void setup() {
  // Arah motor
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);

  // Setup PWM
  ledcSetup(CHANNEL_A, 1000, 8);  // 1kHz, 8-bit resolution
  ledcAttachPin(ENA, CHANNEL_A);
  ledcSetup(CHANNEL_B, 1000, 8);
  ledcAttachPin(ENB, CHANNEL_B);

  // Gerakkan motor maju langsung di setup
  maju(220);  // Kecepatan tinggi (0–255)
}

void loop() {
  // Tidak perlu apa-apa jika motor mau nyala terus
}

void maju(int kecepatan) {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);

  ledcWrite(CHANNEL_A, kecepatan);
  ledcWrite(CHANNEL_B, kecepatan);
}
