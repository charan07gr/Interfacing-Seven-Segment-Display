# Interfacing Seven Segment Display

## AIM:
To display the characters and numbers in the seven segment display using Arduino UNO controller.

## Software required:
Arduino IDE </br>
Proteous

## PROCEDURE:
### Arduino IDE
Step1:Open the Arduino IDE </br>
Step2: Go to file and select new file option </br>
Step3:Type the program </br>
Step4:Go to file and select save option to save the program </br>
Step5:Go to sketch and select verify or compile options </br>
Step6:If no error Hex file will be generated in the temporary folder </br>
### Proteus
Step7:Open the Proteus software </br>
Step8:Go to file select new design and click ok button </br>
Step9:Select component mode and click pick devices from the library </br>
Step10:Type the component name in the keyword to select the components and click ok button </br>
Step11:Design the circuit as per the diagram </br>
Step12:Double click the Arduino controller and upload the hex file generated by Arduino IDE </br>
Step13:Click start button and check the output

## THEORY:

### What is a seven-segment display?

The seven-segment display is a bunch of eight LEDs arranged in a particular pattern. The pattern traces an outline of the digit ‘8’. Out of these eight LEDs, seven are line-shaped arranged in the shape of number eight, and one is a circular LED. The circular LED is mostly used to indicate decimal points.Each of these eight LEDs is individually controllable via separate pins on the display module. Due to this particular arrangement, it can display numbers from 0 to 9 and alphabets from A to F. Since LEDs are cheap and easy to use, a seven-segment display is sufficient for simple projects.

### Understanding the 7 segment display

To properly understand how to use a seven-segment display in tandem with an Arduino or any system for that matter, we need to understand its internal as well as external construction.The internal circuit of a seven-segment display

