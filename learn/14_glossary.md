# 14 · Glossary (A–Z)

> Every technical term used in the deck, plus a few that come up in questions. One or two plain lines each. The doc number in brackets tells you where to read more.

---

**6-axis IMU**: A chip with a 3-axis accelerometer and a 3-axis gyroscope (e.g. Bosch BMI270). [03]

**9-axis IMU**: A 6-axis IMU plus a 3-axis magnetometer (e.g. ST LSM9DS1). [13]

**Accelerometer**: Sensor that measures linear acceleration including the effect of gravity; reads about 1 g when lying still. [01]

**ADC (analogue-to-digital converter)**: Circuit that turns a voltage into a number the processor can read. [06]

**Actuator**: The part that makes something move, e.g. the tiny motor that shifts the camera lens in OIS. [11]

**Allan deviation**: A plot of how much a sensor's averaged output varies against averaging time τ, on log–log axes; used to read ARW and bias instability. [12]

**Anchor**: A point where the moving structure is fixed to the substrate; springs connect the anchors to the proof mass. [05, 09]

**Angle random walk (ARW)**: Random wandering of the integrated angle caused by white noise on the rate signal; grows with √t; unit °/√h. [12]

**Angular rate / angular velocity**: How fast something rotates, in °/s or rad/s. What a gyroscope measures. [01]

**Anti-phase**: Two things vibrating in exactly opposite directions at every instant, like the prongs of a tuning fork. [07]

**Apollo IMU**: The 1960s inertial measurement unit of the Apollo spacecraft, built from spinning-wheel gyros on gimbals. [03]

**AR / VR (augmented / virtual reality)**: Headsets and apps that need fast head-rotation tracking from a gyro. [11]

**Attofarad (aF)**: 10⁻¹⁸ farad. The size of the capacitance changes a MEMS gyro must detect. [06]

**Batch fabrication**: Making thousands of devices at once on a single wafer, so each one is cheap. [02, 09]

**Bias (zero-rate offset)**: The gyro's output when it is not rotating at all; ideally zero. [12]

**Bias drift**: Slow wandering of the bias with time and temperature; integrated, it gives an angle error growing in proportion to t. [12]

**Bias instability / bias stability**: The standard measure of how much the bias wanders, in °/h; read from the flat minimum of the Allan plot. Lower is better. [10, 12]

**Bosch process**: The DRIE technique that alternates etching and wall-coating steps to cut deep vertical trenches. [09]

**Bryan's effect**: G. H. Bryan's 1890 observation that rotating a ringing bell or cylinder shifts its vibration pattern; the basis of ring and hemispherical gyros. [08]

**Capacitance (C)**: How much charge two conductors store per volt; for parallel plates C = ε₀A/d. [06]

**Cap wafer / vacuum cap**: A second wafer bonded on top to seal the gyro in vacuum. [09]

**C-to-V amplifier (charge amplifier)**: Converts tiny capacitance (charge) changes into a voltage. [06]

**Closed-loop (force-rebalance) operation**: Feedback electrodes hold the sense motion at zero; the feedback force needed is the output. [08]

**Comb fingers / comb drive**: Interlocking comb-shaped electrodes; used to drive the mass (by electrostatic force) and to sense its motion (capacitance). [06]

**Common-mode rejection**: Cancelling errors that affect two signals equally by taking their difference. [06, 07]

**Complementary filter**: Simple fusion formula θ = α(θ + ω·Δt) + (1 − α)·θ_acc; trusts the gyro short-term and the accelerometer long-term. [13]

**Coriolis force**: Apparent sideways force on a mass moving in a rotating frame: F_c = −2m(Ω × v). [04]

**Cross product (×)**: Vector operation giving a vector perpendicular to both inputs, size |A||B| sin θ, direction by the right-hand rule. [04]

**Dead reckoning**: Navigating by starting from a known point and integrating your own turning and acceleration, with no outside signal. [11]

**Demodulator**: Circuit that multiplies the sense signal by a reference from the drive loop to recover a steady value proportional to Ω (with sign). [06]

