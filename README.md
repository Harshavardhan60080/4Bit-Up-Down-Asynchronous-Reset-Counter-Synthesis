Exp-No:4 - 4 Bit Up-Down Counter Asynchronous Reset Counter-Synthesize the Gate Level Netlist and tabulate Area, Power and Timing reports.


Aim:

  Synthesize 4Bit-Up-Down-Asynchronous-Reset-Counter design using Constraints and analyse reports, Timing, area and Power.

Tool Required:

  Functional Simulation: Incisive Simulator (ncvlog, ncelab, ncsim)

  Synthesis: Genus

Step 1: Getting Started

  Synthesis requires three files as follows,

    ◦ Liberty Files (.lib)

    ◦ Verilog/VHDL Files (.v or .vhdl or .vhd)

    ◦ SDC (Synopsis Design Constraint) File (.sdc)

Step 2 : Creating an SDC File

  • In your terminal type “gedit input_constraints.sdc” to create an SDC File if you do not have one.

  • The SDC File must contain the following commands;

    create_clock -name clk -period 2 -waveform {0 1} [get_ports "clk"]

    set_clock_transition -rise 0.1 [get_clocks "clk"]

    set_clock_transition -fall 0.1 [get_clocks "clk"]

    set_clock_uncertainty 0.01 [get_ports "clk"]

    set_input_delay -max 0.8 [get_ports "rst"] -clock [get_clocks "clk"]

    set_output_delay -max 0.8 [get_ports "count"] -clock [get_clocks "clk"]

    i→ Creates a Clock named “clk” with Time Period 2ns and On Time from t=0 to t=1.

    ii, iii → Sets Clock Rise and Fall time to 100ps.

    iv → Sets Clock Uncertainty to 10ps.

    v, vi → Sets the maximum limit for I/O port delay to 1ps.

Step 3 : Performing Synthesis

  The Liberty files are present in the library path,

    • The Available technology nodes are 180nm ,90nm and 45nm.

    • In the terminal, initialise the tools with the following commands if a new terminal is being used.

    ◦ csh

    ◦ source /cadence/install/cshrc

    • The tool used for Synthesis is “Genus”. Hence, type “genus -gui” to open the tool.

    • Genus Script file with .tcl file Extension commands are executed one by one to synthesize the netlist.


Synthesis RTL Schematic:


![4_op 1](https://github.com/user-attachments/assets/859ed54e-9b70-4f95-89ce-cdf5bd61ef8d)



Area report:


![4_area 1](https://github.com/user-attachments/assets/71b55cc8-4508-45a5-aabd-47dfc8eb51b9)






Power Report:


![4_power 1](https://github.com/user-attachments/assets/5404ffc6-4ac0-4619-b4ee-8630e042a75e)



Timing Report:


![4_time 1](https://github.com/user-attachments/assets/9a1ab76c-d501-423c-8c6e-0aa6c0ce3af1)



Result:

  The generic netlist has been created, and area, power, and timing reports have been tabulated and generated using Genus.


