//Include The Hardware

#include <Wire.h>
#include <LiquidCrystal_I2C.h>

LiquidCrystal_I2C lcd(0x27, 16, 2); //Depends on what Lcd you have


// Install the Joystick & Led Pins 

const int LEDN = 10; // Red LED (Insert to D10)
const int LEDE = 11; // Green LED (Insert to D11)
const int LEDW = 9; // Blue LED (Insert to D9)
const int LEDS = 8; // Yellow LED (Insert to D8)
const int VRx = A0; // Our Y (Insert to Analog 0)
const int VRy = A1; // Our X (Insert to Analog 1)
const int SW = 12; // Our Centre Button (Insert to D12)



void setup() {

  //Led Pin as outputs

  pinMode(LEDN, OUTPUT); // North Indicates Up and Our Blue LED Pin
  pinMode(LEDE, OUTPUT); // East Indicates Right and our Red LED pin
  pinMode(LEDW, OUTPUT); // West Indicates Left and our Yellow LED pin
  pinMode(LEDS, OUTPUT); // South Indicates Down and our Green LED pin

//Joystick button input

  pinMode(SW, INPUT_PULLUP);

  //Lcd Input

  lcd.init();
lcd.backlight();

lcd.setCursor(0, 0);
lcd.print(" INPUT ");

}

// Joystick Reading Section

void loop() {
  int xVal = analogRead(VRx); 
  int yVal = analogRead(VRy); 
  int buttonState = digitalRead(SW); 

  // Control LEDs based on joystick movement
  if (xVal < 400) digitalWrite(LEDN, HIGH); // Left
  else digitalWrite(LEDN, LOW);

  if (xVal > 600) digitalWrite(LEDE, HIGH); // Right
  else digitalWrite(LEDE, LOW);

  if (yVal < 400) digitalWrite(LEDW, HIGH); // Up
  else digitalWrite(LEDW, LOW);

  if (yVal > 600) digitalWrite(LEDS, HIGH); // Down
  else digitalWrite(LEDS, LOW);

// Joystick Led Conditions
 
  if (buttonState == LOW) { 
    digitalWrite(LEDN, HIGH);
    digitalWrite(LEDE, HIGH);
    digitalWrite(LEDW, HIGH);
    digitalWrite(LEDS, HIGH);
  }else{ 
    digitalWrite(LEDN, LOW);
    digitalWrite(LEDE, LOW);
    digitalWrite(LEDW, LOW);
    digitalWrite(LEDS, LOW);
  }

  //Lcd Screen Conditions

  lcd.setCursor(0, 1);
lcd.print("                "); // Clear line
lcd.setCursor(0, 1);

if (buttonState == LOW) {
    lcd.print("Centre");
}
else if (xVal < 400) {
    lcd.print("^");
}
else if (xVal > 600) {
    lcd.print("v");
}
else if (yVal < 400) {
    lcd.print(">");
}
else if (yVal > 600) {
    lcd.print("<");
}
else {
    lcd.print("    ");
}

  delay(50); 
}


