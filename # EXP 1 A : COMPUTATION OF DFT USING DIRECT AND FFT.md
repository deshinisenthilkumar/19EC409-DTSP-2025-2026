# EXP 1 A : COMPUTATION OF DFT USING DIRECT AND FFT

# AIM: 
 To Obtain DFT and FFT of a given sequence in SCILAB. 

# APPARATUS REQUIRED: 
PC installed with SCILAB. 

# PROGRAM: 
```
clc;
clear;

xn = input("Enter the sequence in square brackets [ ] : ");

n1 = 0:1:length(xn)-1;


subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

j = %i;
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp((-j*2*%pi*k*n)/N);
    end
end

disp("DFT Values (Xk):");
for k = 1:N
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < N then
        printf(" , ");
    else
        printf("\n");
    end
end

K1 = 0:1:length(Xk)-1;

magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

angle = atan(imag(Xk), real(Xk));
subplot(3,1,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');

```
# DFT USING FFT
```
clc;
clear;

xn = input("Enter the sequence in square brackets [ ] : ");

n1 = 0:1:length(xn)-1;


subplot(3,1,1);
plot2d3(n1, xn);
xlabel('Time n');
ylabel('Amplitude xn');
title('Input Sequence');

j = %i;
N = length(xn);
Xk = zeros(1, N);

for k = 0:N-1
    for n = 0:N-1
        Xk(k+1) = Xk(k+1) + xn(n+1) * exp((-j*2*%pi*k*n)/N);
    end
end

disp("DFT Values (Xk):");
for k = 1:N
    realPart = real(Xk(k));
    imagPart = imag(Xk(k));
    
    if abs(imagPart) < 1e-10 then
        printf("%d", round(realPart));
    elseif imagPart > 0 then
        printf("%d+%dj", round(realPart), round(imagPart));
    else
        printf("%d%dj", round(realPart), round(imagPart));
    end
    
    if k < N then
        printf(" , ");
    else
        printf("\n");
    end
end

K1 = 0:1:length(Xk)-1;

magnitude = abs(Xk);
subplot(3,1,2);
plot2d3(K1, magnitude);
xlabel('frequency (Hz)');
ylabel('magnitude (gain)');
title('Magnitude Spectrum');

angle = atan(imag(Xk), real(Xk));
subplot(3,1,3);
plot2d3(K1, angle);
xlabel('frequency (Hz)');
ylabel('Phase');
title('Phase Spectrum');

```
# OUTPUT: 
# DIRECT
<img width="799" height="761" alt="image" src="https://github.com/user-attachments/assets/34bc9022-52ef-4e8d-b4d4-7f1c573eec19" />

# DFT USING FFT
<img width="806" height="755" alt="image" src="https://github.com/user-attachments/assets/45c8793b-9ec1-457b-8c28-b7fed51fdc08" />

# RESULT: 
DFT and FFT of a given sequence in SCILAB was obtained 
