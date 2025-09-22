# EXP 3 : IIR-CHEBYSHEV-FITER-DESIGN

## AIM: 

 To design an IIR Chebyshev filter  using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (LPF): 
clc;
clear;

// ------------------------------
// Filter specifications
// ------------------------------
Fs = 5000;       // Sampling frequency (Hz)
fc = 1500;       // Cutoff frequency (Hz)
n  = 4;          // Filter order
Rp = 1;          // Passband ripple (dB)

// ------------------------------
// Normalized cutoff (0–1) for manual coefficients
Wn = fc / Fs;

// ------------------------------
// Digital Chebyshev Type I coefficients (pre-computed for n=4, Rp=1dB)
b = [0.0976  0.3904  0.5856  0.3904  0.0976];  // numerator
a = [1.0000 -0.5772  0.4218 -0.0562  0.0097];  // denominator

// ------------------------------
// Frequency response
N = 512;
[H, f_norm] = frmag(b, a, N);
f = f_norm * Fs;

// ------------------------------
// Plot magnitude response
figure(1);
plot(f, 20*log10(H + %eps));
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Chebyshev Type I Low-Pass Filter (Order 4, Rp=1dB)");
xgrid();

// ------------------------------
// Plot phase response
phase = atan2(imag(H), real(H)) * 180 / %pi;
figure(2);
plot(f, phase);
xlabel("Frequency (Hz)");
ylabel("Phase (degrees)");
title("Phase Response of Chebyshev Type I LPF");
xgrid();


## PROGRAM (HPF): 
clc;
clear;

// ------------------------------
// Filter specifications
// ------------------------------
Fs = 5000;       // Sampling frequency (Hz)
fc = 1500;       // Cutoff frequency (Hz)
n  = 2;          // Filter order
Rp = 1;          // Passband ripple (dB)

// ------------------------------
// Normalized cutoff frequency
Wn = fc / Fs;    // Must be 0 < Wn < 0.5

// ------------------------------
// Precomputed Chebyshev Type I HPF coefficients (order 2, Rp=1dB)
b = [0.5856 -1.1712 0.5856];  // Numerator
a = [1.0000 -0.5772 0.4218];  // Denominator

// ------------------------------
// Frequency response
N = 512;
[H, f_norm] = frmag(b, a, N);
f = f_norm * Fs;

// ------------------------------
// Plot magnitude response
figure(1);
plot(f, 20*log10(H + %eps));
xlabel("Frequency (Hz)");
ylabel("Magnitude (dB)");
title("Chebyshev Type I High-Pass Filter (Order 2, Rp=1dB)");
xgrid();

// ------------------------------
// Plot phase response
phase = atan2(imag(H), real(H)) * 180 / %pi;
figure(2);
plot(f, phase);
xlabel("Frequency (Hz)");
ylabel("Phase (degrees)");
title("Phase Response of Chebyshev Type I HPF (Order 2)");
xgrid();


## OUTPUT (LPF) : 
![WhatsApp Image 2025-09-22 at 21 29 08_a26f540a](https://github.com/user-attachments/assets/9ba05001-4c85-4612-82fe-90bca74ce350)

## OUTPUT (HPF) : 
![WhatsApp Image 2025-09-22 at 21 29 25_37ec4535](https://github.com/user-attachments/assets/fbddf537-c6b5-435c-87ea-cf4400998bc5)

## RESULT: 
