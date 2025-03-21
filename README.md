# VSD_SquadronFM_Project
<details>
  <summary>
Expand or Collapse
  </summary>
  
## Steps

<details>
  <summary>
Expand or Collapse
  </summary>

### Step 1: Understanding the verilog code:

<details>
  <summary>
Expand or Collapse
  </summary>



### Place where you can find the Verilog code:

<details>
  <summary>
Expand or Collapse
  </summary>

### You can find the verilog in the top.v file of any led  in the github repo given by you.

1) Link of the github repo:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main

2) Link of the verilog code:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/top.v

### Note: Here I have took blue led for Verilog code.


 </details>
  
### Purpose of the Verilog code:

  <details>
  <summary>
Expand or Collapse
  </summary>


### This Verilog code is responsible for controlling the RGB LED on the VSDSquadron FPGA Mini Board. Here’s what’s happening under it:

### 1) Outputs:

  a) led_red, led_blue, led_green --> These control the three colors of the onboard LED.

  b) testwire --> A test signal output for debugging.

### 2) Inputs:

  a) hw_clk --> The clock input from the board’s built-in oscillator.

 </details>
  
### How it works:

  <details>
  <summary>
Expand or Collapse
  </summary>

### 1) Using the Internal Oscillator:

  a) The FPGA has an internal clock generator that keeps everything running on time.

  b) This oscillator is set to a specific frequency to control the LED.

### 2) Counting Clock Cycles:

  a) A counter keeps track of time using the oscillator’s clock signal.

  b) This allows us to control the timing of the LED blinks.

### 3) Controlling the RGB LED:

  a) The logic inside the Verilog code turns the LED on and off at specific intervals.

  b) It ensures the LED doesn’t get too bright by setting current limits.

  </details>
  
### Verilog Code (top.v):

  <details>
  <summary>
Expand or Collapse
  </summary>

    module top (
    output led_red,
    output led_blue,
    output led_green,
    output testwire,
    input hw_clk
    );

    reg [23:0] counter;

    always @(posedge hw_clk) begin
        counter <= counter + 1;
    end

    assign led_red   = counter[23];  // Red LED blinks at a slower rate
    assign led_blue  = counter[22];  // Blue LED blinks slightly faster
    assign led_green = counter[21];  // Green LED blinks even faster
    assign testwire  = counter[20];  // Debug signal

    endmodule

### This is the Verilog code in led_blue (top.v) of the github repo

 1) Link of the verilog code:
    https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/top.v

 </details>
 </details>
 

  
  
  
### Step 2: Assigning Pins with the PCF File:
<details>
  <summary>
Expand or Collapse
  </summary>
  </summary>



### Place where you can find the pins cofiguration file (PCF) :

<details>
  <summary>
Expand or Collapse
  </summary>

### You can find the verilog in the VSDSquadronFM.pcf file of any led in the github repo given by you.
1) Link of the github repo:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main
   
2) Link of the pins cofiguration file (PCF) github repo:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf

### Note: Here I have took blue led for Verilog code.


  </details>

### Pin Mapping and Significance:
<details>
<summary>
Expand or Collapse
  </summary>

### This file maps the signals in our Verilog code to actual pins on the FPGA. Here’s the mapping along with the role of each connection:



## a) led_red:

  
### Link of the red led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_red/VSDSquadronFM.pcf
### 1) FPGA pins: 39
### 2) Purpose: Controls the red channel of the RGB LED. The Verilog code sets this pin high or low based on timing logic to turn the red light on or off.


## b) led_blue:


### Link of the blue led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf
 ### 1) FPGA pins: 40
 ### 2) Purpose: Controls the blue channel of the RGB LED. The Verilog module manipulates this pin to create blinking or color effects.



## c) led_green:

  
### Link of the green led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_green/VSDSquadronFM.pcf
 ### 1) FPGA pins: 41
 ### 2) Purpose: Controls the green channel of the RGB LED. It works in conjunction with the other two LED pins to mix colors.



## d) hw_clk:

  
 ### Link of the hw_clk's pcf file:
https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_white/VSDSquadronFM.pcf
  
 ### 1) FPGA pins: 20
 ### 2) Purpose: Receives the clock signal from the onboard oscillator. This signal is crucial for the counter logic in Verilog, which determines LED blinking speed.


## e) testwire:

  
  ### Link of the testwire's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_white/VSDSquadronFM.pcf
 ### 1) FPGA pins: 17
 ### 2) Purpose: This is an auxiliary output that can be used for debugging. It can carry signals that help monitor internal operations.



 
## f) Purpose of Pin Mapping:
  
### 1) The LED signals must be assigned correctly to their respective FPGA pins so that they physically control the onboard RGB LED.

### 2) The hw_clk input is essential because the Verilog logic relies on a timed clock signal to function correctly.

### 3) The testwire pin can be useful when debugging timing or signal logic, helping to ensure the FPGA is functioning as expected.

### 4) These mappings were confirmed using the VSDSquadron FPGA Mini Board Datasheet.


