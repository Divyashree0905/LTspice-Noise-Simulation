# LTspice-Noise-Simulation

**Op-Amp Used:** LT6200  
*(Ultra-low noise, rail-to-rail, unity gain stable op-amp)*

---

## ✍️ Why I Chose This Project

I picked this project because I’ve always been curious about how noise affects real-world circuits—especially when working with op-amps. I wanted to understand not just *what* noise is, but *where* it comes from and how we can analyze or reduce it. LTspice seemed like the perfect tool to dig into this without needing lab equipment.

---

## 📚 What I Learned

- How to use LTspice's noise simulation features step by step  
- What flicker noise is, and how it shows up in low frequencies  
- That resistors and op-amps both contribute to total noise—and you can isolate them  
- How to measure **input-referred** vs **output** noise  
- Overall, I now feel more confident analyzing and optimizing circuits for low-noise design

---

## 🛠️ Basic Setup

### Circuit:
- Non-inverting amplifier
- Gain = 10× (aka 20 dB)

### AC Analysis:
- Shows 20 dB gain
- -3 dB point is around 16.5 MHz

---

## 🧪 How to Set Up Noise Simulation

1. **Open Noise Sim Settings:**
   - Go to `Simulate > Edit Simulation Cmd`, or right-click an existing sim box
   - Choose the **Noise** tab

2. **Set These Parameters:**
   - Sweep Type: `Decade`
   - Points per Decade: `100`
   - Start Freq: `100 Hz` (to see flicker noise)
   - Stop Freq: Something high enough to show the roll-off

3. **Input / Output:**
   - **Input:** Name of the voltage source (like `VN`)
   - **Output:** Voltage node you want to observe (e.g. `V(Vout)`)

4. **Run It:**
   - Just click the run button or right-click the schematic and hit `Run`

---

## 📊 Checking Out the Results

- Hover over the output node and click → you’ll see the noise graph
- **At low frequencies**: You’ll notice flicker noise
- **At high frequencies**: Noise rolls off
- Hovering over other random nodes = just shows DC values (not helpful here)
- Clicking resistors = shows how much noise *that* resistor adds

---

## 🧠 Some Observations

| Component        | Noise Behavior                              |
|------------------|----------------------------------------------|
| Rf (feedback resistor)| Higher value but adds less noise overall  |
| Rg (input resistor)| Adds more noise (gets amplified by the gain) |

---

## 🧼 If You Only Want Op-Amp Noise

- Right-click each resistor and add `noiseless` after its value
- Run again → resistor noise will be gone, so you just get the op-amp's contribution

---

## ➕ Extra Traces You Can Add

Right-click the waveform → “Add Trace” → pick any of these:

- `V(onoise)` → total output noise
- `Vr(Rf)` or `Vr(Rg)` → noise from those resistors
- `Gain` → your amplifier gain curve (no phase though)
- `I(noise)` → input-referred noise (basically: output noise / gain)

---

## 💭 Final Thoughts

LTspice makes it *really* easy to see where your noise is coming from.  
You can break it down by each resistor or just focus on the op-amp.

Super helpful when you're designing something sensitive and need to keep noise low.
