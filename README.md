# PLL-Design-using-SKY130

# Introduction

![PLL-Workshop-Banner_efabless](https://user-images.githubusercontent.com/22279620/127746035-1e97e877-5d3e-4bbd-a08c-e5131de5c384.png)

This 2 day tapeout workshop on Phase-Locked Loop(PLL) IC design using Open-Source Google-Skywater 130nm involved designing
a simple PLL using open source tools. This two day workshop was conducted from July 31st - August 1st 2021 by Mr Kunal Gosh, co-founder
of VLSI System Design (VSD) Corp. Pvt. Ltd and Lakshmi Sathidevi.

The labs covered the entire IC design flow from circuit design until tapeout using Open-Source 130nm Process Design Kits(PDK) by Google-Skywater and the latest Caravel Framework by efabless. Open-Source EDA tools such as ngSpice and Magic were used throughout th design flow.

# Day 1

![snip2](https://user-images.githubusercontent.com/22279620/127747417-d6453d93-e0ea-432d-a3bd-f8a44e7c651f.PNG)


The first day of the workshop was a theoretical introduction to various concepts related to PLL and how it is used to get a precise noise signal without noise. Quartz Crystals and Voltage Controlled Oscillator were discussed briefly. The various components that make up the PLL such as the Phase Frequency Detector(PFD), Charge Pump(CP), Voltage Controlled Oscillator(VCO) and Frequency Divider(FD) were talked about in depth in terms of timing waveforms, CMOS and digital circuits and Finite State Machines(FSM). Design Flow, PDK, speciifcation and Open-Source EDA tool setup were briefly touched upon as well.

# Day 2

## PLL Component circuit design

![snip2](https://user-images.githubusercontent.com/22279620/127750060-b4499998-3560-464a-8b3d-47229c796a76.PNG)


Create file FreqDiv.cir that would hold the entire frequency division circuit

![snip2](https://user-images.githubusercontent.com/22279620/127750090-0edec457-a7f0-4e9d-8c48-104ca70527bf.PNG)

The circuit file defines three instances of an inverter and two instances of transmission gates.


![snip2](https://user-images.githubusercontent.com/22279620/127750153-837ea5ea-b3e2-469a-85fc-45bb84ec36b3.PNG)

## PLL Component circuit simulation

Run the simulation of the circuit using Ngspice and obtain the transient analysis plot. The plot verifies that the frequency divider circuit works as intended.

![snip2](https://user-images.githubusercontent.com/22279620/127750356-16d87549-3295-414c-8913-33c0f597b550.PNG)


Similarly, the control pump circuit design file is simulated and the transient analysis plot is obtained. 

![snip2](https://user-images.githubusercontent.com/22279620/127750496-0145d978-784f-4cdc-9ce2-6ea3a821920b.PNG)

VCO design is also simulated to obtain the transient analysis plot

![snip2](https://user-images.githubusercontent.com/22279620/127750569-8cd4e54b-1591-4ec6-a2f0-40ff99e206e3.PNG)


## Combine PLL sub circuits and simulate full design

All the sub modules of the PLL are combined and defined in the file PLL_PreLay.cir and the simulate the entire control loop







