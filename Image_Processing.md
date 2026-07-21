# Image Processing

> **Goal:** Transform an image into a new one that is clearer or easier to analyze.

## Topics Covered
1. Pixel Processing
2. LSIS and Convolution
3. Linear Image Filters
4. Non-Linear Image Filters
5. Template Matching by Correlation

---

## 1. Pixel Processing

Pixel processing applies a transformation **T** to the intensity `f` at each pixel to produce a new intensity `g`:

```
g(x, y) = T[ f(x, y) ]
```

### Common Transformations

| Operation      | Formula              |
|----------------|-----------------------|
| Darken         | `f - 128`             |
| Lighten        | `f + 128`             |
| Invert         | `255 - f`              |
| Low Contrast   | `f / 2`                |
| High Contrast  | `f * 2`                |
| Grayscale      | `0.3·fr + 0.6·fg + 0.1·fb` |

---

## 2. Linear Shift Invariant System (LSIS)

The study of **Linear Shift Invariant Systems (LSIS)** leads to many useful image processing algorithms, most notably **convolution**.

### Convolution in LSIS

**Linearity:**
```
T[a·f1 + b·f2] = a·T[f1] + b·T[f2]
```

- Convolution is a linear operation.
- Convolution is also **shift-invariant** — shifting the input shifts the output by the same amount, without changing its shape.

### Unit Impulse Function

- Acts as the fundamental building block for LSIS analysis.
- Any signal can be expressed as a weighted sum of shifted impulses.
- The response of an LSIS to a unit impulse defines its **impulse response**, which fully characterizes the system.

### Properties of Convolution

1. **Commutative** — `f * g = g * f`
2. **Associative** — `(f * g) * h = f * (g * h)`
3. **Cascaded Systems** — Two LSIS systems in series can be replaced by a single system whose impulse response is the convolution of the two individual impulse responses.

---

## 3. Linear Image Filters

A linear filter produces each output pixel as a **weighted sum** of the pixel's neighborhood in the input image:

```
g = f * h
```
where `h` is the filter kernel (mask).

### Key Properties
- **Normalization** — kernel weights typically sum to 1, so overall image brightness is preserved.
- **Separability** — some 2D kernels (e.g., Gaussian) can be split into two 1D convolutions, reducing computation.

### Common Linear Filters

| Filter          | Effect                                  |
|------------------|-------------------------------------------|
| Box Filter       | Simple averaging → blurring, noise reduction |
| Gaussian Filter  | Weighted averaging (center-heavy) → smoother, more natural blur |
| Sobel / Derivative Filters | Highlight intensity changes → used for edge enhancement |

### Notes
- Larger kernel size → stronger blurring, but more loss of detail.
- Gaussian filters are preferred over box filters because they avoid harsh ringing artifacts and better approximate natural blur.

---

## 4. Non-Linear Image Filters

Unlike linear filters, the output pixel is **not** a weighted linear combination of neighboring pixels — it's computed using a non-linear operation (e.g., median, min, max).

### Common Non-Linear Filters

| Filter            | How it Works                                         | Use Case                          |
|---------------------|--------------------------------------------------------|-------------------------------------|
| Median Filter       | Replaces pixel with the **median** of its neighborhood | Removes salt-and-pepper noise while preserving edges |
| Min Filter (Erosion) | Replaces pixel with the **minimum** in neighborhood     | Shrinks bright regions, removes small bright noise |
| Max Filter (Dilation)| Replaces pixel with the **maximum** in neighborhood     | Grows bright regions, fills small dark gaps |
| Bilateral Filter     | Weighted average using both **spatial distance** and **intensity difference** | Smooths image while preserving edges |

### Why Non-Linear Filters Matter
- Linear filters (like Gaussian) blur **everything**, including edges.
- Non-linear filters like median and bilateral filters can suppress noise **without** destroying edge information — important for later edge detection and segmentation steps.

---

## 5. Template Matching by Correlation

**Goal:** Locate where a given template (pattern) appears within a larger image.

### Method
1. Slide the template over every location in the image.
2. At each position, compute a similarity score between the template and the underlying image patch using **correlation**.
3. The location with the **highest correlation score** is the best match.

### Cross-Correlation
```
score(x, y) = Σ [ f(x+i, y+j) · t(i, j) ]
```
- Simple but sensitive to changes in overall brightness/contrast between template and image.

### Normalized Cross-Correlation (NCC)
- Normalizes both template and image patch (subtracts mean, divides by standard deviation) before correlating.
- Makes matching **robust to illumination and contrast changes**.
- Score ranges from -1 (inverse match) to 1 (perfect match).

### Limitations
- Sensitive to **scale** changes (template size vs. object size in image).
- Sensitive to **rotation** (template must match orientation).
- Computationally expensive for large images/templates (can be sped up using FFT-based correlation).

---

## Summary
| Concept | Core Idea |
|----------|------------|
| Pixel Processing | Per-pixel intensity transformation |
| LSIS & Convolution | Linear + shift-invariant systems → convolution as the core tool |
| Linear Filters | Weighted neighborhood averaging (Box, Gaussian) |
| Non-Linear Filters | Neighborhood operations that preserve edges (Median, Bilateral) |
| Template Matching | Finding a pattern in an image via correlation |
