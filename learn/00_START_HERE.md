# MEMS Gyroscopes: study notes (start here)

These notes are for the team presenting **"MEMS Gyroscopes: How a vibrating speck of silicon senses rotation"** (`../MEMS_Gyroscope.pptx`, 24 slides). They assume you know basic physics (F = ma, vectors) and **nothing** about gyroscopes. Read them in order and you should be able to present every slide and handle questions.

![Microscope photo of the InvenSense MPU-6050 MEMS die](img/photo_mpu6050_die.jpg)

*The silicon inside a phone-grade motion sensor (InvenSense MPU-6050), as on the title slide. Photo: ZeptoBars, CC BY 3.0, via Wikimedia Commons.*

---

## The whole idea in 60 seconds

A gyroscope measures **how fast something is rotating** (degrees per second). Old gyros did this with a heavy spinning wheel; a MEMS gyro does it with a microscopic block of silicon, the **proof mass**, held on tiny springs and kept **vibrating** back and forth thousands of times a second. When the chip rotates, the **Coriolis effect** (the same apparent force that makes a ball rolled across a spinning merry-go-round seem to curve) pushes the vibrating mass **sideways, at 90° to its vibration**, with a force proportional to the rotation rate: F = −2m(Ω × v). That force is only about **2 nanonewtons**, and it moves the mass **less than a nanometre**, so the chip measures it as an **attofarad-sized change in capacitance** between the mass and fixed comb-shaped electrodes. Electronics turn that into a number in °/s. Two masses vibrating in opposite directions (**tuning fork**) let the chip ignore bumps. The whole thing is etched from silicon with chip-making tools, thousands per wafer, which is why it is tiny, cheap and inside phones, cars and drones. Its weakness is **drift**: small errors pile up when you integrate rate into angle, so it is combined with an accelerometer and magnetometer (**sensor fusion**).

---

## Reading order

| # | Doc | What you'll learn | Time |
| --- | --- | --- | --- |
| 01 | [Rotation basics](01_rotation_basics.md) | Angular rate, °/s vs rad/s, roll/pitch/yaw, accelerometer vs gyro | 15 min |
| 02 | [What is MEMS](02_what_is_mems.md) | The acronym, the sizes, MEMS in a phone | 10 min |
| 03 | [History: big to small](03_history_big_to_small.md) | Spinning wheels → Apollo IMU → a 3 mm chip | 10 min |
| 04 | [The Coriolis effect](04_coriolis_effect.md) | Merry-go-round, F = −2m(Ω × v), cross product, the 2 nN estimate | 25 min |
| 05 | [Vibrating gyro principle](05_vibrating_gyro_principle.md) | Drive and sense modes, why 90°, the 6 animation steps | 20 min |
| 06 | [Capacitive sensing](06_capacitive_sensing.md) | C = ε₀A/d, ΔC ≈ 2C₀·y/d, comb fingers, signal chain | 20 min |
| 07 | [Tuning fork](07_tuning_fork.md) | Anti-phase masses, rejecting shock | 10 min |
| 08 | [Ring resonators](08_ring_resonators.md) | Wine-glass modes, Bryan 1890, closed loop | 15 min |
| 09 | [Fabrication](09_fabrication.md) | Deposit, pattern, DRIE etch, release, vacuum cap | 15 min |
| 10 | [Types of gyroscopes](10_types_of_gyroscopes.md) | Mechanical, RLG, FOG, HRG, MEMS; bias-stability chart | 15 min |
| 11 | [Applications](11_applications.md) | OIS, AR/VR, ESC, rollover, drones, dead reckoning, Mars | 15 min |
| 12 | [Performance challenges](12_performance_challenges.md) | ARW, bias drift, temperature, Allan deviation plot | 20 min |
| 13 | [Sensor fusion and future](13_sensor_fusion_future.md) | Complementary filter with numbers, Kalman, what's next | 15 min |
| 14 | [Glossary](14_glossary.md) | Every term, A–Z | reference |
| 15 | [Likely questions](15_likely_questions.md) | 35 questions with short answers | 20 min |

**If you only have one hour:** read the 60-second summary above, then 04, 05 and 15.

**Note on order:** these docs follow the deck's order, except that doc 01 (slide 3: accelerometer vs gyro) comes before doc 02 (slide 2: what is MEMS), because you need to know what a gyro measures before anything else makes sense.

Every doc ends with **Key points to remember**, **Which slide uses this**, and **self-check questions** with hidden answers (click "Answers").

---

## Slide → doc map

