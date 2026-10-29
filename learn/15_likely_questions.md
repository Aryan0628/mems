# 15 · Likely questions after the talk (with short answers)

> Questions a teacher or classmate might ask, grouped by topic. Each answer is meant to be said out loud in 15–30 seconds. The doc number tells you where to read more.
>
> Tip: when you don't know, say so honestly, and offer the closest thing you *do* know. Keep `gyro3d.html` open to show the Ω slider live (slides 12 and 24 speaker notes).

---

## Basics

**1. What exactly does a gyroscope measure?**
Angular rate: how fast the device is rotating about each axis, in degrees per second. Not the angle itself; to get angle you integrate the rate over time. [01]

**2. Why does the accelerometer read 1 g on a table but the gyro reads zero?**
The accelerometer measures acceleration plus the effect of gravity: the table pushes up on it as if it were accelerating upward at 1 g. Gravity doesn't make anything rotate, and the phone isn't turning, so the gyro reads about 0 °/s (plus a little bias and noise). [01]

**3. Then why do we need a gyro at all if the accelerometer knows which way is down?**
The accelerometer gets confused by any movement or vibration: shakes look like tilt. It also can't sense yaw (turning flat on a table). The gyro tracks fast rotations smoothly; the two are fused. [01, 13]

**4. What does MEMS stand for and how small is it?**
Micro-Electro-Mechanical Systems. Features are 1–100 µm; the sense gap is about 2 µm, about 35× thinner than a hair; a whole 6-axis IMU package is 2.5 × 3 mm. [02, 03]

## Physics

**5. Explain the Coriolis effect simply.**
On a rotating merry-go-round, a ball rolled straight outward appears to curve sideways to someone riding it. That apparent sideways push on anything moving in a rotating frame is the Coriolis force, F = −2m(Ω × v). [04]

**6. Is the Coriolis force a "real" force?**
It is a fictitious (inertial) force: it appears only because we describe motion from a rotating frame. But inside the chip, which *is* the rotating frame, its effect on the proof mass is completely real and measurable. [04]

**7. Why is there a factor of 2 and a minus sign?**
They come out of the maths of converting motion from a fixed frame to a rotating one. The minus sign, together with the cross product, sets the direction of the force; the 2 sets its size. [04]

**8. How big is the Coriolis force in a MEMS gyro?**
With m ≈ 1 µg, v ≈ 1 m/s and Ω = 1 rad/s: F = 2mΩv = 2 × 10⁻⁹ N = 2 nN, about the weight of a speck of dust. It moves the mass well under a nanometre (≈ 0.1 nm in our estimate). [04]

**9. Why does the mass vibrate instead of spin?**
The Coriolis force needs a moving mass. You can't build reliable bearings and motors at micrometre scale, but springs and electrostatic comb drives are easy to etch in silicon. A vibrating mass is always moving, so it works. [05]

**10. Why is the sensed motion at 90° to the drive?**
Because the force is a cross product, Ω × v, which is perpendicular to both the rotation axis and the velocity. With drive along x and rotation about z, the force is along y. [04, 05]

**11. Why is the mass driven at its resonant frequency?**
At resonance a small push gives a large amplitude, like pushing a swing in time. Large amplitude means high velocity, which means a bigger Coriolis force and a bigger signal. [05]

**12. How does the gyro know which direction it's rotating?**
Reversing Ω reverses the Coriolis force, so the sense signal flips sign (animation step 6). The demodulator keeps that sign. [05, 06]

**13. Why does a MEMS gyro need three sensing elements for 3 axes?**
Each element senses rotation only about the axis perpendicular to both its drive and sense directions (no force if v is parallel to Ω). So different structures, or one cleverly designed multi-axis structure, are used for roll, pitch and yaw. [04]

## Sensing and electronics

**14. How do you measure a sub-nanometre movement?**
With capacitance. The mass forms capacitors with fixed electrodes; C = ε₀A/d, so a tiny gap change changes C. Using two capacitors that change in opposite directions gives ΔC ≈ 2C₀·y/d, in the attofarad range. [06]