</details>

### PCF File (VSDSquadronFM.pcf):
<details>
<summary>
Expand or Collapse
  </summary>

    set_io  led_red	39
    set_io  led_blue 40
    set_io  led_green 41
    set_io  hw_clk 20
    set_io  testwire 17

### This is the pcf file in the github repo given by you.

### Link of the pcf file:
https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_white/VSDSquadronFM.pcf


 </details>
 </details>
 

  
  
  
### Step 3: Setting Up the FPGA Mini Board:
<details>
  <summary>
Expand or Collapse
  </summary>
  </summary>



### Things you need:
<details>
<summary>
Expand or Collapse
  </summary>

### 1) A USB-C cable connected to the FPGA board to your computer as in the figure below.

![Image](https://github.com/user-attachments/assets/9c39ec69-5831-4b7f-9d69-e550af7a8e97)

### 2) FTDI drivers installed to make sure the board is recognized.

### 3) The required development tools (as mentioned in the datasheet).

</details>

### Steps to make the rgb led make blink:
<details>
<summary>
Expand or Collapse
  </summary>
  
### Step 1: Open terminal in virtual box:
After opening the terminal this screen will be shown:

photo of opening terminal


### Step 2: Change to the home directory (‘cd‘):

Write the code below in the terminal to change it to home directory:

    cd
    cd VSDSquadron_FM
    cd blink_led
    
The commands above allow you to:
a) Change to the home directory (‘cd‘).
b) Navigate to the ‘VSDSquadron FM‘ folder, which has a sample project.
c) Move into the ‘blink led‘ directory, which is the first FPGA project to be tried on VSDSquadron FPGA Mini (FM) board.

After writing the following commands this screen will appear:

photo of these commands

### Step 3: Making sure that the board is connected to the computer:


1) There is a preloaded project in ”blink led” directory. To test the project on VSDSquadron
 FPGA Mini (FM) board, we need to make sure that the board is connected to the Oracle
Virtual Machine. Perform below steps:
   
a) Connect the board to your PC, as shown earlier.

b) On the Virtual Machine, click on "Devices → USB → FTDI Single RS232-HS [J900]" as
shown in the picture below.

photo of devices of usb

### Step 3: Confirming that the board is connected to the computer:


1) To confirm if the board is connected to the USB, type the ‘lsusb‘ command in the terminal.
2) You should see a line stating ”Future Technology Devices International,” as shown in the picture below.

photo of lsusb



 ### Step 4: programming the VSDSquadron FPGA Mini (FM) board:

To program the VSDSquadron FPGA Mini (FM) board, follow these steps:

1) Run the following command to clean up previous builds:
    

       make clean  # clears any old build
   

After writing this in terminal the screen will appear like the picture below.

photo of make clean

2) Build the binaries for the FPGA board using below command the picture below shows the output
screen after ‘make build‘ command:

       make build   # compiles the design

photo of make build


3) Flash the code to the external SRAM with the following command:
   
       sudo make flash  # Uploads the code to your FPGA
   
 After executing the above command, the screen will look as shown in the picture below.

photo of sudo make flash

</details>

### What you should see after executing the code:
<details>
<summary>
Expand or Collapse
  </summary>

### 1) The RGB LED should start blinking or changing colors based on your Verilog code.
    
### 2) If nothing happens, check your connections, power supply, and pin assignments.

### 3) The board would look like the pictures below after successfully executing the code.

### Red Led blinking:

   ![Image](https://github.com/user-attachments/assets/381f0b36-c495-40c3-ab7d-68faca58e13b) 

### Blue Led blinking:
   ![Image](https://github.com/user-attachments/assets/416a4ca5-19ab-4d2a-8bd2-90200d6355b4) 

### Green Led blinking:
  ![Image](https://github.com/user-attachments/assets/f67d1fdd-d7db-48fe-8772-654d6235223a)

### No Led blinking:
  ![Image](https://github.com/user-attachments/assets/dda59a7a-1e0f-4f4b-8d76-b615e940a48c)
  
 </details>
 </details>
 

  
  
  
### Step 4: Final notes and troubleshooting:
<details>
  <summary>
Expand or Collapse
  </summary>
  </summary>

  ### Quick recap:
<details>
<summary>
Expand or Collapse
  </summary>

### 1) The Verilog code controls the LED using a built-in clock.

### 2) The PCF file assigns signals to the right FPGA pins.

### 3) The Makeclean, Makebuild, Sudo make flash helps compile and upload the design.

     make clean   # Clears any old builds
     make build   # Compiles the design
     sudo make flash   # Uploads the code to your FPGA

   </details>

### Common issuses and how to resolve the issue:
<details>
<summary>
Expand or Collapse
  </summary>

### 1) Board not detected:
### Make sure the USB cable is connected and FTDI drivers are installed.


### 2) LED not lighting up:
### Double-check the pin assignments in the PCF file.

### 3) Compilation errors:
### Ensure all required tools are installed.

