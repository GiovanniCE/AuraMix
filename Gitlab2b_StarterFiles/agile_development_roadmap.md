# AuraMix: 8-Week Development Roadmap

## Sprint 1: The Data Pipeline (Weeks 1–2)

**Goal:** Establish the "Wired Bridge" between the Quest 3, the DDJ-FLX4, and your PC.

- [ ] **Unity Setup:** Configure a project with the OpenXR and Meta Movement SDK.
- [ ] **Hardware Handshake:** Get the Quest 3 to recognize the FLX4 via USB-C using Unity’s Input System or MidiJack.
- [ ] **The Logic:** Write a basic C# script that prints a "Hello World" message to the console every time you move a fader or press a button on the controller.

**Deliverable:** A functional (but invisible) bridge where hardware actions trigger events in Unity.

## Sprint 2: Body Mapping & OSC (Weeks 3–4)

**Goal:** Translate your physical movement into musical data.

- [ ] **Skeletal Access:** Implement the Meta Movement SDK to track hand and arm positions.
- [ ] **The "Mapping Engine":** Create a script to normalize XYZ coordinates into a 0.0−1.0 float range.
- [ ] **OSC Out:** Setup OSC Jack to send that normalized data out of the headset to your laptop.
- [ ] **DAW Integration:** Map a hand-raise movement to a "Filter Cutoff" in Rekordbox or Ableton.

**Deliverable:** You can now change the music by waving your hands in the air.

## Sprint 3: The AR Interface & Passthrough (Weeks 5–6)

**Goal:** Build the "Heads-Up Display" (HUD).

- [ ] **Passthrough Integration:** Enable Mixed Reality so you can see your physical hands and the FLX4 while wearing the headset.
- [ ] **Spatial UI:** Design the floating waveforms and holographic effect racks.
- [ ] **Anchor Logic:** Use Spatial Anchors to "pin" the AR UI to your physical DJ controller so it doesn't drift when you move your head.

**Deliverable:** A visual overlay that stays locked to your DJ booth.

## Sprint 4: Visual Polish & Performance Testing (Weeks 7–8)

**Goal:** Make it look "Pro" and ensure stability.

- [ ] **Reactive Visuals:** Add shaders and particle effects that pulse to the beat (using audio-reactive triggers).
- [ ] **Latency Stress Test:** Optimize the code to ensure there is no "lag" between a hand movement and the sound changing.
- [ ] **Presentation Prep:** Record a demo video of you performing a 2-minute set with the AR overlays active.

**Deliverable:** A polished, showcase-ready build for your final class presentation.