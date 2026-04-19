# Optical Ray Simulator

A 2D/3D interactive optical ray-tracing simulator running in the browser.

## Run

Double-click `optics_simulator.html` to open it in any modern browser. The Keplerian telescope preset loads automatically.

## Elements

Convex Lens, Concave Lens, Flat Glass, Flat Mirror, Convex Mirror, Concave Mirror, Aperture Stop, Filter, Detector.

Every element can be moved (drag body) and rotated (drag orange handle, or type degrees in the sidebar).

## Light source modes

- Point source (finite, rotatable)
- Star at infinity (parallel beam with field angle)
- Parallel beam (finite, rotatable)
- Collimated fan (rotatable)

## Spectrum modes

- Monochromatic (single wavelength)
- RGB dispersion (3 wavelengths)
- White light (user-defined range and sample count)

## Aberrations

- Chromatic aberration on/off
- Spherical aberration on/off (strength auto-scaled by f-ratio)

## Presets

Keplerian, Galilean, Newtonian (proper L-shaped path), Cassegrain.

## Controls

| Input | Action |
|---|---|
| Drag element body | Move |
| Drag orange handle | Rotate |
| Mouse wheel | Zoom |
| Shift + drag / right-click drag | Pan |
| 2D / 3D button | Switch view |
| Drag in 3D | Orbit camera |

## Units

Distances in mm, wavelengths in nm, angles in degrees.

## Sign convention

Positive focal length = converging. Negative = diverging. Rotation 0 degrees means the optical axis points along +X.

## Notes

Paraxial thin-element model with optional parametric spherical aberration. Mirrors reflect once per encounter. 3D view shows full revolution symmetry only when all elements have zero rotation and lie on the optical axis.
