# Home-Automation-using-Arduino-Relay-and-Bluetooth-Module-HC-05
This project implements a home automation system using an Arduino and an 8-channel relay module. The system allows users to control various home appliances and devices remotely through a serial communication interface.

## Features
- **8-Channel Relay Control:** The system supports the control of up to 8 different electrical devices using individual relays.
- **Remote Control:** Users can send commands to the Arduino using a serial communication interface (e.g., via a smartphone or computer).
- **Versatility:** Suitable for controlling lights, fans, or any other electrical appliances within the capacity of the relays.

## Hardware Requirements
- Arduino Board
- 8-Channel Relay Module
- Jumper Wires
- Power Supply for the Relay Module
- Home Appliances to Control

## Software Requirements
- Arduino IDE
- MIT app inventor 

## Setup Instructions
1. Connect the 8-channel relay module to the Arduino board using jumper wires.
2. Connect the home appliances to the relay outputs.
3. Upload the Arduino sketch provided in this repository to the Arduino board.
4. Open a serial communication terminal on your computer or use a smartphone app to send commands to the Arduino.
## **circuit diagram **
Model 
![ciruit_diagram](https://github.com/SYEDASHRUF/Home-Automation-using-Arduino-Relay-and-Bluetooth-Module-HC-05/assets/86299480/265de430-c831-4c7f-b46c-e5b826414fbb)

## **block diagram **
![WhatsApp Image 2023-11-27 at 15 19 56_810b1279](https://github.com/SYEDASHRUF/Home-Automation-using-Arduino-Relay-and-Bluetooth-Module-HC-05/assets/86299480/21e84ae1-efca-4f57-ba2e-91ee456691dd)

## code for Arduino Uno
String inputs;
#define relay1 2 // Connect relay1 to pin 2
#define relay2 3 // Connect relay2 to pin 3
#define relay3 4 // Connect relay3 to pin 4
#define relay4 5 // Connect relay4 to pin 5
#define relay5 6 // Connect relay5 to pin 6
#define relay6 7 // Connect relay6 to pin 7
#define relay7 8 // Connect relay7 to pin 8
#define relay8 9 // Connect relay8 to pin 9

void setup() {
  Serial.begin(9600); // Set rate for communicating with the phone
  pinMode(relay1, OUTPUT); // Set relay1 as an output
  pinMode(relay2, OUTPUT); // Set relay2 as an output
  pinMode(relay3, OUTPUT); // Set relay3 as an output
  pinMode(relay4, OUTPUT); // Set relay4 as an output
  pinMode(relay5, OUTPUT); // Set relay5 as an output
  pinMode(relay6, OUTPUT); // Set relay6 as an output
  pinMode(relay7, OUTPUT); // Set relay7 as an output
  pinMode(relay8, OUTPUT); // Set relay8 as an output

  // Turn off all relays initially
  digitalWrite(relay1, LOW);
  digitalWrite(relay2, LOW);
  digitalWrite(relay3, LOW);
  digitalWrite(relay4, LOW);
  digitalWrite(relay5, LOW);
  digitalWrite(relay6, LOW);
  digitalWrite(relay7, LOW);
  digitalWrite(relay8, LOW);
}

void loop() {
  while (Serial.available()) {
    delay(10);
    char c = Serial.read();
    if (c == '#') {
      break; // Stop the loop once # is detected after a word
    }
    inputs += c; // Means inputs = inputs + c
  }

  if (inputs.length() > 0) {
    Serial.println(inputs);

    // Use a switch statement for cleaner code
    switch (inputs[0]) {
      case 'A':
        digitalWrite(relay1, LOW);
        break;
      case 'a':
        digitalWrite(relay1, HIGH);
        break;
      case 'B':
        digitalWrite(relay2, LOW);
        break;
      case 'b':
        digitalWrite(relay2, HIGH);
        break;
      case 'C':
        digitalWrite(relay3, LOW);
        break;
      case 'c':
        digitalWrite(relay3, HIGH);
        break;
      case 'D':
        digitalWrite(relay4, LOW);
        break;
      case 'd':
        digitalWrite(relay4, HIGH);
        break;
      case 'E':
        digitalWrite(relay5, LOW);
        break;
      case 'e':
        digitalWrite(relay5, HIGH);
        break;
      case 'F':
        digitalWrite(relay6, LOW);
        break;
      case 'f':
        digitalWrite(relay6, HIGH);
        break;
      case 'G':
        digitalWrite(relay7, LOW);
        break;
      case 'g':
        digitalWrite(relay7, HIGH);
        break;
      case 'H':
        digitalWrite(relay8, LOW);
        break;
      case 'h':
        digitalWrite(relay8, HIGH);
        break;
    }
    inputs = "";
  }
}

## **App interface **
![WhatsApp Image 2023-11-27 at 14 19 54_e76f4af8](https://github.com/SYEDASHRUF/Home-Automation-using-Arduino-Relay-and-Bluetooth-Module-HC-05/assets/86299480/3a10e5d8-5259-4ae8-a762-eebd44cd8cf0)


## Usage
- Send commands to control the corresponding relay channels.
  - Example: Sending '>data<' turns on/off the device connected to relays.

## License
This project is licensed under the [MIT License](LICENSE.md)
