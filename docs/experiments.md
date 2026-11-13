# 🧪 Experiments to try

Short guided experiments. Each one isolates a single idea from rocket design. Start every experiment from the **default rocket** (press **Reset** and reload the page). Use the faded traces of earlier runs to compare flights side by side.

---

## 1. Thrust-to-weight ratio: the liftoff threshold

**Do:** Select Stage 1 and lower the thrust until the S1 TWR shown under the sliders drops below 1. Launch.

**Expect:** The rocket never leaves the pad: "STUCK ON PAD".

**Then:** Try a TWR of 1.1, then 1.7 (the default), then 3.0. Compare the apogees.

**Question:** Why does a TWR just above 1 give such a poor flight, even though the Δv barely changes? *(Hint: gravity loss ≈ g × burn time.)*

---

## 2. Why stage at all?

**Do:**
1. Launch the default two-stage rocket and note the apogee (about 392 km).
2. Remove Stage 2. On Stage 1, set dry mass to 1250 kg and fuel mass to 2850 kg. The total mass and propellant are now the same as the two-stage version.
3. Launch again.

**Expect:** An apogee of about 150 km, less than half.

**Question:** Use `Δv = Isp·g₀·ln(m₀/m_f)` to explain the difference by hand.

---

## 3. Isp: the cheapest performance you can buy

**Do:** Raise Stage 2's Isp from 250 s to 350 s. Change nothing else.

**Observe:** The total ideal Δv shown under the sliders and the apogee.

**Question:** Isp went up by 40%. Did the apogee go up by more or less than 40%? *(Hint: coasting height ≈ v²/2g. What happens to a squared quantity?)*

---

## 4. Drag losses

**Do:** Set Cd to 0.10 (the minimum) and launch. Then set the body diameter to 2.0 m with Cd at 0.5 and launch.

**Observe:** The burnout velocity in the flight log, and Max Q.

**Question:** Which matters more for drag: diameter or Cd? Look at how each one appears in `D = ½ρv²CdA`.

---

## 5. Find Max Q

**Do:** Launch at 1× time warp and watch for the red **MAX Q** flag (about T+50 s).

**Question:** Speed keeps rising after Max Q, so why does dynamic pressure fall? Sketch `q = ½ρv²` with `ρ` falling exponentially.

---

## 6. Payload trade-off

**Do:** Raise the payload from 100 kg to 300 kg, then 600 kg. Record the apogee each time.

**Plot:** Apogee against payload. Is it linear?

---

## 7. Escape velocity challenge 🌌

**Goal:** Get the status to read **ESCAPED EARTH**.

**Hint:** You need about 11 km/s *after* losses. Use three stages, high Isp on the upper stages (400+ s), low payload, a slim body and low Cd. Watch the total Δv shown under the sliders. You'll need well over 11 km/s.

**Question:** How much total Δv did your design need, and how much was lost to gravity and drag?

---

## Record template

| Run | Change made | Total Δv (km/s) | Burnout v (m/s) | Max Q (kPa) | Apogee (km) |
|---|---|---|---|---|---|
| 1 | Default | 3.94 | 2064 | 38.8 | 392 |
| 2 | | | | | |
| 3 | | | | | |
