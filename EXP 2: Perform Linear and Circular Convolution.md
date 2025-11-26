# EXP 1 : Linear and Circular Convolution

## AIM: 
To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
x = input("Enter x(n) as a vector, e.g., [1 2 1 2]: ");
h = input("Enter h(n) as a vector, e.g., [1 1]: ");

Nx = length(x);
Nh = length(h);
Ny = Nx + Nh - 1;

x_p = [x, zeros(1, Ny - Nx)];
h_p = [h, zeros(1, Ny - Nh)];

y = zeros(1, Ny);
for n = 0:Ny-1
    for k = 0:Nx-1
        if (n-k >= 0 & n-k < Nh) then
            y(n+1) = y(n+1) + x_p(k+1) * h_p(n-k+1);
        end
    end
end

disp("y(n) = "), disp(y);

clf;

subplot(3,1,1);
n1 = 0:Nx-1;
plot2d3(n1, x);   
xtitle("x(n)");

subplot(3,1,2);
n2 = 0:Nh-1;
plot2d3(n2, h);
xtitle("h(n)");

subplot(3,1,3);
n3 = 0:Ny-1;
plot2d3(n3, y);
xtitle("y(n) = x(n) * h(n)");

```

## PROGRAM (Circular Convolution): 
```
clc;
clear;


function [y] = pmod(a, n)
    y = modulo(a, n);
endfunction


disp("Enter first sequence x: ");
x = input("");

disp("Enter second sequence h: ");
h = input("");

N = max(length(x), length(h));


x = [x, zeros(1, N-length(x))];
h = [h, zeros(1, N-length(h))];

y_lin = conv(x, h);

y_circ = zeros(1, N);
for k = 1:length(y_lin)
    idx = pmod(k-1, N) + 1;
    y_circ(idx) = y_circ(idx) + y_lin(k);
end

disp("Circular Convolution using conv():");
disp(y_circ);

subplot(3,1,1);
plot2d3(0:N-1, x);
xtitle("Input Sequence x[n]");

subplot(3,1,2);
plot2d3(0:N-1, h);
xtitle("Input Sequence h[n]");

subplot(3,1,3);
plot2d3(0:N-1, y_circ);
xtitle("Circular Convolution y[n]");

```

## OUTPUT (Linear Convolution): 
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/c9fa6ba5-b604-47db-a285-e70a03f66225" />

## OUTPUT (Circular Convolution): 
<img width="800" height="400" alt="image" src="https://github.com/user-attachments/assets/862445c2-f5cf-4054-a24e-013c6686a69d" />

## RESULT: 
Thus, the linear convolution and circular convolution of the two given sequences were performed and its result was verified.
