# Automatic-Street-Lighting-System-Using-LDR

# OBJECTIVE

The traditional lighting system has been limited to two options ON and OFF only, and it is not efficient because this kind of operations meant power loss due to continuing working on maximum voltage. Hence, wastage of power from street lights is one of the noticeable power loss, but with the use of automation, it leads to many new methods of energy and money saving. In this regard, controlling lighting system using Light Dependent Resistor (LDR).

The most natural solution is to control the street lights according to the outside lighting condition. This is we are aiming for in smart lighting system in which the street lights will be turned OFF during day-time, otherwise the lights will be remained Dim/ON. Our proposed design is aimed at efficiently replacing any light systems that are manually controlled, and this is accomplished with the proper arrangements of microcontroller Arduino Uno, LDR, and Resistors. In this scenario, when the intensity of sunlight impinges with LDR, street lights can be further controlled as per the desired requirements, automatically. 

# WORKING

Firstly, LDR will sense the intensity value of sunlight and send it to Arduino. Arduino will judge if the received value is above the threshold level (which is set independently by the user from the discrete value: 0-2023), then it will consider it as daytime and LEDs will remain OFF, or if the received value below the threshold level, Arduino will consider it as a night-time. 

# COMPONENTS : 

# A. Light Dependent Resistor (LDR) 

LDR is a Light Dependent Resistor whose resistance is dependent on the light impinging on it. The resistance offered by the sensor decreases with the increase in light strength and increases with the decrease in light strength. This device is used for detection of day-time and night-time because when sunlight falls on it, it will consider as day-time, and when there is no sunlight falls on it, it will be regarded as a night, as shown in Fig. 2b. These are very beneficial, especially in light/dark sensor circuits and help in automatically switching ON /OFF the street lights. 

# B. Arduino Uno 

The Arduino Uno  is a microcontroller board which is based on the ATmega328 series controllers and has an IDE (Integrated Development Environment) for writing, compiling and uploading codes to the microcontroller.  It has 14 digital input and output pins (of which 6 are PWM) and 6 analogue inputs for communication with the electronic components such as sensors, switches, motors and so on. It also has 16 MHz ceramic resonators, a USB connection jack, an external power supply jack, an ICSP (in-circuit serial programmer) header, and a reset button. Its operating voltage is 5v, input voltage 7 to 12v (limit up to 20v).

# C. LEDs 

An LED (light-emitting diode) is a PN junction diode which is used for emitting visible light when it is activated.  When the voltage is applied over its elements, electrons regroup with holes within the LED, releasing energy in the form of photons which gives the visible light. 

# D. Resistors 

A resistor is a passive electronic component, used with other electronic components such as LEDs and sensors to prevent or limit the flow of electrons through them as illustrated in Fig. 6. It works on the principle of Ohm’s law which prevent overflow of voltage.

For this very simple DIY Arduino project we need:
A breadboard
An arduino (whatever is handy)
LED (Light Emitting Diode)
LDR (Photoresistor)
A 10K Resistor for creating the voltage divider and a 220ohm resistor for the LED
Few breadboard friendly connecting wires
and a USB cable to upload the code to the Arduino

# ASSEMBLY

1. Connect the 3.3v output of the Arduino to the positive rail of the breadboard
2. Connect the ground to the negative rail of the breadboard
3. Place the LDR on the breadboard
4. Attach the 10K resistor to one of the legs of the LDR
5. Connect the A0 pin of the Arduino to the same column where the LDR and resistor is connected (Since the LDR gives out an analog 	        voltage, it is connected to the analog input pin on the Arduino. Arduino, with its built-in ADC (Analog to Digital Converter), then      converts the analog voltage from 0-5V into a digital value in the range of 0-1023). - Now connect the other end of the 10K resistor      to the negative rail - And the second (free) leg of the LDR to the positive rail
6. Place the LED on the breadboard
7. Connect the 220ohm resistor to the long leg (positive) of the LED
8. Then we will connect the other leg of the resistor to pin number 13 (digital pin) of the Arduino 
   and the shorter leg of the LED to the negative rail of the breadboard.

# CODE

const int ledPin = 13;

const int ldrPin = A0;

void setup() 
{  

    	Serial.begin(9600);
	pinMode(ledPin, OUTPUT);
	pinMode(ldrPin, INPUT);

}

void loop() 
{

    	int ldrStatus = analogRead(ldrPin);
	if (ldrStatus <= 200) 
	{
	
        	digitalWrite(ledPin, HIGH);  
		Serial.print("Its DARK, Turn on the LED : ");  
		Serial.println(ldrStatus);
    	} 
	else 
	{   
        	
		digitalWrite(ledPin, LOW);  
		Serial.print("Its BRIGHT, Turn off the LED : ");  
		Serial.println(ldrStatus);	
    }
   
}
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
