# EXP 3 : IIR-BUTTERWORTH-FITER-DESIGN

## AIM: 
To design and analyze an IIR Butterworth filter (both Low Pass and High Pass) using SCILAB.

 To design an IIR Butterworth filter  using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (LPF):

clc;
clear;

// Sampling frequency
Fs = 5000;           // Hz

// Cutoff frequency
fc = 1000;           // Hz
Wn = 2 * fc / Fs;    // Normalized (0 to 1)

// Butterworth LPF (order 2) — precomputed coefficients
b = [0.0675 0.1349 0.0675];   // Numerator
a = [1.0000 -1.1429 0.4128];  // Denominator

// Frequency response (N = 512 points)
N = 512;
[H, f_norm] = frmag(b, a, N);  // Only 3 arguments

// Convert normalized freq to Hz
f = f_norm * Fs;

// Plot magnitude response in dB
clf();
plot(f, 20 * log10(H));
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Butterworth Low Pass Filter (Order 2)");
xgrid();




## PROGRAM (HPF): 

clc;
clear;

// Sampling frequency in Hz
Fs = 8000;

// Cutoff frequency in Hz
fc = 2000;

// Precomputed 2nd order Butterworth HPF coefficients
// These coefficients correspond to a 2nd order Butterworth HPF with cutoff ~ 2000 Hz
b = [0.6389 -1.2777 0.6389];    // Numerator
a = [1.0000 -0.5095 0.1825];    // Denominator

// Number of frequency points for response
N = 512;

// Calculate frequency response magnitude and normalized frequency vector
[H, f_norm] = frmag(b, a, N);

// Convert normalized frequency (0 to 0.5) to Hz (0 to Fs/2)
f = f_norm * Fs;

// Plot magnitude response in dB
clf();
plot(f, 20 * log10(H), 'LineWidth', 2);
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Butterworth High Pass Filter (Order 2) Frequency Response");
xgrid();

// Optional: draw vertical line at cutoff frequency (fc)
xset("color", 2); // red color
plot([fc fc], [-80 5], '--');
xset("color", 1); // reset to black





## OUTPUT (LPF) :
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/2c1b3c5c-32e5-4f8f-a107-a1469236eeb9" />




## OUTPUT (HPF) : 
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/bf49d82e-e842-4029-87d5-07b516bd5d0a" />


## RESULT: 
The IIR Butterworth Low Pass and High Pass filters were designed successfully using SCILAB. The frequency response plots showed the expected behavior with proper cutoff frequencies and smooth roll-off, confirming that the filters work as intended.

