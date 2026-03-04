# Discrete Air-Flow Simulation

## Description
Most explanations of airflow use a continuous calculus-based approach that abstracts away what the air is actually doing. The explanation that air flows faster over the top edge of an airfoil does not explain _why_ the air behaves that way. 
What is far more intuitive is a discrete approach based on the movement of individual particles. This project will implement a discrete particle simulation designed for an aerospace museum kiosk. The simulation will clearly demonstrate the Coanda Effect, Pressure Voids, and Sonic Booms in a way that is emergent from a few simple principles.

## Physics Outline
This engine will use a Step-and-Resolve approach:
- **Discrete Interaction**: Air particles are treated as individual entities. An air particle will step in the direction of its velocity, then be accelerated toward any near low pressure regions. This, combined with collision response, will result in particles hugging objects to avoid vacuums (The Coanda Effect).
- **Lift Calculation**: The list is calculated through a particle counter system that measures the density differential between the upper and lower surfaces of an object.
- **Signal Latency (Sonic Boom)**: The speed of sound is modeled as the propagation delay of repulsive forces between particles. When the particle is moving faster than the other particles can get out of the way, they will stack up and produce a shockwave.

##  Tech Stack
- **Language**: C++ for performance
- **Graphics**: Raylib (using `PLATFORM_DRM` for native Linux frame-buffer rendering)
- **Deployment**: Dockerized environment for cross-compilation (x86_64 to ARM64)
- **Target Hardware**: Raspberry Pi (locked down Kiosk Mode)
  - TODO: determine required specs
 
## Next Steps:
- Determine how pressure regions will work
  - Consider: Separate the screen into a grid where each cell has a particle count. Compare to neighbors to create a pressure gradient.
- Develop Sim Architecture
- Outline Vertical Slice Dev Roadmap
- Begin Protyping
