//bluetooth-lcd-arduini-uno


 #include <LiquidCrystal.h>

// Initialize the LCD: RS, E, D4, D5, D6, D7
LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

void setup() {
  lcd.begin(16, 2); // Initialize 16x2 LCD
  lcd.print("Waiting..."); // Display initial message
  Serial.begin(9600); // Start serial communication for Bluetooth
}

void loop() {
  // Check if Bluetooth data is available
  if (Serial.available()) {
    lcd.clear(); // Clear LCD screen
    delay(10);   // Short delay for stability
    
    String receivedText = ""; // Variable to store received text
    
    // Read all available characters
    while (Serial.available()) {
      char c = Serial.read(); // Read a character
      receivedText += c;      // Append to string
    }
    
    // Display received text on LCD
    lcd.setCursor(0, 0); // Set cursor to the first line
    lcd.print("Received:");
    lcd.setCursor(0, 1); // Set cursor to the second line
    lcd.print(receivedText); // Display text
  }
}
