// Define motor pins
#define IN1 4
#define IN2 5
#define IN3 6
#define IN4 7

// Setup function
void setup() {
  // Initialize motor pins as outputs
  pinMode(IN1, OUTPUT);
  pinMode(IN2, OUTPUT);
  pinMode(IN3, OUTPUT);
  pinMode(IN4, OUTPUT);
  
  // Initialize serial communication with voice recognition module
  Serial.begin(9600);
}

// Loop function
void loop() {
  // Check if a voice command is received from the module
  if (Serial.available() > 0) {
    int command = Serial.read(); // Read the command
    
    // Voice command processing
    if (command == 1) {
      moveForward();
    } else if (command == 2) {
      moveBackward();
    } else if (command == 3) {
      turnLeft();
    } else if (command == 4) {
      turnRight();
    } else if (command == 5) {
      stopCar();
    }
  }
}

// Functions for movement
void moveForward() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void moveBackward() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void turnLeft() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, HIGH);
  digitalWrite(IN3, HIGH);
  digitalWrite(IN4, LOW);
}

void turnRight() {
  digitalWrite(IN1, HIGH);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, HIGH);
}

void stopCar() {
  digitalWrite(IN1, LOW);
  digitalWrite(IN2, LOW);
  digitalWrite(IN3, LOW);
  digitalWrite(IN4, LOW);
}
