# Image Formation

An image is a **projection of a 3D scene onto a 2D plane**.

To understand this, we need two things:
- **Geometric** — given a point in the scene, where does it land in the image?
- **Photometric** — given the brightness/appearance of a point in the scene, what does it look like in the image?

---

## 1. Pinhole Camera & Perspective Projection

A pinhole camera is the simplest camera model. It has a tiny hole (pinhole) instead of a lens. Light from the scene passes through this hole and forms an image on the opposite wall (image plane).

### How it works

```
Scene point P = (X, Y, Z)
Pinhole at origin
Image plane at distance f (focal length)

Projected image point p = (x, y)
```

### Perspective Projection Equations

```
x = f · (X / Z)
y = f · (Y / Z)
```

- `f` = focal length (distance from pinhole to image plane)
- `Z` = depth of the scene point
- As `Z` increases (object moves farther), `x` and `y` get smaller → objects look smaller when far away.

### Image Magnification

```
Magnification m = f / Z
```

- Object of height `H` at depth `Z` → image height `h = f · H / Z`
- Deeper the object, smaller it appears in image.

---

## 2. Vanishing Points

Parallel lines in the real world appear to **converge at a single point** in the image — this is called the **vanishing point**.

Key facts:
- Every set of parallel lines has its own vanishing point.
- The location of the vanishing point depends on the **orientation** of those lines (not their position).
- Lines parallel to the image plane have a vanishing point **at infinity** (they stay parallel in the image).
- Vanishing points are often used in art and photography to draw attention — the eye naturally moves toward them.

### False Perspective

When you photograph a flat image (like a painting or billboard) that itself contains perspective cues, the camera adds another layer of projection on top. This can create misleading or distorted depth perception — called **false perspective**.

---

## 3. Image Formation Using Lenses

A pinhole camera has one big problem — the hole must be tiny to keep the image sharp, which lets in very little light → dark image.

**Solution: use a lens.**

A lens bends (refracts) light so that rays from a single scene point converge back to a single image point, even through a large opening. This lets in much more light.

### Thin Lens Equation

```
1/f = 1/d_o + 1/d_i
```

- `f` = focal length of the lens
- `d_o` = distance of object from lens
- `d_i` = distance of image from lens

When this equation is satisfied, the object is **in focus**.

## 4. Depth of Field

**Depth of Field (DOF)** is the range of distances in a scene that appear acceptably sharp in an image.

Only objects at the focus distance are perfectly sharp. Objects closer or farther away become increasingly blurred.

### Hyperfocal Distance

The **hyperfocal distance** is the focus distance that maximizes depth of field.

When a lens is focused at the hyperfocal distance:

* Objects from approximately half that distance to infinity appear sharp.
* It is commonly used in landscape photography to keep most of the scene in focus.

### Aperture Size: DOF vs Brightness

The aperture controls both the amount of light entering the camera and the depth of field.

**Large Aperture (small f-number, e.g., f/1.8)**

* Brighter image or shorter exposure time
* Shallow depth of field
* Strong background blur

**Small Aperture (large f-number, e.g., f/16)**

* Darker image or longer exposure time
* Large depth of field
* More of the scene remains in focus

## 5. Issues Related to Lens

**Vignetting**

Image is darker at the edges than at the center. Caused by less light reaching the edges of the image sensor.

**Chromatic Aberration**

Different wavelengths of light (colors) bend by different amounts through a lens → colored fringing/blurring around edges.

**Radial Distortion**

Straight lines in the scene appear curved in the image.

Barrel distortion — lines bow outward (common in wide-angle lenses)
Pincushion distortion — lines bow inward (common in telephoto lenses)

## 6. Wide Angle Cameras
Standard perspective projection has a limited field of view (FOV). To capture more of the scene, we use wide angle cameras.

**Fisheye Lens**

Extremely wide FOV (up to 180°)
Uses spherical (not perspective) projection
Produces heavy barrel distortion — straight lines look curved

**Catadioptric Camera (Mirror + Lens)**

Uses a curved mirror (parabolic or hyperbolic) combined with a lens
Can achieve a full 360° horizontal FOV
Used in surveillance and robotics

# Image Sensing
It is the process of capturing light from an object or scene and converting it into a digital image using a sensor (such as a camera sensor).

## 1. Types of Image Sensors

### **Charge Coupled Device (CCD)**

