# EXP 1 :  ANALYSIS OF DFT WITH AUDIO SIGNAL

# AIM: 
 To analyze audio signal by removing unwanted frequency. 

# APPARATUS REQUIRED: 
PC installed with SCILAB/Python. 

# PROGRAM: 
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.io import wavfile
from google.colab import files
from scipy.fft import fft, fftfreq

# ---- 1. UPLOAD AUDIO FILE ----
print("Upload an audio file (.wav)")
uploaded = files.upload()

filename = list(uploaded.keys())[0]

# ---- 2. READ AUDIO FILE ----
fs, audio = wavfile.read(filename)
print("Sampling Frequency =", fs)

# Convert to mono if stereo
if len(audio.shape) == 2:
    audio = audio.mean(axis=1)

# Normalize audio
audio = audio / np.max(np.abs(audio))

# ---- 3. PLOT TIME DOMAIN WAVEFORM ----
t = np.linspace(0, len(audio)/fs, len(audio))

plt.figure(figsize=(12,4))
plt.plot(t, audio)
plt.title("Time-Domain Audio Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()
plt.show()

# ---- 4. COMPUTE DFT USING FFT ----
N = len(audio)
Y = fft(audio)
Y_mag = np.abs(Y) / N          # magnitude spectrum
freq = fftfreq(N, 1/fs)        # frequency bins

# ---- 5. PLOT MAGNITUDE SPECTRUM (0 to fs/2) ----
half = N // 2

plt.figure(figsize=(12,4))
plt.plot(freq[:half], Y_mag[:half])
plt.title("Magnitude Spectrum (FFT)")
plt.xlabel("Frequency (Hz)")
plt.ylabel("Magnitude")
plt.grid()
plt.show()

# ---- 6. PRINT DOMINANT FREQUENCIES ----
# Find top peaks
indices = np.argsort(Y_mag[:half])[-5:][::-1]
dominant_freqs = freq[indices]

print("\nTop 5 dominant frequency components (Hz):")
print(dominant_freqs)

```

# OUTPUT: 
<img width="811" height="313" alt="image" src="https://github.com/user-attachments/assets/9d040855-2ad1-4d54-bb53-c43d6eb22977" />

<img width="810" height="307" alt="image" src="https://github.com/user-attachments/assets/8ad6b04b-bdf6-4c16-9d20-54c42db2d6eb" />

# RESULTS
Thus ,the audio signal was analyzed using DFT.