![image](https://user-images.githubusercontent.com/71547910/235332708-1cd24f92-c15c-44eb-aade-e2bad64f6f5b.png)

Study the internal circuitry of a seven-segment display, as shown in the picture above carefully. You’ll notice the carefully laid out LEDs. Notice how in both the configurations, one off the two ends of the LEDs is connected to a common line. This common line is either GND (left) or VCC (right). Let’s talk about that a bit. Your 7-segment display is possibly one of two types: Common cathode,Common anode

### What is a common anode seven-segment display?

For an LED to light up, the anode needs to connect with a power source. And the cathode needs to connect with the ground. That’s the basic working of an LED.In a common anode display, all the eight LEDs have their anodes interconnected. This means that the power supply to all the LEDs will be via one common pin. But don’t we need to control each of these LEDs separately to display different characters.Thus the individual control comes from the free multiple cathode pins. To switch on any of the eight LEDs, its cathode pin needs to be grounded. And since the LEDs retain their individual cathode pins, we can use them to control them.All you need to remember is this: To light up a common anode seven-segment display, you have to ground/write a LOW output on the pins that need to be lit up

![image](https://user-images.githubusercontent.com/71547910/235332776-7ef7146a-16de-4a56-aff5-2937652364a8.png)

### What is the common cathode seven-segment display?

This type is just a reverse design of the common anode type. In a common cathode seven-segment display, all of the cathode pins are connected to a common ground (GND). Thus the individual control comes from the free multiple anode pins. To switch on any of the eight LEDs, its anode pin needs to be given power.All you need to remember is this: To light up a common cathode seven-segment display, you have to write a HIGH output on the pins that need to be lit up

![image](https://user-images.githubusercontent.com/71547910/235332805-4c1a1a34-0aec-4378-b621-f42b10d30391.png)

### Working principle of the seven-segment display

The LED segments are selected based on the decimal number. For example, if we want to display the number 8, we should select all of the LEDs a, b, c, d, e, f, g.You can turn on the needed LED segments, depending on the number or alphabet you wish to display. You can select the LED segments according to the table shown below. To display any character from the table below, you just need to send the corresponding hex codes to the right pins.

![image](https://user-images.githubusercontent.com/71547910/235332841-7159e75f-b403-43ff-bf96-8ef54ad0310a.png)

## PROGRAM:

int cnt=0;<\br>
int incPrev, decPrev;<\br>
void setup()<\br>
{<\br>
pinMode(0, INPUT);<\br>
pinMode(3, INPUT);<\br>
pinMode(5, INPUT);<\br>
pinMode(13, OUTPUT);<\br>
pinMode(12, OUTPUT);<\br>
pinMode(11, OUTPUT);<\br>
pinMode(10, OUTPUT);<\br>
pinMode(9, OUTPUT);<\br>
pinMode(8, OUTPUT);<\br>
pinMode(7, OUTPUT);<\br>
pinMode(6, OUTPUT);<\br>
}<\br>
void loop()<\br>
{<\br>
int inc = digitalRead(3);<\br>
int dec = digitalRead(5);<\br>
int res = digitalRead(0);<\br>
{<\br>
switch (cnt)<\br>
{<\br>
case 0://when count value is zero show”0” on disp<\br>
digitalWrite(13, HIGH);<\br>
digitalWrite(12, HIGH);<\br>
digitalWrite(11, HIGH);<\br>
digitalWrite(10, HIGH);<\br>
digitalWrite(9, HIGH);<\br>
digitalWrite(8, HIGH);<\br>
digitalWrite(7, LOW);<\br>
digitalWrite(6, LOW);<\br>
break;<\br>
case 1:// when count value is 1 show”1” on disp<\br>
digitalWrite(13, LOW);<\br>
digitalWrite(12, HIGH);<\br>
digitalWrite(11, HIGH);<\br>
digitalWrite(10, LOW);<\br>
digitalWrite(9, LOW);<\br>
digitalWrite(8, LOW);<\br>
digitalWrite(7, LOW);<\br>
digitalWrite(6, LOW);<\br>
break;<\br>
case 2:// when count value is 2 show”2” on disp<\br>
digitalWrite(13, HIGH);<\br>
digitalWrite(12, HIGH);<\br>
digitalWrite(11, LOW);<\br>
digitalWrite(10, HIGH);<\br>
digitalWrite(9, HIGH);<\br>
digitalWrite(8, LOW);<\br>
digitalWrite(7, HIGH);<\br>
digitalWrite(6, LOW);<\br>
break;<\br>
case 3:// when count value is 3 show”3” on disp<\br>
digitalWrite(13, HIGH);<\br>
digitalWrite(12, HIGH);<\br>
digitalWrite(11, HIGH);<\br>
digitalWrite(10, HIGH);<\br>
digitalWrite(9, LOW);<\br>
digitalWrite(8, LOW);<\br>
digitalWrite(7, HIGH);<\br>
digitalWrite(6, LOW);<\br>
break;<\br>
case 4:// when count value is 4 show”4” on disp<\br>
digitalWrite(13, LOW);<\br>
digitalWrite(12, HIGH);<\br>
digitalWrite(11, HIGH);<\br>
digitalWrite(10, LOW);<\br>
digitalWrite(9, LOW);<\br>
digitalWrite(8, HIGH);<\br>
digitalWrite(7, HIGH);<\br>
digitalWrite(6, LOW);<\br>
break;<\br>
}<\br>
}<\br>
if((inc == HIGH)&& (cnt < 3))<\br>
{<\br>
delay(1000);<\br>
cnt++;<\br>
switch (cnt);<\br>
}<\br>
if((dec == HIGH) && (cnt > 0))<\br>
{<\br>
delay(1000);<\br>
cnt--;<\br>
switch (cnt);<\br>
}<\br>
if ((res == HIGH)&& (cnt > 0))<\br>
{<\br>
delay(1000);<\br>
cnt=0;<\br>
switch (cnt);<\br>
}<\br>
}<\br>


## CIRCUIT DIAGRAM:

![image](https://user-images.githubusercontent.com/132322854/236758047-8a02e565-f324-472e-8beb-256218a40cbb.png)



## OUTPUT:

![image](https://user-images.githubusercontent.com/132322854/236757422-975918f7-ac26-4cfb-bb6d-c3badd7d0f42.png)


## RESULT:
Thus the characters and numbers are displayed in the seven segment display using Arduino UNO controller
