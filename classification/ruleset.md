# Face-shape classification rule set

Machine-readable copy: [`ruleset.json`](./ruleset.json).
Source: the constants the live classifier on [knowyourfaceshape.com](https://knowyourfaceshape.com/) imports (`lib/prototypes.ts`), also published in prose at [/about](https://knowyourfaceshape.com/about/). Exported 2026-09-19.

**Method.** Five features per face; each is compared to each of the seven prototypes in units of its own spread (`z = (x - mu) / sigma`), weighted, and summed into one distance per shape. Smallest distance wins.

**Features.** R1 = face length / cheekbone width. R2 = forehead / cheekbone. R3 = jaw / cheekbone. A = angle at the jaw corner (degrees). C = chin width / jaw width.

**Two scales.** The detector measures 10 MediaPipe landmarks; a tape measure touches different points. The scales are related by a per-feature affine map, so z-scores - and therefore the classification - are identical in both. The tape-measure table below is what the site shows users.

## Tape-measure scale (what the site displays)

| Shape | R1 | R2 | R3 | A (deg) | C |
|---|---|---|---|---|---|
| oval | 1.449 | 0.899 | 0.803 | 121.957 | 0.449 |
| round | 1.05 | 0.881 | 0.849 | 132 | 0.55 |
| square | 1.05 | 0.951 | 0.951 | 108 | 0.55 |
| oblong | 1.65 | 0.951 | 0.923 | 118.043 | 0.497 |
| heart | 1.35 | 1.05 | 0.72 | 119.915 | 0.3 |
| diamond | 1.399 | 0.8 | 0.72 | 119.915 | 0.3 |
| triangle | 1.301 | 0.8 | 1.08 | 118.043 | 0.497 |

sigma (tape scale): {"R1":0.182,"R2":0.081,"R3":0.12,"A":7.66,"C":0.083}

weights: {"R1":1.59,"R2":0.97,"R3":1.1,"A":0.85,"C":0.49} - manual-angle boost x1.5 on A when the user supplies their own jaw angle.

## Disclosed limitations (verbatim from the source comments and /about)

- heart (n=1), diamond (n=3) and triangle (n=0) prototypes are interpolated along the literature ordering, not measured.
- Measured jaw angle does not separate square from round in the calibration set (both group means near 133 degrees), while the literature separates them by 24 degrees. The A ordering follows the literature because the classification system is built on it; this is why the site reports mixed-shape hints and confidence instead of a single answer.
- Calibration data: 50 local photographs, MediaPipe GPU inference, single-annotator draft labels.
