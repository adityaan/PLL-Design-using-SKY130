# PLL-Design-using-SKY130 PDK

# Table of Contents

- [Introduction](#introduction)
- [Day 1 - PLL Overview](#day1)
- [Day 2 - Project Labs](#day2)
  - [PLL Component Circuit Design](#design)
  - [PLL Component Circuit Simulation](#simulation)
  - [Combine PLL Sub Circuits and Simulate Full Design](#combine)
  - [PLL Circuit Layout using Magic](#layout)
  - [Parasitics Extraction](#parasitic)
  - [Post Layout Simulation](#postlayout)
  - [Tapeout using Caravel SoC](#tapeout)
- [Acknowledgements](#ack)

# Introduction <a name="introduction"></a>

![PLL-Workshop-Banner_efabless](https://user-images.githubusercontent.com/22279620/127746035-1e97e877-5d3e-4bbd-a08c-e5131de5c384.png)

This 2 day tapeout workshop on Phase-Locked Loop(PLL) IC design using Open-Source Google-Skywater 130nm involved designing
a simple PLL using open source tools. This two day workshop was conducted from July 31st - August 1st 2021 by Mr Kunal Gosh, co-founder
of VLSI System Design (VSD) Corp. Pvt. Ltd and Lakshmi Sathidevi.

The labs covered the entire IC design flow from circuit design until tapeout using Open-Source 130nm Process Design Kits(PDK) by Google-Skywater and the latest Caravel Framework by efabless. Open-Source EDA tools such as ngSpice and Magic were used throughout th design flow.

# Day 1 - PLL Overview <a name="day1"></a>

![snip2](https://user-images.githubusercontent.com/22279620/127747417-d6453d93-e0ea-432d-a3bd-f8a44e7c651f.PNG)


The first day of the workshop was a theoretical introduction to various concepts related to PLL and how it is used to get a precise noise signal without noise. Quartz Crystals and Voltage Controlled Oscillator were discussed briefly. The various components that make up the PLL such as the Phase Frequency Detector(PFD), Charge Pump(CP), Voltage Controlled Oscillator(VCO) and Frequency Divider(FD) were talked about in depth in terms of timing waveforms, CMOS and digital circuits and Finite State Machines(FSM). Design Flow, PDK, speciifcation and Open-Source EDA tool setup were briefly touched upon as well.

# Day 2 - Project Labs <a name="day2"></a>

## PLL Component circuit design <a name="design"></a>

During this stage, we designed the frequency divider module as discussed during Day 1. We designed the gate level circuit which contains inverters and transmission gates connected together. These gates are designed by specifying their p-type and n-type FET specification along with their length and width specifications. 

![snip2](https://user-images.githubusercontent.com/22279620/127750060-b4499998-3560-464a-8b3d-47229c796a76.PNG)


The FreDiv.cir circuit is created to define the specifications of the circuit. The file also includes the SKY130nm library file and also constraints to plot the transient analysis.

![snip2](https://user-images.githubusercontent.com/22279620/127766001-df6ab13b-79b3-4d07-bc8e-93c9dea59f27.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127750153-837ea5ea-b3e2-469a-85fc-45bb84ec36b3.PNG)

Similarly, the other sub modules for the PLL circuit is defined using the specifications.

## PLL Component Circuit Simulation <a name="simulation"></a>

After designing the circuits, all the sub modules are simulated using Ngspice along with the transient analysis plots. The simulations are carried out to verify the functionality before moving to the Layout stage of the project.

![snip2](https://user-images.githubusercontent.com/22279620/127766176-89421591-03fc-47e8-b5c6-68cd1f6173cb.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127766219-3586040b-ea68-433b-8b9c-29b9c53dbe82.PNG)


Similarly, the control pump circuit design file is simulated and the transient analysis plot is obtained. 

![snip2](https://user-images.githubusercontent.com/22279620/127766302-c8f37fda-4060-4854-9a78-43b0eed95a68.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127766323-86a4935d-6f49-4925-9c3d-636eae14bb6c.PNG)

PD design is simulated to obtain the transient analysis plot

![snip2](https://user-images.githubusercontent.com/22279620/127766421-7a231fe9-2d71-43d8-a711-373b7dab5e40.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127766447-1a4d6e0d-613b-4171-8811-75dae80eefdf.PNG)


VCO design is also simulated to obtain the transient analysis plot

![snip2](https://user-images.githubusercontent.com/22279620/127766503-968090a8-a254-4b0c-a1ed-ee0da590df81.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127766519-d202f00d-688f-455f-87b4-ca87a5ec5d26.PNG)

All the PLL sub modules and their transient plots were as expected.


## Combine PLL Sub Circuits and Simulate Full Design <a name="combine"></a>

All the sub modules of the PLL are combined and defined in the file PLL_PreLay.cir and the simulate the entire control loop


![snip2](https://user-images.githubusercontent.com/22279620/127767962-efd0c3ec-3ec6-42ca-8407-4424defb8bf9.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127767982-92ef59b0-ab66-4669-8aa1-fa20243aab79.PNG)

## PLL Circuit Layout using Magic <a name="layout"></a>

During this stage, we design the layouts for each sub module using Magic. This is done by creating gates, NMOS and PMOS regions, creating the VDD and VSS by placcing the appropriate metal layers and connecting the layers using local interconnects. Also, vias would also be used to connect the metal layers. Most importantly, at the end of this stage, the priority is to make sure that the layed out design is free of Design Rule Check(DRC) errors so as to get a circuit the functions correctly.

![snip2](https://user-images.githubusercontent.com/22279620/127768242-5e7c8a06-d7d9-4760-9cbb-c7cc341ae28b.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768266-b0cfcc19-3469-411b-a43d-7fdda7f33023.PNG)

Then, the layout for the control pump was designed

![snip2](https://user-images.githubusercontent.com/22279620/127768337-841b24fd-4418-4d3e-866a-c440c7f2a38d.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768362-7c043eed-d43b-4817-a231-dc12d6c11f59.PNG)

The layout for the MUX was designed after the control pump

![snip2](https://user-images.githubusercontent.com/22279620/127768408-aec351cd-1092-4ced-bc20-bef17cc4c6ce.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768422-f8d7c762-edb6-40bd-94c9-d4da75d4122d.PNG)

After the MUX, the layout for the PFD was created

![snip2](https://user-images.githubusercontent.com/22279620/127768482-93e82472-9c62-45a0-bdca-ff2719259144.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768498-df2c5654-a2fd-44b7-854f-38c064c96a77.PNG)

The layout for the VCO was the last sub module to be designed before putting the entire PLL layout together.

![snip2](https://user-images.githubusercontent.com/22279620/127768531-8e0363b6-8dd8-4537-9fdd-c8f1271bea08.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768554-0327355e-5ab4-4097-b911-a9e8edf95995.PNG)

Finally, the entire PLL layout was designed using the various sub modules layouts designed earlier

![snip2](https://user-images.githubusercontent.com/22279620/127768614-3ba6a68a-2939-48de-9f92-7043a44b58d8.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127768636-137a8790-b9cc-4f11-b47f-13ca16b76b19.PNG)

All the above designs are free of DRC errors. In the next stage, we would be using the design from this stage for parasitic extraction.

## Parasitics Extraction <a name="parasitic">

During this stage, the design is used for parasitic extraction. This is done to make sure that the various capacitance values are being extracted so as to simulate
the precise delay values during the post layout simulation stage.

![snip2](https://user-images.githubusercontent.com/22279620/127769168-fdd87b6f-42db-40e3-9327-6ccd34089499.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127769185-b71a0a4b-4170-4d5b-af6a-4c4ad3337c18.PNG)

The extracted parasitic file consists of multiple capacitance values.

![snip2](https://user-images.githubusercontent.com/22279620/127769266-1abd90ab-5144-47c6-bace-ef535823eb6e.PNG)

## Post Layout Simulation <a name="postlayout">
  
This stage is being caaried out to simulate the PLL design post layout along with the extracted parasitic value. This would be the last simulation of the design to
verify it's functionality and to make sure that it meets all the design constraints before tapeout.

![snip2](https://user-images.githubusercontent.com/22279620/127769401-55cce147-33e3-4417-9f5f-517435661160.PNG)

![snip2](https://user-images.githubusercontent.com/22279620/127769427-e6305800-f28d-44b2-a918-3e41d2c9a81e.PNG)

Comparing the transient file output with what is being expected, the circuit works as intended. The next step is to prepare the design for tapeout.

## Tapeout using Caravel SoC <a name="tapeout"></a>
  
 ![snip2](https://user-images.githubusercontent.com/22279620/127870858-12988d03-a1c8-419f-bf18-0f14e4f4202b.PNG)
  
During this final stage, we would be coonecting the PLL designed to the Caravel SoC for tapeout. The final PLL design would be in GDSII format and can be imported into the 
SoC architecture. For more information about Caravel SoC and how to integrate designs, please check this [link.](https://github.com/efabless/caravel). The analog user project wrapper is downloaded from the efabless Github repo. The extracted GDS file is used to place the layout of the PLL design. The GDS file contains IO and power pins such as VDD and VSS on it's sides.

![snip2](https://user-images.githubusercontent.com/22279620/127773851-e58a8a65-9bc6-4cb9-ab0c-a411aabf7a2d.PNG)

# Acknowledgements <a name="ack"></a>

- [Kunal Gosh - Co-Founder at VLSI System Design](https://github.com/kunalg123)
- [Lakshmi Sathi](https://github.com/lakshmi-sathi)










