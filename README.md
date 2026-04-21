# Ideal, Natural, & Flat-top -Sampling
# Aim
Write a simple Python program for the construction and reconstruction of ideal, natural, and flattop sampling.
# Tools required
# Program
```
import numpy as np
import matplotlib.pyplot as plt

# Parameters
fm = 5                      # Message frequency (Hz)
fs = 50                     # Sampling frequency (Hz)

t = np.linspace(0, 1, 1000)   # Continuous time axis
ts = np.arange(0, 1, 1/fs)    # Sampled time axis

# Original analog signal
x = np.sin(2 * np.pi * fm * t)

# Sampled values (ideal samples)
xs = np.sin(2 * np.pi * fm * ts)

# -------- Natural Sampling --------
pulse_width = 0.01
natural = np.zeros_like(t)

for i in range(len(ts)):
    idx = np.where((t >= ts[i]) & (t < ts[i] + pulse_width))
    natural[idx] = x[idx]

# -------- Flat-top Sampling --------
flat_top = np.zeros_like(t)

for i in range(len(ts)-1):
    idx = np.where((t >= ts[i]) & (t < ts[i+1]))
    flat_top[idx] = xs[i]

# -------- Plotting --------
plt.figure(figsize=(12, 8))

# 1. Original Signal
plt.subplot(4,1,1)
plt.plot(t, x)
plt.title("Original Analog Signal")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 2. Ideal Sampling
plt.subplot(4,1,2)
plt.stem(ts, xs, basefmt=" ")
plt.title("Ideal Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 3. Natural Sampling
plt.subplot(4,1,3)
plt.plot(t, natural)
plt.title("Natural Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

# 4. Flat-top Sampling
plt.subplot(4,1,4)
plt.plot(t, flat_top)
plt.title("Flat-top Sampling")
plt.xlabel("Time (s)")
plt.ylabel("Amplitude")
plt.grid()

plt.tight_layout()
plt.show()
```
# Output Waveform
```
<img width="1020" height="672" alt="image" src="https://github.com/user-attachments/assets/c37db69b-a180-47c5-aae5-8fd0a7059c73" />

```
# Results
```
Attach the output waveform
```
# Hardware experiment output waveform.
