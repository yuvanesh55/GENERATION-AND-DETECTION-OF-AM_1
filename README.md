# GENERATION-AND-DETECTION-OF-AM_1
## AIM:
To generate and detect the amplitude modulation and demodulation u s i n g S C I L A B and to calculate modulation index of AM.

## EQUIPMENTS REQUIRED

•	Computer with i3 Processor

•	SCI LAB

## THEORY:
Modulation can be defined as the process by which the characteristics of carrier wave are varied in accordance with the modulating wave (signal). Modulation is performed in a transmitter by a circuit called a modulator.

Need for modulation is as follows:

•	Avoid mixing of signals

•	Reduction in antenna height

•	long distance communication

•	Multiplexing

•	Improve the quality of reception

•	Ease of radiation.

Amplitude Modulation is the process of changing the amplitude of a relatively high frequency carrier signal in proportion with the instantaneous value of the modulating signal. The output waveform contains all the frequencies that make up the AM signal and is used to transport the information through the system. Therefore the shape of the modulated wave is called the AM envelope. With no modulating signal the output waveform is simply the carrier signal. Coefficient of modulation is a term used to describe the amount of amplitude change present in an AM waveform. There are three degrees of modulation available based on value of modulation index.

1)	Under modulation :	m<1, Em < Ec
	
2)	Critical modulation: m-1, Em = Ec
  
3)	Over modulation:	m>1, Em > Ec

Note: Keep all the switch faults in off position

## ALGORITHM
1.	Define Parameters
   
    First, define the parameters for your signals:
    
    •	Carrier frequency (fc)
    
    •	Modulating signal frequency (fm)
    
    •	Sampling frequency (Fs)
    
    •	Duration of the signal (T)

2.	Create a time vector based on the sampling frequency and duration.
 
3.	Create Modulating Signal:Define the modulating signal (message signal).

4.	Create Carrier Signal:Define the carrier signal.

5.	Perform Amplitude Modulation:Multiply the carrier signal by the modulating signal plus 1 (to ensure the modulation depth).

6.	Plot the Signals:Visualize the modulating, carrier, and modulated signals.

7.	Demodulate the AM Signal:To demodulate, you can use envelope detection. One way is to rectify the signal and then apply a low-pass filter.

8.	Plot the Demodulated Signal:Visualize the demodulated signal.

9.	Compare Signals:Compare the original modulating signal with the demodulated signal.

 ## PROCEDURE
•	Refer Algorithms and write code for the experiment.

•	Open SCILAB in System

•	Type your code in New Editor

•	Save the file

•	Execute the code

•	If any Error, correct it in code and execute again

•	Verify the generated waveform using Tabulation and Model Waveform

## MODEL GRAPH:
<img width="600" height="800" alt="image" src="https://github.com/user-attachments/assets/7bc77926-9c2a-42c6-994b-6c67433b11d2" />

## PROGRAM:
```
	am = 8.8;
	fm = 863;
	fs = 863000;
	pi = %pi;
	t = 0:1/fs:2/fm;
	m = am * cos(2 * pi * fm * t);
	ac = 17.6;
	fc = 8630;
	c = cos(2 * pi * fc * t);
	modulated = (ac + m) .* c;
	
	demod_raw = modulated .* c;
	N = length(demod_raw);
	M = fft(demod_raw);
	f = (0:N-1)*(fs/N);
	
	cutoff = 2 * fm;
	H = (f < cutoff);
	M_filtered = M .* H;
	demodulated = real(ifft(M_filtered));
	
	avg = sum(demodulated) / length(demodulated);
	demodulated = demodulated - avg;
	demodulated = demodulated / max(abs(demodulated));
	demodulated = demodulated * max(abs(m));
	
	subplot(4,1,1);
	plot(t, m);
	title('Message Signal');
	xlabel('Time (s)');
	ylabel('Amplitude');
	
	subplot(4,1,2);
	plot(t, c);
	title('Carrier Signal');
	xlabel('Time (s)');
	ylabel('Amplitude');
	
	subplot(4,1,3);
	plot(t, modulated);
	title('AM Modulated Signal');
	xlabel('Time (s)');
	ylabel('Amplitude');
	
	subplot(4,1,4);
	plot(t, demodulated);
	title('Demodulated Signal');
	xlabel('Time (s)');
	ylabel('Amplitude');
```
 
## TABULATION:

<img width="793" height="450" alt="image" src="https://github.com/user-attachments/assets/09998a45-3ca3-4f82-bee0-a7dae59bb197" />




## CALCULATION:

<img width="757" height="255" alt="image" src="https://github.com/user-attachments/assets/0e11056e-ab98-46f7-bf36-af9c2ffdf65a" />




## OUTPUT:

<img width="730" height="459" alt="image" src="https://github.com/user-attachments/assets/733142c3-ec07-4ee3-89c8-fd48a16bfa57" />


## RESULT:

Thus the amplitude modulation and demodulation is experimentally done and the output is verified.