* Converts light into electrical charge and transfers it across the sensor for processing.
* Produces high-quality images with low noise.
* Consumes more power and is relatively expensive.
* Commonly used in scientific, medical, and industrial imaging.

### **Complementary Metal-Oxide Semiconductor (CMOS)**

* Converts and processes signals directly at each pixel.
* Faster, cheaper, and more power-efficient than CCD.
* Widely used in smartphones, webcams, and digital cameras.
* Modern CMOS sensors provide excellent image quality with low power consumption.

### **Rolling Shutter vs Global Shutter**

* **Rolling shutter** — the sensor reads out rows one after another rather than all at once. Common in CMOS sensors. Fast-moving objects or fast camera motion appear skewed or wobbly (rolling shutter distortion).
* **Global shutter** — the entire frame is captured at the same instant. Common in CCD and high-end CMOS sensors. Avoids motion distortion but is more expensive.

## 2. Resolution, Noise, Dynamic Range

### **Resolution**

* Refers to the number of pixels in an image.
* Higher resolution captures more details.
* Common examples: 1920×1080 (Full HD), 3840×2160 (4K).
* Important for image clarity and object recognition.

### **Noise**

* Unwanted modification of signal during capture, conversion, transmission, processing.
* Often caused by low light conditions or sensor limitations.
* Makes images appear grainy or distorted.
* Noise reduction techniques are used to improve image quality.

#### **Photon Shot Noise (Scene Dependent)**

* Caused by the random arrival of photons at the sensor.
* Increases with light intensity.
* Fundamental noise that cannot be completely eliminated.
* Photon Shot Noise is modeled using the Poisson distribution because photons arrive at a camera sensor randomly and independently.

#### **Readout Noise (Scene Independent)**

* Introduced during sensor readout and signal amplification.
* Exists even when no light is present.
* Depends on sensor electronics and circuitry quality.
* Gaussian Distribution.

#### **Other Sources (Scene Independent)**

* Thermal (Dark Current) Noise due to sensor heating.
* Quantization Noise introduced during analog-to-digital conversion.
* Fixed Pattern Noise caused by pixel-to-pixel sensor variations.

 

### **Dynamic Range**

* The range between the darkest and brightest parts of an image.
* Higher dynamic range preserves details in both shadows and highlights.
* Important for scenes with strong lighting variations.
* Often measured in stops (exposure levels).

## 3. Sensing Color

### **Quantum Efficiency (QE)**

* Quantum Efficiency (QE) measures how effectively a sensor converts incoming photons into electrons.
* QE varies with the wavelength of light.
* Silicon sensors have high QE in the near-infrared region and lower QE at shorter wavelengths.
* QE determines the sensitivity of an image sensor to different colors.

### **Spectral Distribution**

* Light reflected from an object contains a range of wavelengths called its spectral distribution.
* Different objects have different spectral distributions.
* A sensor measures the combined effect of all incoming wavelengths.
* The complete spectral distribution cannot be recovered from a single sensor measurement.

### **Color Filters**

* Filters are placed in front of sensors to selectively measure specific wavelength ranges.
* Different filters capture different portions of the spectrum.
* Multiple filtered measurements provide color information.
* Color sensing relies on combining information from several filters.

### **Bayer Filter & Demosaicing**

* The **Bayer filter** is the most common color filter array placed over a sensor — a mosaic of red, green, and blue filters, with twice as many green filters as red or blue (because human vision is most sensitive to green).
* Each pixel therefore records only one color (R, G, or B).
* **Demosaicing** is the process of interpolating the missing color values at each pixel to reconstruct a full-color image.
* Poor demosaicing can introduce artifacts such as false colors and zipper/moiré patterns near edges.

### **Visible Spectrum**

* Human vision is sensitive to wavelengths approximately between 400 nm and 700 nm.
* Wavelengths below 400 nm are called ultraviolet (UV).
* Wavelengths above 700 nm are called infrared (IR).
* Cameras can be designed to capture UV and IR information beyond human vision.

### **Human Visual Sensors**

* The retina contains two types of photoreceptors: rods and cones.
* Rods are responsible for brightness perception and low-light vision.
* Cones are responsible for color perception.
* There are three types of cones — short (S/blue), medium (M/green), and long (L/red) wavelength — which is why human color vision is **trichromatic**. This is also why cameras use three color channels (RGB).
* Visual information is processed and transmitted to the brain through the optic nerve.

