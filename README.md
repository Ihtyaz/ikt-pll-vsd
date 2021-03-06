# On-Chip-Clock-Multiplier (PLL) using OSU 180nm PDK  | VSD
This particular project is enodorsed and faciliated by VSD, and emphasizes on the design of an 'On-Chip-Clock-Multiplier' using PLL with library OSU 180nm PDK. It comes as part of a 24-hour long tutorial/workshop initiated on 19th October, 2021.



### I. Introduction 

* Intellectual Property (IP): Pre-defined logical cells that are not built from scratch but are rather bought from IP vendors so that they can be used directly on a chip/core. RAM and ROM are few examples of IPs. This helps to reduce design and testing time significantly.

* On-Chip Clock Multiplier: Amplifies incoming low frequency clock signal into a high freqeuncy clock signal, in order to improve performance. This is especially required by processors that demand high frequency clock signals.

<p align="center">
  <img width="681" height="287" src="https://i.imgur.com/p6963Zc.png">
</p>

<p align="center">
    Figure: Implementation of On-Chip Clock Multiplier using PLL
</p>

* Processors come in two types - Synchronous and Asynchronous; those that require a clock signal are categorized as synchronouse and those that don't are categorized as asynchronous.


* Phase Locked Loop: A circuit construction/block used to implement the concept of Clock Multiplier. It constitutes of the following blocks - Phase Detector, Low-Pass Filter, Voltage Control Oscillator and Frequency Divider (N Counter). 

<p align="center">
  <img width="650" height="270" src="https://i.imgur.com/KwwaCMt.png">
</p>
<p align="center">
    Figure: Generic block diagram of a typical PLL
</p>


* Feedback Loop: PLL employs the implementation of a feedback loop, whose operation is similar to that of in control system, in order to ensure desired frequency is attained. A feedback loop is one where the output of a particular circuit block is fed back to the input in order to determine the degree of error and correct it accordingly based on the requirements. A characteristic equation is derived from the transfer function in order to better understand the behavior of the circuit block. In the design of a PLL, it is most preferable to ensure the design of a critically damped system.

### II. Pre-layout Implementation & Simulation

* The PLL has been designed using pre-installed open-source EDA tools provisioned by VSD's custom platform. Process used is 180nm

<p align="center">
  <img width="681" height="287" src="https://i.imgur.com/sKSmgNe.png">
</p>
<p align="center">
    Figure: Architectural block diagram of a typical PLL
</p>

* eSim application is generally employed in order to generate netlist representation of different gates or circuit components. Subsequently, ngspice can be used to simulate the input and output waveforms of the circuit or gate under observation.

* General Design Flow | Chip Design Specifications - Architectural Design - Logic Synthesis - Simulation - Architectural Design - .. (Optimization Loop)

#### A. Phase Frequency Detector - Evaluates difference in frequency between two signals
<p align="center">
  <img width="750" height="460" src="https://i.imgur.com/VzhdR0O.png">
</p>
<p align="center">
    Figure: Gate-Level Circuit Diagram of a Phase Frequency Detector                                                

 
#### B. Charge Pump - Acts as a supply of additional charge
<p align="center">
  <img width="750" height="480" src="https://i.imgur.com/UfzJY7R.png">
</p>
<p align="center">
    Figure: Schematic Circuit Diagram of a Charge Pump
</p>


#### C. Voltage Controller Oscillator - Used to control degree of oscillation based on voltage
<p align="center">
  <img width="780" height="380" src="https://i.imgur.com/vKU1wdR.png">
</p>
<p align="center">
    Figure: Gate-Level Circuit Diagram of a Charge Pump
</p>


#### D. Frequency Divider - Used to enhance or degrade frequency of the output signal
<p align="center">
  <img width="700" height="490" src="https://i.imgur.com/PMVvg73.png">
</p>
<p align="center">
    Figure: Schematic Circuit Diagram of a Charge Pump
</p>


#### E. Phase Locked Loop
<p align="center">
  <img width="700" height="490" src="https://i.imgur.com/PMVvg73.png">
</p>
<p align="center">
    Figure: Schematic Circuit Diagram of a Charge Pump
</p>



### II. Physical Design & Post-layout

* Standard Flow | Floorplanning - Placement - Routing - Circuit Extraction 

#### A. CMOS Inverter Layout
<p align="center">
  <img width="138" height="488" src="https://i.imgur.com/X7ifKLT.png">
</p>
<p align="center">
    Figure: Layout Diagram of an Inverter
</p>



<p align="center">
  <img width="988" height="336" src="https://i.imgur.com/6JEHYu8.png">
</p>
<p align="center">
    Figure: Execution of commands on Magic
</p>


<p align="center">
  <img width="651" height="517" src="https://i.imgur.com/26gEi4v.png">
</p>
<p align="center">
    Figure: Generated Netlist of Inverter Layout from Magic
</p>



#### B. Phase Frequency Detector Layout
<p align="center">
  <img width="479" height="728" src="https://i.imgur.com/bFQjcLi.png">
</p>
<p align="center">
    Figure: Layout Diagram of Phase Detector
</p>



<p align="center">
  <img width="762" height="844" src="https://i.imgur.com/EcUrtnQ.png">
</p>
<p align="center">
    Figure: Modified Netlist of Phase Detector - 1
</p>


<p align="center">
  <img width="980" height="915" src="https://i.imgur.com/8MRBgmo.png">
</p>
<p align="center">
    Figure: Generated Netlist of Phase Detector - 2
</p>


<p align="center">
  <img width="1793" height="808" src="https://i.imgur.com/FzIsumQ.png">
</p>
<p align="center">
    Figure: Simulated Output of Phase Detector
</p>



#### C. VCO Layout
<p align="center">
  <img width="1181" height="565" src="https://i.imgur.com/NBDn1rV.png">
</p>
<p align="center">
    Figure: Layout Diagram of VCO
</p>



<p align="center">
  <img width="734" height="883" src="https://i.imgur.com/PNCGXzJ.png">
</p>
<p align="center">
    Figure: Modified Netlist of VCO
</p>


<p align="center">
  <img width="728" height="870" src="https://i.imgur.com/vzMOgXn.png">
</p>
<p align="center">
    Figure: Generated Netlist of VCO

  
<p align="center">
  <img width="1817" height="840" src="https://i.imgur.com/faPQwTb.png">
</p>
<p align="center">
    Figure: Simulated output of VCO
  
  