**Deposition**: Adding a thin film of material (oxide, polysilicon) to a wafer. [09]

**Die**: One individual chip cut from a wafer. [02]

**Differential capacitor**: A moving plate between two fixed plates; one capacitance rises as the other falls, giving ΔC ≈ 2C₀·y/d. [06]

**Disk resonator gyroscope (DRG)**: A gyro made of many nested rings forming a disk, vibrating in wine-glass modes. [08]

**Drive mode**: The motion the gyro deliberately keeps going (mass vibrating along x at resonance). [05]

**DRIE (deep reactive-ion etching)**: Plasma etching that cuts deep, vertical, high-aspect-ratio trenches (> 20:1). [09]

**ESC (Electronic Stability Control)**: Car safety system comparing expected and actual yaw rate and braking individual wheels to prevent skids. [11]

**Etching**: Removing material where it is not protected by the patterned photoresist. [09]

**Feedback electrodes**: Electrodes that apply a force to cancel motion in closed-loop operation. [08]

**FOG (fibre-optic gyroscope)**: Optical gyro sending light both ways round a long fibre coil; rotation causes a phase difference (Sagnac effect). [10]

**g**: Acceleration due to gravity, ≈ 9.81 m/s²; also used for shock ratings (e.g. 10,000 g). [01, 05]

**Getter**: Material inside a sealed cavity that absorbs stray gas to keep the vacuum good. [08, 09]

**Gimbal**: A pivoted ring that lets an object stay pointing one way while its mount turns; used in old spinning-wheel gyros. [03]

**GPS-denied**: Any place GPS signals can't reach or are jammed: tunnels, buildings, underwater, other planets. [11]

**Gyroscope (gyro)**: A sensor that measures rotation rate (angular velocity). [01]

**HF (hydrofluoric acid)**: Acid that dissolves silicon dioxide but not silicon; used for the release step. [09]

**HRG (hemispherical resonator gyroscope)**: A vibrating quartz "wine glass" gyro; the most stable type, used on spacecraft. [10]

**IMU (inertial measurement unit)**: A package of accelerometers and gyroscopes (sometimes magnetometers). [02, 13]

**Integration**: Adding up a rate over time to get a total (rate → angle; acceleration → velocity → position). Also accumulates errors. [12]

**Kalman filter**: A statistically optimal fusion algorithm that weights each sensor by its uncertainty and can estimate gyro bias. [13]

**Lithography (photolithography)**: Printing a pattern onto a wafer by shining UV light through a mask onto photoresist. [09]

**Magnetometer**: Sensor measuring the magnetic field; works as an electronic compass to find north (yaw). [13]

**Mask**: A glass plate carrying the pattern to be printed in lithography, like a stencil. [09]

**MEMS (Micro-Electro-Mechanical Systems)**: Tiny machines with moving parts and electronics built on a silicon chip. [02]

**Mode matching**: Making the drive and sense resonant frequencies equal, so the sense response is amplified by Q; natural in symmetric rings. [08]

**Navigation grade**: The most precise gyro class; bias around 0.01 °/h (slide 21). [10, 12]

**OIS (optical image stabilisation)**: Camera feature where the gyro measures hand shake and the lens is moved the opposite way. [11]

**Open-loop operation**: Letting the sense mode move freely and measuring how far it moves. [08]

**Oversteer / understeer**: The car rotating more (rear sliding out) / less (front sliding wide) than the driver intended. [11]

**Photoresist**: Light-sensitive coating used in lithography. [09]

**Pick-off**: Electrode that measures (picks off) the motion of a resonator. [08]

**Pitch**: Rotation about the side-to-side axis (nose up / nose down). [01]

**Polysilicon**: Silicon made of many small crystals; a common structural layer in MEMS. [09]

**Proof mass**: The small moving mass inside a MEMS sensor whose motion is measured. [05]

**Quadrature error**: An unwanted sense signal, a quarter cycle out of step with the Coriolis signal, caused by manufacturing imbalance; rejected by phase-sensitive demodulation. [06]

