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

<summary>
<summary>

### led_red:
<details>
<summary>
Expand or Collapse
  </summary>
  
### Link of the red led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_red/VSDSquadronFM.pcf
### 1) FPGA pins: 39
### 2) Purpose: Controls the red channel of the RGB LED. The Verilog code sets this pin high or low based on timing logic to turn the red light on or off.

<summary>
<summary>

### led_blue:
<details>
<summary>
Expand or Collapse
  </summary>

### Link of the blue led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_blue/VSDSquadronFM.pcf
 ### 1) FPGA pins: 40
 ### 2) Purpose: Controls the blue channel of the RGB LED. The Verilog module manipulates this pin to create blinking or color effects.

<summary>
<summary>

### led_green:
<details>
<summary>
Expand or Collapse
  </summary>
  
### Link of the green led's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_green/VSDSquadronFM.pcf
 ### 1) FPGA pins: 41
 ### 2) Purpose: Controls the green channel of the RGB LED. It works in conjunction with the other two LED pins to mix colors.


<summary>
<summary>

### hw_clk:
<details>
<summary>
Expand or Collapse
  </summary>
  
 ### Link of the hw_clk's pcf file:
https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_white/VSDSquadronFM.pcf
  
 ### 1) FPGA pins: 20
 ### 2) Purpose: Receives the clock signal from the onboard oscillator. This signal is crucial for the counter logic in Verilog, which determines LED blinking speed.

<summary>
<summary>

### testwire:
<details>
<summary>
Expand or Collapse
  </summary>
  
  ### Link of the testwire's pcf file:
   https://github.com/thesourcerer8/VSDSquadron_FM/blob/main/led_white/VSDSquadronFM.pcf
 ### 1) FPGA pins: 17
 ### 2) Purpose: This is an auxiliary output that can be used for debugging. It can carry signals that help monitor internal operations.
 
 </details>

### Pin Mapping and Significance:
<details>
<summary>
Expand or Collapse
  </summary>
  
### 1) The LED signals must be assigned correctly to their respective FPGA pins so that they physically control the onboard RGB LED.

### 2) The hw_clk input is essential because the Verilog logic relies on a timed clock signal to function correctly.

### 3) The testwire pin can be useful when debugging timing or signal logic, helping to ensure the FPGA is functioning as expected.

### 4) These mappings were confirmed using the VSDSquadron FPGA Mini Board Datasheet.

 
