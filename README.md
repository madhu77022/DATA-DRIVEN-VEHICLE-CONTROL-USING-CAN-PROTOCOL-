🚗 Data-Driven Vehicle Control Using CAN Protocol

🎯 Aim

The main objective of this project is to:

Monitor and display the engine temperature.

Provide a reverse alert using distance sensing.

Control door glass windows (via LEDs) based on user input.

All communication between modules is handled through the CAN protocol.



---

🧠 Project Insights

This project helps in gaining:

Practical knowledge of Embedded C programming.

Hands-on experience with LPC2129 architecture, including GPIO, ADC, External Interrupts, and CAN interface.

Clear understanding of CAN (Controller Area Network) protocol in real-time embedded systems.



---

📦 Block Diagram

> [Insert Block Diagram Image Here]



The system is split into three nodes:

1. Main Node – Handles temperature sensing, user input, and display.


2. Window Glass Control Node – Controls door window LEDs based on input from main node.


3. Reverse Alert Node – Detects object proximity and alerts main node.




---

🧰 Hardware Requirements

LPC2129 Microcontroller

CAN Transceiver (MCP2551)

DS18B20 – Digital Temperature Sensor

GP2D12 – Distance Sensor

16x2 LCD

Switches (SW, SW1, SW2)

LEDs (for door window simulation)

USB to UART Converter



---

💻 Software Requirements

Embedded C Programming

Keil µVision (C Compiler and IDE)

Flash Magic (to burn code into LPC2129)



---

🔁 Implementation Sequence

1. Folder Setup

Create a dedicated folder for your project.



2. Module Testing (Individually)

✅ LCD: Display character, string, and integer constants.

✅ ADC: Read potentiometer values and display on LCD.

✅ Distance Sensor: Read GP2D12 and show object distance on LCD.

✅ External Interrupts: Count number of interrupts and display on LCD.

✅ Temperature Sensor: Read and display engine temperature (DS18B20).

✅ CAN: Download and test basic CAN communication code.

✅ External Interrupt Test Code: Check switch press detection.



3. Node Implementation

🧩 Main Node

Reads engine temperature and displays on LCD.

Based on SW1/SW2 press count, sends control command via CAN to Window Glass Control Node.

Reads data from Reverse Alert Node via CAN:

If value is 1, triggers reverse alert indication.


Uses external interrupts to detect switch status.


🧩 Window Glass Control Node

Listens for control commands from main node.

Simulates window movement using LEDs:

Number of LEDs ON = Value received from main node.



🧩 Reverse Alert Node

Continuously reads GP2D12 distance values.

Compares with set limit:

If below limit → Sends 1 to main node (alert).

Else → Sends 0 to main node.







---

✅ Completion Criteria

All modules work correctly.

CAN communication is established between nodes.

Data transmission and reception is accurate.

All expected output behaviors are verified:

Temperature reading.

Reverse alert indication.

LED-based window control simulation.

📂 Directory Structure (Example)

/Vehicle_CAN_Project
│
├── /Main_Node
│   ├── main.c
│   ├── lcd.c
│   └── ds18b20.c
│
├── /Window_Glass_Node
│   └── window_control.c
│
├── /Reverse_Alert_Node
│   └── reverse_alert.c
│
├── /Docs
│   ├── README.md
│   └── BlockDiagram.jpg
│
└── FlashMagic_Config.txt


---

📝 Notes

Use external interrupts (EINTx) for all switch inputs.

Always test each module in isolation before integrating.

Carefully manage CAN message IDs to prevent conflicts.

Use LEDs instead of motors for window simulation to simplify testing and reduce hardware risks.