**15. Why use a differential pair of capacitors?**
The signal doubles, and anything that affects both equally (temperature, stray capacitance, voltage drift) cancels in the difference; linearity also improves. [06]

**16. What does the demodulator do?**
The sense signal is an oscillation at the drive frequency whose size is proportional to Ω. Multiplying by a reference from the drive loop and averaging turns it into a steady value proportional to Ω, keeps the sign, and rejects noise and quadrature error. [06]

**17. Why put the gyro in a vacuum?**
Air damps the vibrating mass. In vacuum the resonator has a high quality factor (Q), giving a large, clean motion for little drive power, which improves sensitivity and noise. [09]

## Architectures and fabrication

**18. Why two masses in a tuning-fork design?**
A single mass can't tell rotation from a bump: both push it sideways. Two masses vibrating in opposite directions get opposite Coriolis forces but identical bump forces. Subtracting doubles the rotation signal and cancels the bump. [07]

**19. What's special about ring resonators?**
A symmetric ring has two identical wine-glass modes at the same frequency (mode matching), so the Coriolis force drives the sense mode at resonance: high sensitivity. Rotation shifts the vibration pattern round the ring (Bryan, 1890). [08]

**20. What is force-rebalance (closed-loop) operation and why use it?**
A controller applies feedback force to hold the sense motion at zero; that force equals the Coriolis force and becomes the output. The mass barely moves, so you get better linearity, wider range and faster response. [08]

**21. Briefly, how is a MEMS gyro made?**
Deposit a sacrificial oxide and a structural polysilicon layer; pattern the shape with photolithography; cut deep vertical trenches with DRIE; dissolve the oxide underneath with HF to release the moving parts; seal under vacuum with a cap wafer. Thousands per wafer. [09]

**22. What are the ridges on the DRIE photo?**
"Scallops" left by the Bosch process, which alternates an etch step and a wall-coating step. Each ridge is one cycle. [09]

## Comparisons and applications

**23. If MEMS is the least precise, why is it everywhere?**
It is tiny (mm), low-power (under 1 mA for a full IMU), rugged (no bearings, shock ratings up to about 10,000 g) and very cheap thanks to batch fabrication. Its drift is corrected by sensor fusion. [10]

**24. How do optical gyros work?**
They use the Sagnac effect: light sent both ways round a rotating loop takes different times. Ring laser gyros measure a frequency difference; fibre-optic gyros measure a phase difference in a long fibre coil. [10]

**25. Which gyro is the most precise?**
On the deck's chart the hemispherical resonator gyro (HRG) has the best bias stability, down to about 0.0001 °/h, followed by ring laser and fibre-optic gyros. MEMS spans roughly 0.05–100 °/h. [10]

**26. How does ESC use the gyro?**
It computes the expected yaw rate from steering angle and speed, compares it with the actual yaw rate from the MEMS gyro, and if they differ, brakes one wheel to pull the car back on course. NHTSA's 2025 update found about a 48% (47.7%) reduction in first-event single-vehicle rollover risk with ESC. [11]

**27. How does OIS use the gyro?**
The gyro measures hand-shake rotation; a controller computes the correction; an actuator moves the lens (or sensor) the opposite way so the image stays still during exposure. [11]

**28. How did the Mars helicopter navigate without GPS?**
Ingenuity used a phone-grade MEMS IMU (Bosch BMI160) for fast attitude and motion sensing, plus a downward-looking camera (and a laser rangefinder for altitude) to correct the IMU's drift. [11]

## Errors and fusion

**29. What is angle random walk vs. bias drift?**
ARW comes from white noise on the rate; integrated, the angle error grows like √t (unit °/√h). Bias drift is a slowly wandering offset; integrated, the error grows like t (unit °/h). Over long periods, bias drift dominates. [12]

