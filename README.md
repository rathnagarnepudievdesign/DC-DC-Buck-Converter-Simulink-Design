# DC-DC-Buck-Converter-Simulink-Design
MATLAB/Simulink based DC-DC Buck Converter design for Electric Vehicle auxiliary applications with PWM control and ripple analysis.
Project Description

This project involves the design and simulation of a DC-DC Buck Converter (Step-Down Converter) using MATLAB/Simulink. The model is designed to convert a higher DC input voltage to a lower, regulated DC output voltage. It utilizes the ode23t solver and is optimized for high-precision power electronics simulation with a maximum time step of 1micro second



The system is modeled in MATLAB/Simulink to analyze:
Output voltage regulation
Inductor current ripple
Duty cycle variation
Switching behavior
Converter efficiency
  


Given Parameters

Input Voltage (vin) = 24 V
Inductor 𝐿 = 3 mH = 0.003 H
Capacitor C = 200 µF = 200 × 10⁻⁶ F
Load Resistance R = 10 Ω
PI Controller Gains: Kp=4;
                     Ki=0.01;
Main Components & Function
1️⃣ MOSFET Switch

Acts as a high-speed switching element controlled by PWM signal.

2️⃣ Diode

Provides freewheeling path for inductor current during OFF state.

3️⃣ Inductor (L)

Stores energy during ON time and releases during OFF time.
Controls current ripple.

4️⃣ Capacitor (C)

Filters output voltage ripple and stabilizes DC output.

5️⃣ Load Resistance
Represents EV low-voltage load (ECU, lighting, control modules).

Voltage Transfer Function

The relationship between the Input Voltage (vin) and Output Voltage (vout) is determined by the Duty Cycle

V_out = D * V_in
Where 0 < D < 1.

Duty Cycle Calculation

For Buck Converter:

D=Vin/Vout;
D=24/12=0.5
Duty Cycle = 50%

	Output Current
  Iout=R/Vout;
  Iout=10/12=1.2A;
  Output Current = 1.2 A
  
  Inductor Ripple Current
  
Ripple current formula:
ΔIL=(Vin−Vout)⋅D/L.fs
We must assume switching frequency.
Let’s assume:
fs=20kHz
ΔIL=(24−12)⋅0.50/0.003⋅20000
ΔIL=6/60
ΔIL=0.1A
Inductor Ripple Current = 0.1 A

Inductor Current Range

IL(max)=Iout+ΔIL2
IL(max)=1.2+0.05=1.25A
 IL(min)=1.2−0.05=1.15 
 Continuous Conduction Mode (CCM confirmed)
 
 Output Voltage Ripple
 
ΔVo=ΔIL/8fsC
ΔVo=0.1/8⋅20000⋅200×10−6
=0.1/32
ΔVo=0.003125V 
Output Ripple ≈ 3.1 mV
Very low ripple → good capacitor selection.


Critical Inductance (Boundary Mode)
Lcritical=(1−D)R/2fs
 Lcritical=(1−0.5)⋅10/2⋅20000)
5/40000 
Lcritical=125μH 
Your L = 3 mH (3000 µH)
Much higher than critical → Deep CCM


PI Controller Transfer Function
PI Controller:
G(s)=Kp+Ki/s
G(s)=0.1+4/s 
This controller:
•	Kp → Improves response speed
•	Ki → Eliminates steady-state error
Integral time constant:
Ti=Kp/Ki
Ti =0.1/4=0.25s

Parameter	Value
Duty Cycle	0.5
Output Current	1.2 A
Inductor Ripple	0.1 A
Voltage Ripple	3.1 mV
Critical Inductance	125 µH
Operating Mode	CCM
Controller	PI (0.1 + 4/s)

Tools Used

• MATLAB  
• Simulink  
• Simscape Electrical

Simulation Result:

• Output voltage waveform verified  
• Inductor current ripple analyzed  
• Stable steady-state response observed 
• Stable steady-state response observed

Application
Suitable for EV auxiliary DC power systems.
 DC-DC Buck Converter for EV Application




​​​

	​
