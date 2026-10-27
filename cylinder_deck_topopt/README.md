# Cylinder-constrained 3D deck topology optimization

This folder contains a modified version of the supplied PINN/SIMP deck optimizer.

- A centered square lattice of fixed cylinder centers is placed on the deck plan (x-z).
- Each cylinder extends through the deck thickness. Its inner diameter is fixed at zero; only the outer radius is optimized.
- A sigmoid-bounded radius parameter limits the radius. The default minimum material web between adjacent cylinders is 12 mm, and edge clearance is 15 mm, subject to the available deck boundary.
- The original displacement network, hard simply-supported displacement ansatz, linear-elastic strain energy, SIMP interpolation, collocation grid, loading convention, and support constraints are retained.
- Outputs include a top-view PNG, 3D topology PNG when extractable, and an NPZ export of the sampled density and cylinder geometry.

Use the local `cylinder_deck_topopt.zip` from this conversation for the complete runnable package. Install dependencies from `requirements.txt`, then run `python 3D.py` from the extracted folder. Training uses the existing long-running defaults.

Important: a zero radius has zero useful geometric sensitivity, so the optimizer uses a tiny positive seed (effectively zero at grid scale). The differentiable density transition is a numerical device. This model is a research prototype, not a validated bridge design; verify mesh convergence, stresses, fatigue, shear effects, web manufacturability, and physical loading before engineering use.
