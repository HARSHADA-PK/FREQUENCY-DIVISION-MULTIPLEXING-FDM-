## FREQUENCY-DIVISION-MULTIPLEXING-FDM

## AIM:

To simulate Frequency Division Multiplexing (FDM) using Scilab and observe the multiplexing and demultiplexing of multiple message signals transmitted over different carrier frequencies.

## APPARATUS REQUIRED

A computer system

Scilab (Latest stable version)

Signal Processing Toolbox (inbuilt functions)

## THEORY:

Frequency Division Multiplexing is a technique in which multiple message signals are transmitted simultaneously over a communication channel by allocating different carrier frequencies to each signal. Each signal modulates its own carrier → modulated signals are added → transmitted together → separated at the receiver using band-pass filters or carrier synchronization.

## ALGORITHM:

Start Scilab.

Define simulation parameters:

Time vector

Carrier frequencies

Amplitude values

Generate two or more message signals (e.g., sine waves).

Generate carrier signals corresponding to each message.

Modulate each message using

## CODE:
```
Fs = 50000;
t = 0:1/Fs:0.02;

m1 = 1.4 * sin(2*%pi*450*t);
m2 = 1.8 * sin(2*%pi*550*t);
m3 = 2.2 * sin(2*%pi*650*t);
m4 = 2.6 * sin(2*%pi*750*t);
m5 = 3.0 * sin(2*%pi*850*t);
m6 = 3.4 * sin(2*%pi*950*t);

c1 = 4000; 
c2 = 8000; 
c3 = 12000; 
c4 = 1600; 
c5 = 20000; 
c6 = 24000;

carrier1 = cos(2*%pi*c1*t);
carrier2 = cos(2*%pi*c2*t);
carrier3 = cos(2*%pi*c3*t);
carrier4 = cos(2*%pi*c4*t);
carrier5 = cos(2*%pi*c5*t);
carrier6 = cos(2*%pi*c6*t);

s1 = m1 .* carrier1;
s2 = m2 .* carrier2;
s3 = m3 .* carrier3;
s4 = m4 .* carrier4;
s5 = m5 .* carrier5;
s6 = m6 .* carrier6;

s_total = s1 + s2 + s3 + s4 + s5 + s6;

r1 = s_total .* carrier1;
r2 = s_total .* carrier2;
r3 = s_total .* carrier3;
r4 = s_total .* carrier4;
r5 = s_total .* carrier5;
r6 = s_total .* carrier6;

function y = ideal_lowpass_fft(x, Fs, fc)
    N = length(x);
    X = fft(x);
    f = Fs*(0:N-1)/N;
    mask = (f <= fc) | (f >= Fs-fc);
    Y = X .* mask;
    y = real(ifft(Y));
endfunction

fc = 1000; 

dm1 = ideal_lowpass_fft(r1, Fs, fc);
dm2 = ideal_lowpass_fft(r2, Fs, fc);
dm3 = ideal_lowpass_fft(r3, Fs, fc);
dm4 = ideal_lowpass_fft(r4, Fs, fc);
dm5 = ideal_lowpass_fft(r5, Fs, fc);
dm6 = ideal_lowpass_fft(r6, Fs, fc);

figure(1);
subplot(3,2,1); plot(t,m1); title("Message Signal 1");
subplot(3,2,2); plot(t,m2); title("Message Signal 2");
subplot(3,2,3); plot(t,m3); title("Message Signal 3");
subplot(3,2,4); plot(t,m4); title("Message Signal 4");
subplot(3,2,5); plot(t,m5); title("Message Signal 5");
subplot(3,2,6); plot(t,m6); title("Message Signal 6");

figure(2);
plot(t, s_total); title("Multiplexed FDM Signal");
figure(3);

subplot(3,2,1); plot(t,dm1); title("Recovered Signal 1");
subplot(3,2,2); plot(t,dm2); title("Recovered Signal 2");
subplot(3,2,3); plot(t,dm3); title("Recovered Signal 3");
subplot(3,2,4); plot(t,dm4); title("Recovered Signal 4");
subplot(3,2,5); plot(t,dm5); title("Recovered Signal 5");
subplot(3,2,6); plot(t,dm6); title("Recovered Signal 6");

```

## OUTPUT:

<img width="752" height="661" alt="image" src="https://github.com/user-attachments/assets/3700ce27-1ead-49ef-82d8-fcd0bb9534ab" />

<img width="773" height="663" alt="image" src="https://github.com/user-attachments/assets/708e071a-489c-498e-9554-d60fca855d2c" />

<img width="761" height="658" alt="image" src="https://github.com/user-attachments/assets/9898cd27-940e-4bbb-8e2e-939b9dc7cb99" />

## TABULATION:

![WhatsApp Image 2025-11-29 at 07 34 19_c471debb](https://github.com/user-attachments/assets/99c78200-9047-4757-bc2b-02b6dcfb74dc)

![WhatsApp Image 2025-11-29 at 07 34 20_11414380](https://github.com/user-attachments/assets/1677c796-c2f3-48ce-83cb-92f4f04b0dd6)

![WhatsApp Image 2025-11-29 at 07 34 21_db07db1c](https://github.com/user-attachments/assets/d2d22170-c182-42d5-98d4-86d129fb8508)




## RESULT:

Frequency Division Multiplexing (FDM) using Scilab and observe the multiplexing and demultiplexing of multiple message signals transmitted over different carrier frequencies is stimulated.

