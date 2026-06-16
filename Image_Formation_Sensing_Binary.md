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


The key trade-off: wider FOV → more distortion
## Summary

| Concept | Key Idea |
|--------|----------|
| Perspective projection | `x = f·X/Z`, objects shrink with depth |
| Magnification | `m = f/Z` |
| Vanishing point | Parallel lines meet at one point in image |
| Thin lens | `1/f = 1/d_o + 1/d_i`, trades light for focus |
| Depth of field | Aperture controls how much is in focus |
| Lens distortion | Barrel, pincushion, chromatic aberration |
| Wide angle | More FOV = more distortion |
