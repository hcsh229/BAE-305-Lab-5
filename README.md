# BAE-305-Lab-5
# Lab 5: The Brain – Microcontrollers

Group Members: Heath Shewmaker and Terence Redford

Date Submitted: 3/5/2025
# Introduction:
The aim of this lab was to learn how to use microcontrollers. We used an Arduino Uno as our microcontroller and Arduino IDE to program the controller. Parts of our code also utilized mechanical components, such as potentiometers and photoresistors. We used these components to manipulate an LED in various ways, such as making it blink, dim, and brighten. 
# Methods: 
Step 1: There is a link provided in the manual to download the Arduino IDE, do as such. Other programming languages will work with the Arduino, but we will be using example codes already integrated into this program. 
-	For the remainder of the lab, it will be crucial to carefully read the manual. Following directions precisely will help you navigate the program and decide on the example codes you will need. It will also ensure that you select the correct COM port and board you are using to allow communication between your computer and the Arduino. 

Step 2: Create the circuit provided in the Arduino manual (lab manual 4.C). It is a simple circuit, only requiring a resistor in series with the pinned connection of the breadboard. Don’t forget to ground the other side of the LED. It is also essential to wire the LED correctly, since it is functionally a diode, meaning it has a positive and negative terminal, designed for current to flow in at the positive terminal and out of the negative terminal.

 ![image](https://github.com/user-attachments/assets/9ec34e74-a4ae-4354-8096-37461398db78)

Figure 1: Simple LED circuit with resistor in series

Step 3: Open the blink program from the example files and upload it to your Arduino. This code should make the LED turn on and off based on the delay set in your code. Make sure to read and answer the discussion question associated with this circuit before moving on. Pictured below is the blink program.

 ![image](https://github.com/user-attachments/assets/075a4b77-20ca-4ae3-88b2-329710afcab1)

Figure 2: Given code from Arduino example Blink

Code explanation: The “setup()” function only runs when the program is initially executed. In this case the only code included in this function is to set the variable LED_BUILTIN (which was declared before this to be the digital pin 13), to be an output pin. This indicates to the microcontroller that we intend to send power to this pin, and not receive power to it. For the code in the “loop()” function, which runs continuously once the setup has executed, we used the “digitalWrite()” function on the LED_BUILTIN variable in order to write it to a value of either high or low. This causes the arduino board to supply the LED with voltage if high, or cut off the voltage if low. By adding instances of the “delay()” function, we could determine how quickly the voltage would be made high or low.

Step 4: Add a potentiometer to your previous circuit. This is done by connecting it to power and ground (sides), while connecting the variable resistance pin (middle) to A0 on the Arduino. This connection is pictured below. 

![image](https://github.com/user-attachments/assets/d58b885b-9c53-4513-b089-7440db7c3d1d)

Figure 3: LED circuit utilizing potentiometer

Step 5: Open the Analog Read Serial program from the example files and upload it to your Arduino. This code should allow you to change how quickly the LED blinks based on the position of the potentiometer. Make sure to read and answer the discussion question associated with this circuit before moving on. Pictured below is the Analog Read Serial program.
 
![image](https://github.com/user-attachments/assets/ada81d46-5b68-49db-bf4a-1783e7e8e4d5)

Figure 4: Given code for manipulation of LED blink using potentiometer

Code Explanation: In the “setup()” function we initialized communication with “Serial.Begin()”, and set the communication rate to be 9600 bits per second. In the main code of the program we used analogRead() to check the incoming voltage into pin A0, which could be modified by increasing or decreasing the resistance of the potentiometer. The loop would consistently read this value and report it to us in the serial monitor.

Step 6: Replace the potentiometer from the previous circuit with a photoresistor in series with a 10k ohm resistor. This can be done with 5V on one side of the photoresistor, ground to the other side of the resistor, and pin A0 to the node between the two. This connection can be seen below.
 
 ![image](https://github.com/user-attachments/assets/a918bf25-3641-4fd8-9ab9-7a9a621b5db7)

Figure 5: LED circuit utilizing photoresistor

Step 7: Use the same code from the previous program (figure 4), but you will have to make small additions to make the LED turn on and off with light exposure. Once you have adjusted your code, block the light coming into the photoresistor with different objects and note the minimum and maximum analog values that your program outputs. If having trouble getting the light to turn on, try completely covering all sides of the photoresistor, as it takes in light from angles other than just above. 

Step 8: Rebuild the circuit from step 4, but swap the LED pin to a PWM capable pin (~). This connection can be seen in the figure below.
 
 ![image](https://github.com/user-attachments/assets/00b35145-b827-457e-a9f2-8414c6245cce)

Figure 6: LED circuit using a PWM signal from a potentiometer

Step 9: You can use the code from part 2 (step 5) with a few changes to convert this potentiometer signal into a PWM signal. These changes can be seen in the results section below (step 9). 

# Results: 
Step 3: We were able to get the example code to blink the LED with no alterations. However, to get the LED to appear constant as requested from the discussion question, we had to substantially decrease the delay value as seen below.  

![image](https://github.com/user-attachments/assets/0b8762a8-3990-4f69-96dd-dabb6a3bd854)

Figure 7: Modified code for LED to stay on “constantly”

Step 5: We were able to get the example code to blink the LED with no alterations. However, if issues are occurring, make sure you have your Baud Rate set to 9600bps. Pictured below is the given code, with the correct Baud Rate highlighted.

![image](https://github.com/user-attachments/assets/8b94655c-6469-4373-8a7c-91bb6569b5ab)

Figure 8: Given code for potentiometer circuit (possible issue highlighted)

Step 7: We found that the maximum and minimum analog values output by our program were 1000 and 26, respectively. To get our LED to react as a “night light”, we had to make some changes to our code, highlighted in the figure below. 
 
 ![image](https://github.com/user-attachments/assets/46356f4b-7cd4-40cc-8d06-1afdb6fd69b1)

Figure 9: Modified code for photoresistor activated “night light”

Step 9: The changes to the part 2 code are highlighted in the figure below. 
 
 ![image](https://github.com/user-attachments/assets/b96d346d-761b-4df2-ab3d-668ce4bf1aec)

Figure 10: Modified code for PWM signal from potentiometer
# Discussion:
Part 1: 
Your LED flashes with a delay from the uploaded code. Decrease this delay (after both write instructions) until the LED just stops blinking—that is until the light is still blinking but appears to stay constantly
illuminated.

a. What is the value of your delay now?

b. What field may this “persistence of vision” play a greater role in?

-	The LED appears to stay on constantly at a delay value of 10, much lower than the original value of 1000. This is an example of frame rate, which is used to create videos and other light emissions in a manner which appears smooth or constant to the human eye. This occurs because the rate at which our nerves can transfer signals to our brain is limited and therefore if we can reduce the time between blinks to be so short that our eyes cannot send the signal to our brain, it appears to our eyes as if the light never turns off.  If this was not utilized, the lights we use every day would flicker constantly, causing irritation and rendering them useless. This can also decode a factor in smoothly displaying graphics, since they are also essentially a compilation of still frames that change quick enough to trick our eyes into seeing movement.

Part 2: 

a. What is the difference between an analog and a digital signal?

b. In your lab report, list a few examples of real-world examples that can be described by an analog
signal. Likewise, what are the two states which can be conveyed by a digital signal?

c. What happens to the Serial Monitor Refresh rate as you move the potentiometer to control the LED blinking time?

-	Most real-world measurements are analog, meaning they exist as an infinitely detailed continuum of numbers, such as temperature, time, and length. These measurements can be almost infinitely more precise. Digital signals have discrete values, with most of them being either on or off. 

-	By moving the resistor, we did not change the serial monitor refresh rate. This refresh rate was defined by the rate at which the microcontroller executes the code. Moving the potentiometer was only able to change the value that we reported, not how often the value was reported.

Part 3: 

a. Does the LED turn on immediately after blocking the light? What about when you remove the object blocking the light, does the LED turn off immediately? Why?

-	The LED turns on and off a very short time after blocking or removing the blockage from the light. This is because our code runs the main loop of code a certain number of times a second. Although the LED Changed very quickly, we were able to observe this very slight delay.

Part 4: 

a. Connect the oscilloscope to the LED pin and observe and record what happens to the signal and the LED brightness when you turn the knob of the potentiometer.

-	The LED gets brighter or dimmer depending on which way you turn the potentiometer. You can see this trend on the oscilloscope as well, as when the LED gets brighter, the PWM signal seems to “grow”. This essentially occurs because the code translates the measured resistance of the potentiometer to a percentage, and then allows us to map that percentage onto the desired duty cycle for the PWM square wave signal. The result of this is that because the signal is so quick, we cannot see the LED flickering, and therefore what our eyes see is the time-averaged brightness of the LED, which is directly related to the percentage of the resistance encoded from the potentiometer.

![image](https://github.com/user-attachments/assets/89a84172-b1cb-4928-ab05-f3039b818e10)

Figure 11: Display of “small” PWM signal from potentiometer
 
 ![image](https://github.com/user-attachments/assets/e1e7d5a7-d43e-4b65-8161-7a864b883a5c)

Figure 12: Display of “large” PWM signal from potentiometer
# Conclusion: 
The aim of this lab was to discover the various ways we could interact with the microcontroller on our Redboards. We investigated the function of digital pins as outputs, how analog pins can be used to take in sensor values, the function of PWM enabled pins, and we discovered some nuances of using the Arduino IDE to interact with components on the breadboard. We learned that digital pins can be used as both input and output pins and need to be programmed accordingly. We only used them as inputs in this lab, since all the outputs were analog signals, which we learned could be interpreted by the Analog pins. Once we understood how digital outputs and analog inputs could be handled in Arduino IDE, we were able to create programs that measured the resistance of either a potentiometer or a photoresistor and powered an LED with them using digital outputs. Finally, we learned about PWM and how it is a powerful intermediary between digital and analog signals. By measuring the time that a “High” signal is received, we can simulate analog outputs by averaging these signals over time. We put this into practice by using the analog input of a potentiometer’s resistance to encode the duty cycle of a PWM that was delivered to an LED, and we discovered that PWM, despite being a digital signal, could make the LED brighter or dimmer.