**Quality factor (Q)**: How "ringy" a resonator is; high Q means low energy loss and large amplitude for little drive. Vacuum raises Q. [08, 09]

**rad/s**: Radians per second; 1 rad/s ≈ 57.3 °/s. [01]

**Rate random walk**: Slow random wandering of the bias itself; the +½ slope on the right of the Allan plot. [12]

**Release**: Dissolving the sacrificial layer so the structure becomes free to move. [09]

**Release holes**: Small holes in large structures so the etchant can reach the sacrificial layer underneath. [09]

**Resonant frequency**: The natural frequency at which a mass–spring system vibrates most easily; ≈ 10–30 kHz for MEMS gyro drive modes. [05]

**Right-hand rule**: Rule for the direction of a cross product or rotation vector: curl fingers along the rotation, thumb gives the axis. [04]

**Ring laser gyroscope (RLG)**: Optical gyro where two laser beams circulate opposite ways round a mirror loop; rotation creates a frequency difference. [10]

**Roll**: Rotation about the front-to-back axis (one wing down). [01]

**Rollover detection**: Using a roll-rate gyro plus accelerometer to predict a car rollover and fire curtain airbags. [11]

**Sacrificial layer**: A temporary layer (usually oxide) that supports the structure during processing and is removed at release. [09]

**Sagnac effect**: Light travelling both ways round a rotating loop takes different times; the basis of optical gyros (1913). [10]

**Scale factor (sensitivity)**: How much output you get per °/s (e.g. 131 counts per °/s). Errors in it are scale-factor errors. [06, 12]

**SEM (scanning electron microscope)**: Microscope using electrons to image tiny structures; source of the deck's black-and-white device photos. [02]

**Sense mode**: The motion caused by the Coriolis force, at 90° to the drive, which is measured. [05]

**Sensor fusion**: Combining several sensors so each covers another's weakness. [13]

**Solid-state**: No spinning or rubbing parts; MEMS gyros vibrate rather than spin. [05]

**Stiction**: Microscopic parts sticking to the substrate (often during drying after release). [09]

**Tactical grade**: Middle precision class; bias around 1 °/h (slide 21). [12]

**Tuning-fork gyroscope**: Design with two masses vibrating in anti-phase, so rotation signals add and shocks cancel. [07]

**Wafer**: Thin polished disc of silicon on which many chips are made together. [09]

**Wine-glass mode**: Vibration where a ring or shell flexes into an ellipse and back. [08]

**Yaw**: Rotation about the vertical axis (turning left/right). [01]

**Yaw rate**: How fast a vehicle is rotating about its vertical axis; what ESC's gyro measures. [11]

**°/h, °/√h, °/s**: Degrees per hour (bias), degrees per root-hour (ARW), degrees per second (rotation rate). [01, 12]

---

## Key points to remember

- When in doubt, a **gyro** measures **rate**, an **accelerometer** measures **acceleration incl. gravity**.
- **Drive** = motion we create; **sense** = motion rotation causes, at 90°.
- **ARW** (°/√h, √t growth) vs **bias instability** (°/h, t growth).
- **DRIE, HF release, vacuum cap** are the key fabrication words.

**Which slide uses this:** All of them; keep this page open while rehearsing.

## Self-check

1. What is the difference between "drive mode" and "sense mode"?
2. What does "anti-phase" mean?
3. What is a sacrificial layer?
4. Expand ESC, OIS, IMU and DRIE.

<details>
<summary>Answers</summary>

1. Drive mode is the vibration the gyro maintains on purpose (along x); sense mode is the motion caused by the Coriolis force when the chip rotates (along y, at 90°).
2. Two things vibrating in exactly opposite directions at every instant.
3. A temporary layer (usually silicon dioxide) that supports the structure during fabrication and is dissolved at the release step.
4. Electronic Stability Control; Optical Image Stabilisation; Inertial Measurement Unit; Deep Reactive-Ion Etching.

</details>

---

### Sources
- Definitions follow the deck (slides 1–22) and the other docs in this folder, which list their own sources.