| Slide | Title on the slide | Read |
| --- | --- | --- |
| 1 | MEMS Gyroscopes (title, MPU-6050 die photo) | 00, [02](02_what_is_mems.md) |
| 2 | MEMS: tiny machines built on a silicon chip | [02](02_what_is_mems.md) |
| 3 | One sensor for linear motion, one for rotation | [01](01_rotation_basics.md) |
| 4 | The same job, now on a 3 mm chip | [03](03_history_big_to_small.md) |
| 5 | Rotation pushes a moving mass sideways | [04](04_coriolis_effect.md) |
| 6 | Rotate a vibrating mass and it moves at 90° | [05](05_vibrating_gyro_principle.md) |
| 7–12 | Watch the Coriolis effect inside a MEMS gyroscope (steps 1–6) | [05](05_vibrating_gyro_principle.md) §3 |
| 13 | Tiny gap changes become an electrical signal | [06](06_capacitive_sensing.md) |
| 14 | Two masses in opposition: sense rotation, reject shock | [07](07_tuning_fork.md) |
| 15 | Ring resonators: rotation shifts the vibration pattern | [08](08_ring_resonators.md) |
| 16 | Built layer by layer, then set free | [09](09_fabrication.md) |
| 17 | MEMS trades precision for size, power and cost | [10](10_types_of_gyroscopes.md) |
| 18 | Every smartphone carries a gyroscope | [11](11_applications.md) Part A |
| 19 | Yaw-rate gyroscopes keep cars on the road | [11](11_applications.md) Part B |
| 20 | Navigating where GPS cannot reach | [11](11_applications.md) Part C |
| 21 | Small errors add up: noise and drift | [12](12_performance_challenges.md) |
| 22 | Combine sensors so each covers another's weakness | [13](13_sensor_fusion_future.md) |
| 23 | References | Sources sections at the bottom of each doc |
| 24 | Thank you · Questions are welcome | [15](15_likely_questions.md) |

---

## Things to double-check before presenting

- **Slide 4, "≈ 1.2 billion" smartphones per year:** an unverified estimate. Check a current source or say "over a billion". ([03](03_history_big_to_small.md))
- **Slides 4 and 18, "each/every smartphone has a gyro":** most do, not all. Say "most". ([02](02_what_is_mems.md), [11](11_applications.md))
- **Slide 5 merry-go-round drawing:** the curve direction doesn't match the clockwise arrow. Know the rule. ([04](04_coriolis_effect.md))
- **Slide 22, "navigation-grade MEMS (< 0.1 °/h)":** slide 21 calls navigation grade 0.01 °/h. Say "approaching navigation grade". ([13](13_sensor_fusion_future.md))

---

## Key points to remember

- A gyroscope measures **rotation rate** (°/s), not angle.
- A MEMS gyro **vibrates** a tiny proof mass; rotation adds a **Coriolis** push at **90°**, proportional to Ω.
- The push is tiny (**≈ 2 nN**, **< 1 nm**), read as an **attofarad** capacitance change.
- MEMS is **small, cheap and rugged** but **drifts**, so it is **fused** with other sensors.

**Which slide uses this:** The whole deck; the slide → doc map above tells you where each slide is covered.

## Self-check

1. In one sentence, what does a MEMS gyroscope measure and with what physical effect?
2. Why does the proof mass have to keep vibrating?
3. What is the main weakness of a MEMS gyro, and how is it handled?

<details>
<summary>Answers</summary>

1. It measures rotation rate (°/s) using the Coriolis force on a vibrating proof mass.
2. The Coriolis force acts only on a mass that is moving relative to the rotating chip (F ∝ Ω × v; if v = 0, F = 0).
3. Drift: bias and noise add up when the rate is integrated into an angle. It is handled by sensor fusion with an accelerometer and magnetometer (complementary or Kalman filter).

</details>

---

## Image credits

Diagrams and animation frames in `img/` (axes, scale, merry, threeStep, anim_step1–6, capacitor, tuningFork, ring, process, fog, esc, allan) were made by the team for the deck. Photos are from Wikimedia Commons, as credited on the deck's References slide:

| File | Credit |
| --- | --- |
| `photo_mpu6050_die.jpg` | MPU-6050 die: ZeptoBars, CC BY 3.0 |
| `photo_l3g4200d_board.jpg` | L3G4200D board: SparkFun Electronics, CC BY 2.0 |
| `photo_lsm9ds1_board.jpg` | LSM9DS1 board: SparkFun Electronics, CC BY 2.0 |
| `photo_apollo_imu.jpg` | Apollo IMU: ArnoldReinhold, CC BY-SA 4.0 |
| `photo_tuning_fork_sem.jpg` | Tuning-fork gyroscope SEM: M. N. Nguyen et al., CC BY 4.0 |
| `photo_disk_resonator_gyro.jpg` | Disk resonator gyroscope: D. Xia et al., CC BY 4.0 |
| `photo_drie_pillar.jpg` | DRIE pillar SEM: Pgalajda, public domain |
