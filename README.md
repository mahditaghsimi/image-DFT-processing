# image-DFT-processing
Frequency‑domain image filtering using DFT and a Gaussian low‑pass filter.

---

This project demonstrates how to:
- Load and preprocess a grayscale image  
- Compute its 2‑D DFT (magnitude + phase)  
- Design and apply a Gaussian Low‑Pass Filter in the frequency domain  
- Reconstruct the filtered image using inverse DFT  
- Compare the noisy input with the filtered result

---

## 1. Overview  
In the frequency domain, low‑pass filters remove high‑frequency components such as salt‑and‑pepper noise.  
A Gaussian LPF is smooth, isotropic, and avoids sharp discontinuities compared to an ideal LPF.

The workflow of this project:
1. Read a noisy grayscale image  
2. Compute DFT and visualise magnitude/phase  
3. Build a 2‑D Gaussian LPF  
4. Multiply the DFT with the filter  
5. Apply inverse DFT to reconstruct the cleaned image

---

## 2. Input Image  
<img width="407" height="203" alt="image" src="https://github.com/user-attachments/assets/58c65a3e-f29b-44e5-934f-e6097de016cc" />

---

## 3. Magnitude & Phase Spectra  
The DFT decomposes the image into its frequency components.  
- The **magnitude spectrum** shows frequency strength  
- The **phase spectrum** preserves structural information
<img width="950" height="218" alt="image" src="https://github.com/user-attachments/assets/bf6c29dd-b7bf-42ec-9498-8dfcfa28338b" />

---

## 4. Gaussian Low‑Pass Filter  
A Gaussian LPF is defined as:

$$
H(u, v) = \exp\!\left( -\frac{u^{2} + v^{2}}{2\.D_{0}^{2}} \right)
$$

Where:
- `D0` = cutoff frequency  
- Smaller `D0` removes more high‑frequency noise  
- Larger `D0` keeps details but reduces smoothing
<img width="407" height="203" alt="image" src="https://github.com/user-attachments/assets/d0e162a0-e647-4621-bfe8-e7149a65d786" />

---

## 5. Filtered Image (After Applying Gaussian LPF)  
The filtered output is obtained by:
1. Multiplying the shifted DFT with the Gaussian mask  
2. Applying inverse shift  
3. Computing the real‑valued magnitude  
4. Normalising back to 0–255
<img width="484" height="235" alt="image" src="https://github.com/user-attachments/assets/65ca671f-61ae-480e-8f0b-793b170893c6" />

---

## 6. Input vs Output Comparison  
The difference clearly shows:
- Salt‑and‑pepper noise is reduced  
- Low‑frequency components (main structure) are preserved  
- Edges become smoother due to Gaussian LPF behaviour
<img width="950" height="218" alt="image" src="https://github.com/user-attachments/assets/75cc938d-515c-4e54-991b-c28ba27fb159" />

---

## 7.Requirements
```
opencv-python
numpy
matplotlib
```
---

## 8.Project Structure
```
image-DFT-processing/
│
├── images/                 # Input & Output Images
├── src/                    # Python Scripts
├── requirements.txt
└── README.md
```

---