**30. How bad is a 10 °/h bias?**
After one hour of pure integration, the heading is off by 10°. That is fine for a phone, which constantly corrects itself, but useless for long-term navigation. [12]

**31. Can a phone gyro detect the Earth's rotation?**
Not really. The Earth turns at 15 °/h, about the same size as a consumer gyro's bias and noise, so it is lost in the error. Navigation-grade gyros (around 0.01 °/h) can. [01, 12]

**32. What is an Allan deviation plot?**
A log–log plot of how much the averaged gyro output varies against averaging time. The falling −½ slope gives the angle random walk; the flat bottom gives the bias instability; the rising +½ slope is rate random walk. One test gives all of them. [12]

**33. What does the complementary filter do, and what does α = 0.98 mean?**
It mixes 98% of the gyro's prediction with 2% of the accelerometer's angle each step. The gyro handles fast motion; the steady 2% pull toward the accelerometer cancels drift. At 100 Hz the crossover is about half a second. [13]

**34. Why do we need a magnetometer?**
The accelerometer gives tilt (roll and pitch) from gravity but can't see yaw. The magnetometer gives heading from the Earth's magnetic field, though it's disturbed by nearby metal. [13]

**35. What's the future of MEMS gyros?**
Better bias stability approaching navigation grade, AI-based drift compensation, and chip-scale optical gyroscopes. Present these as research directions. [13]

---

## Questions to be careful with

- **"Does every smartphone have a gyroscope?"** Most do, but some budget models leave it out. Don't claim "every". (Slides 4 and 18 say "every/each".)
- **"Where does 1.2 billion come from?"** It is an estimate of yearly smartphone shipments that we haven't verified. Say "over a billion smartphones a year, roughly" unless you have checked a current source. [03]
- **"Which way does the ball curve in the merry-go-round picture?"** For an anticlockwise spin (seen from above) the ball curves to the right of its path; for clockwise, to the left. The slide's drawing pairs a clockwise arrow with a rightward curve, so explain the rule rather than defending the drawing. [04]
- **"Is < 0.1 °/h navigation grade?"** Slide 21 uses about 0.01 °/h for navigation grade, so < 0.1 °/h is "approaching navigation grade". [13]

---

## Key points to remember

- Know the **one-sentence version** of each topic; most questions are "explain X simply".
- Have the numbers ready: **2 nN**, **< 1 nm**, **attofarads**, **10–30 kHz**, **10,000 g**, **10 °/h → 10° per hour**, **α ≈ 0.98**, **–48%**.
- Be honest about the **unverified** "≈ 1.2 billion" figure and the "every smartphone" wording.

**Which slide uses this:** Slide 24 ("Thank you · Questions are welcome"), and every slide before it.

## Self-check

1. Answer question 9 out loud in under 20 seconds.
2. Answer question 18 using the words "anti-phase" and "subtract".
3. What would you say if asked for the source of "≈ 1.2 billion"?
4. Give the three numbers you'd quote for the size of the effect inside a MEMS gyro.

<details>
<summary>Answers</summary>

1. "The Coriolis force only acts on a moving mass. Spinning parts need bearings, which can't be made reliably at micrometre size, but springs and comb drives are easy to etch in silicon. A vibrating mass is always moving, so rotation produces a Coriolis force on it."
2. "The two masses vibrate in anti-phase, so rotation pushes them opposite ways while a bump pushes them the same way. When we subtract their outputs, the rotation signal doubles and the bump cancels."
3. "It's an estimate of yearly smartphone shipments that we haven't verified ourselves. The safe statement is 'over a billion phones a year', and not every one has a gyro."
4. Force ≈ 2 nN at 1 rad/s; motion under 1 nm; capacitance change in the attofarad (10⁻¹⁸ F) range.

</details>

---

### Sources
- All answers follow docs 01–13 in this folder, which list their sources (deck references [1]–[10], NHTSA DOT HS 813 749, Apple newsroom, Bosch/InvenSense datasheets, IEEE Std 952, and others).
