# EVALUATION-OF-RADAR-RANGE-USING-PYTHON-

## Aim:

To calculate the maximum range of a radar system using the Radar Range Equation and verify the results 
through Python programming.

## Theory:

The Radar Range Equation is a fundamental formula used in radar system design to determine the maximum 
range at which a radar can detect a target. It is given by:

<img width="573" height="442" alt="image" src="https://github.com/user-attachments/assets/ba374d30-d11f-41e5-a4fc-a42dde71d8e7" />

## Procedure:

1. Set Up the Python Environment: Ensure that Python is installed on your system. You can use 
Anaconda for managing Python packages and environments, or any other Python IDE of your choice. 
2. Import Necessary Libraries: Import the math library in Python. 
3. Define the Radar Range Equation Function: Create a function to calculate the maximum range using 
the Radar Range Equation. 
4. Input Parameters for the Radar System: Define the input parameters such as transmitted power, 
transmitter gain, receiver gain, radar frequency, radar cross section, and minimum detectable power. 
5. Calculate the Maximum Range: Use the function to calculate the maximum range of the radar. 
6. Execute the Program: Run the Python script to calculate and display the maximum range of the radar.

## Algorithm:
1.Define all radar parameters such as transmit power, gain, frequency, target RCS, and minimum detectable power.
2.Calculate the wavelength using the formula λ=cf\lambda = \frac{c}{f}λ=fc​.
3.Apply the radar range equation to compute received power at different ranges.
4.Compare the received power with the minimum detectable power.
5.Determine the maximum radar range where the received power is just above the detection threshold.

## Program:
```
import numpy as np
import matplotlib.pyplot as plt

Pt = 10          
Gt = 30          
Gr = 30         
lam = 0.03  
sigma = 5        
L = 1           
R = np.arange(100, 20000, 10)   
Pr = (Pt * Gt * Gr * (lam**2) * sigma) / ((4*np.pi)**3 * (R**4) * L)
plt.subplot(3,1,1)
plt.plot(R, Pr)
plt.title("Received Power vs Range")
plt.xlabel("Range (m)")
plt.ylabel("Pr (W)")
Pr_dB = 10 * np.log10(Pr)
plt.subplot(3,1,2)
plt.plot(R, Pr_dB)
plt.title("Received Power (dB) vs Range")
plt.xlabel("Range (m)")
plt.ylabel("Pr (dB)")
Pr_min = 1e-10    
valid_indices = np.where(Pr > Pr_min)[0]
Rmax = R[valid_indices[-1]]
print("Maximum Detection Range =", Rmax, "meters")
plt.subplot(3,1,3)
plt.plot(R, Pr)
plt.axhline(Pr_min, color='r')
plt.title("Detection Threshold")
plt.xlabel("Range (m)")
plt.ylabel("Received Power (W)")
plt.tight_layout()
plt.show()


```
## Output:
<img width="630" height="469" alt="image" src="https://github.com/user-attachments/assets/767d66a3-0e32-439f-bf0b-774bc765316e" />

## Tabulation:

![WhatsApp Image 2025-11-23 at 16 11 24_350fa348](https://github.com/user-attachments/assets/7e9e520d-2648-40d9-accd-8aca7c6581bd)

## Result:

The Radar Range experiment demonstrates how the received power decreases rapidly as the target distance increases, following the relationship of the radar range equation. The plotted graphs clearly show the received power in both linear and dB scales, helping visualize signal attenuation over distance. By comparing the received power with the minimum detection threshold, the experiment successfully determines the maximum range at which the radar can detect a target. This confirms the effectiveness of the radar range equation in predicting radar performance.
   




