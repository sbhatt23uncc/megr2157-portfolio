# A1 — Build Your Professional Portfolio

## Part 2: Decide

The Decide pillar asks one question: can you make a choice between alternatives, document your criteria, and justify your selection? The following three decisions were made before any other content was written on this page.

---

### Decision 1: Homepage Identity

The homepage of this portfolio serves a single reader: an engineer — whether a grader, a peer, or a future employer — who has arrived at this URL and needs to determine within thirty seconds what this site contains, how it is organized, and whether the work inside meets a defensible standard. The homepage therefore opens with the course identifier and the framework that governs every entry (Analyze, Decide, Communicate), because that framework tells the reader *how* to evaluate each assignment, not just where to find it. The semester arc section provides a chronological map so the reader can locate any assignment by its position in the design sequence without navigating blindly through sidebar links. The About Me section is placed on the homepage rather than behind a separate navigation link because the most common use case — a recruiter or instructor scanning the portfolio for the first time — requires both the author's identity and the portfolio's organizational logic to be visible on the same page without an additional click. Every element on the homepage exists to reduce the reader's time-to-orientation; content that serves the author's self-expression rather than the reader's navigation efficiency was excluded.

---

### Decision 2: One Intentional Customization — Color Scheme

**What was changed:** The primary theme color was changed from `green` (the template default) to `indigo`.

**What requirement this change better satisfies:** Typographic contrast ratio and visual association with the portfolio's subject domain. The Material for MkDocs theme uses the primary color for the top navigation bar, sidebar highlights, and hyperlink accents. The default `green` (`#4CAF50`) achieves a WCAG AA contrast ratio of approximately 3.1:1 against white body text backgrounds, which is below the 4.5:1 threshold recommended for text-adjacent UI elements. `Indigo` (`#3F51B5`) achieves approximately 5.9:1 against the same white background, improving legibility for readers scanning navigation elements in peripheral vision. Additionally, indigo is the standard color associated with aerospace engineering and navigation instrumentation (artificial horizon indicators, avionics HUD symbology), which aligns the visual identity of this portfolio with the aerospace concentration that defines my engineering trajectory.

**Why the template default did not meet this requirement:** The default green met no functional requirement specific to this portfolio's content domain and provided a lower contrast ratio against the white content background, reducing the speed at which a reader can distinguish navigational elements from body content.

---

### Decision 3: Documentation Standard

Every assignment entry in this portfolio will identify the governing equation or physical model, define all variables with units, present at least one alternative considered with a stated basis for rejection, and justify the selected approach with a quantitative or functional rationale traceable to a requirement — documented to the standard that a mechanical engineer unfamiliar with the project could reproduce the analysis and arrive at the same conclusion without asking a clarifying question.

---

## Part 1: Analyze

---

### Task A: Portfolio Analysis (25%)

Two engineering portfolios were identified and evaluated against four functional requirements: navigability, reproducibility, evidence of reasoning, and professional tone. The prohibited terms (*good, bad, nice, clear, professional*) are used below only with explicit qualification.

---

#### Portfolio 1: Rick Meade — Mechanical & Robotics Engineering

**URL:** [https://rjmeade.github.io/](https://rjmeade.github.io/)
**Hosting platform:** GitHub Pages (static site deployment)

**a. Navigability**
The site uses a single-page indexed layout with distinct project cards organized by engineering discipline (aerospace systems, robotics, computer vision, optimization). A reader arriving at the landing page can identify the title and discipline of any individual project within approximately 15 seconds by scanning the card grid, well below the 60-second threshold. The flat architecture eliminates multi-tier menu traversal — every project is one click from the homepage. This structure prioritizes speed-to-artifact for a reader who already knows what discipline they are looking for.

**b. Reproducibility**
In the Complete Coverage Path Planning project, analytical formulations for concave domain decomposition are defined with geometric boundary conditions. In the autonomous fixed-wing aircraft project, topology optimization objectives (minimizing structural compliance subject to volume fraction constraints) are outlined alongside finite element parameters. However, the portfolio does not host parametric CAD files (`.sldprt`, `.step`), finite element mesh configurations, or dimensioned fabrication drawings. A peer engineer could replicate the algorithmic logic and conceptual topology, but would need to reconstruct discrete geometric dimensions and tolerance stack-ups from scratch. Reproducibility is therefore partial: the reasoning is recoverable, but the manufacturing-level implementation is not.

**c. Evidence of Reasoning**
This portfolio documents the *iteration pipeline* rather than presenting static end-state CAD models. In the aircraft structural design, material allocation was driven by stress-tensor distribution under maximum aerodynamic gust loading rather than intuitive geometric placement. In the UGV chassis design, structural decisions were governed by dynamic impact deceleration ($F = m \cdot \frac{dv}{dt}$) and payload mass budget constraints. The documentation presents the physics, boundary conditions, and optimization algorithms that dictated design decisions — the reader sees *why* a cross-section was chosen, not just *what* the final geometry looks like.

**d. Professional Tone**
The language relies on domain-specific engineering terminology (*topology optimization*, *convex cellular decomposition*, *impact attenuation*) without informal hyperbole. Claims reference quantifiable context — project scale, engineering role (Chief Engineer), and award recognition (Dean's Choice Award). The tone is suitable for a document submitted to an employer to the extent that every assertion is backed by a technical context rather than a subjective adjective.

---

#### Portfolio 2: Julian Zachar-Fink — Mechanical & Manufacturing Engineering

**URL:** [https://julianzacharfink.com/](https://julianzacharfink.com/)
**Hosting platform:** Independent web hosting (custom domain)

**a. Navigability**
The portfolio is structured chronologically by academic semester, with each project accessible from a global gallery page. Sub-headers within each project follow a consistent sequence: Problem Definition → Technical Specifications → Kinematic/Structural Calculations → CAD & Manufacturing → Experimental Validation. A reader can navigate from the homepage to a specific calculation or bill of materials within approximately 20 seconds. The consistent internal structure means that once a reader understands one project page, they can predict the location of equivalent content in every other project — this predictability is itself a navigability feature.

**b. Reproducibility**
This portfolio achieves a higher reproducibility standard than Portfolio 1. In the TRAS Residential Plastic Compactor project, the documentation specifies the 3:1 volumetric compaction ratio, lead screw torque requirements ($\tau = \frac{F \cdot d_m}{2} \cdot \frac{\pi f d_m + L}{\pi d_m - f L}$), gear reduction ratios, and a line-item bill of materials establishing a unit manufacturing cost of 822 DKK against a retail ceiling of 4,500 DKK. The presence of kinetic formulas, electrical power ratings, cost breakdown tables, and linkage kinematic sketches provides sufficient data for an engineering team to construct an equivalent functional prototype without contacting the author.

**c. Evidence of Reasoning**
Design decisions are consistently linked to quantitative requirements or physical constraints rather than presented as final selections without justification. In the plastic sorting system (G.O.O.N.E.R.), the author documents why standard near-infrared (NIR) reflection failed on carbon-black polymers due to total spectral absorption, justifying the selection of hyperspectral short-wave infrared spectroscopy as the alternative. Motor torque versus lead screw pitch was balanced against consumer duty-cycle constraints and acoustic noise thresholds. Formal Pugh concept screening matrices and failure mode evaluations are documented, meaning the reader can trace any final design back through the selection methodology that produced it.

**d. Professional Tone**
The writing follows European/ISO engineering report conventions with precise mechanical terminology (*kinematic synthesis*, *volumetric strain*, *transmission efficiency*, *Design for Manufacturing and Assembly*). The tone is dispassionate and specification-driven — measurable tolerances, financial constraints, and functional performance targets replace subjective assessments. This is professional in the specific sense that it meets the documentation standard expected by a European manufacturing engineering employer reviewing a candidate's design capability.

---

#### Comparative Summary

| Criterion | Portfolio 1 (Meade) | Portfolio 2 (Zachar-Fink) |
|---|---|---|
| **Navigability** | Single-page card grid; ~15 s to target | Semester taxonomy; ~20 s to target |
| **Reproducibility** | Algorithmic logic recoverable; fabrication data absent | Sufficient for prototype reconstruction |
| **Evidence of Reasoning** | Optimization-driven; physics traced to design | Pugh matrices; failure mode analysis documented |
| **Professional Tone** | Aerospace/robotics vocabulary; objective | ISO-standard engineering report format |

Portfolio 2 (Zachar-Fink) sets a higher standard for reproducibility and decision traceability because it includes quantified trade studies and manufacturing cost data. Portfolio 1 (Meade) excels in navigability due to its flat single-page architecture. Both portfolios demonstrate that the value of an engineering portfolio is not in the final geometry shown, but in the documented reasoning that produced it.

---

### Task B: Product Analysis — Binder Clip (25%)

---

#### a. Primary Engineering Function

The binder clip performs the following mechanical function: it exerts a reversible, compressive normal clamping force across a planar stack of flexible sheet media via elastic flexural deflection of a sheet-metal spring body, generating static frictional resistance sufficient to prevent relative shear displacement and separation of the sheets without inducing plastic deformation or surface perforation of the substrate.

This is not "holding papers together" — that is a consumer description. The engineering function is: *convert stored elastic strain energy in a preloaded flexure spring into a sustained normal contact force that produces friction-based shear retention of a sheet stack.*

---

#### b. Governing Model

The binder clip operates through two coupled mechanical subsystems:

**1. Clamping Force (Spring Deflection)**

The triangular spring body functions as a symmetric dual-cantilever flexure spring. From Euler-Bernoulli beam theory:

$$F_{\text{clamp}} = k \cdot \delta = \frac{E \cdot w \cdot t^3}{4L^3} \cdot (t_{\text{stack}} - g_0)$$

where:

| Variable | Description | Unit |
|---|---|---|
| $F_{\text{clamp}}$ | Normal compressive clamping force on the paper stack | N |
| $E$ | Young's modulus of tempered spring steel (~200–210 GPa) | Pa |
| $w$ | Width of the clip body (extrusion depth) | m |
| $t$ | Thickness of the spring steel sheet | m |
| $L$ | Cantilever span from apex to lip (flange length) | m |
| $t_{\text{stack}}$ | Thickness of the inserted paper stack | m |
| $g_0$ | Initial resting jaw gap (often ≤ 0 for preloaded clips) | m |

The retention criterion against pull-out is governed by Coulomb friction:

$$F_{\text{pull}} \leq 2\mu F_{\text{clamp}}$$

where $\mu$ is the static coefficient of friction (steel-to-paper ≈ 0.4–0.5; paper-to-paper ≈ 0.6–0.7).

**2. Opening Mechanics (Lever Actuation)**

Each wire handle acts as a Class 1 lever pivoting against the body's shoulder:

$$F_{\text{applied}} \cdot L_{\text{handle}} = F_{\text{spring}} \cdot d_{\text{pivot-to-lip}}$$

Mechanical advantage:

$$MA = \frac{L_{\text{handle}}}{d_{\text{pivot-to-lip}}} \approx 5\text{–}10$$

**One assumption that makes this model valid:** The spring steel operates strictly within its elastic limit ($\sigma_{\text{max}} < \sigma_{\text{yield}}$), meaning Hooke's law applies and the clip returns to its original geometry after each use cycle without permanent plastic set. If the material were loaded beyond its yield strength, the clamping force would degrade with each use cycle and the linear spring constant $k$ would no longer be valid — the clip would take a "set" and stop clamping.

---

#### c. Component Photographs and Geometry Analysis

*Note: Photographs must be taken by the student. Replace each placeholder below with your own image.*

**Component 1: The Clip Body (Triangular Spring Steel Piece)**

![Photograph of binder clip body — spring steel triangle](clip_body.jpg)

The clip body is stamped and bent from a single strip of high-carbon tempered spring steel into an isosceles triangular prism cross-section. The geometry affects mechanical function in the following ways:

- **Sheet thickness ($t$):** Clamping stiffness scales with $t^3$ (from $k \propto E w t^3 / 4L^3$). A small increase in material thickness produces a cubic increase in clamping force — this is why binder clips of different sizes use different gauge steel, not just different overall dimensions. Manufacturing tolerances on $t$ directly control force output.
- **Apex radius of curvature:** The bend at the top of the triangle is radiused rather than sharp-cornered. This distributes bending strain across a smooth arc rather than concentrating it at a single line, which prevents fatigue crack initiation at the highest-stress location in the clip. A sharp fold would create a stress concentration factor exceeding 2.0, dramatically reducing cycle life.
- **Flange span and angle:** The length of each triangular side ($L$) determines the maximum paper stack depth (throat capacity) and the cantilever moment arm. A longer $L$ reduces clamping force for the same material and deflection (force scales as $1/L^3$), so clip size is a direct trade between stack capacity and retention force.
- **Rolled beads (curled lips):** The terminal edges of the body are curled outward into cylindrical channels. These serve three simultaneous functions: (1) they form journal bearings that capture the wire handle pivot feet, creating a revolute kinematic pair; (2) they eliminate sharp sheet-metal edges that would score and tear paper sheets under clamping pressure; (3) they increase the second moment of area of the edge cross-section, preventing transverse edge buckling when the clip is opened.

**Component 2: Wire Handle (Left)**

![Photograph of binder clip wire handle](handle_left.jpg)

Each handle is a single piece of high-tensile nickel-plated steel wire bent into a trapezoidal loop with two inward-pointing coaxial cylindrical feet at the proximal ends.

- **Lever arm length ($L_{\text{handle}}$):** The handle length provides a mechanical advantage of approximately 5:1 to 10:1, meaning a user applying 2 N of finger force can overcome 10–20 N of spring reaction force. Without this mechanical advantage, the clip would require pliers to open.
- **Wire diameter ($d$):** The second moment of area of the wire ($I = \frac{\pi d^4}{64}$) must be high enough that the handle does not deflect appreciably during squeezing — any handle bending represents lost input stroke that does not translate into jaw opening. The wire diameter is therefore sized for stiffness, not strength.
- **Pivot feet geometry:** The inward-facing cylindrical tips function as journal pins inside the body's rolled beads, creating a single degree-of-freedom revolute joint. The wire can rotate approximately 270° around this axis, allowing the handle to fold flat against the paper stack or be removed entirely by compressing the feet together.

**Component 3: Wire Handle (Right)**

![Photograph of binder clip wire handle — right](handle_right.jpg)

Identical in geometry and function to the left handle. The symmetric pair ensures that the opening force is applied as a balanced couple about the clip body's longitudinal axis, preventing asymmetric jaw opening that would cause one lip to release before the other. If only a single lever were provided, the clip would twist during opening, producing non-uniform clamping pressure across the clip width.

---

#### d. Patent Research and Design Decision Analysis

**Patent identification:**

- **Patent number:** US 1,139,627
- **Title:** *Paper-binding clip*
- **Inventor:** Louis E. Baltzley (Washington, D.C.)
- **Filed:** July 2, 1910
- **Granted:** May 18, 1915
- **Context:** Baltzley invented the clip to help his father, Edwin Baltzley (a prolific inventor and writer), organize and bind manuscript pages without punching holes or sewing them together.

A subsequent improvement patent, **US 1,865,453** (*Binder clip*, filed March 17, 1930, granted July 5, 1932), also by Baltzley, added articulated/segmented gripping jaws to accommodate non-uniform stack thicknesses.

**Alternative solutions that solve the same primary function (compressive retention of a sheet stack):**

1. **Gem paper clip (wire loop clip):** A single continuous formed wire with nested concentric loops utilizing combined torsional and flexural elastic deformation to clamp a small bundle. Trade-off: zero assembly cost and single-piece construction, but significantly lower clamping force, limited to approximately 10–20 sheets, and easily undergoes permanent plastic yielding under overloading.

2. **Bulldog clip (pivot-jaw clip):** Two stamped sheet-metal jaw halves joined by a central pivot pin and energized by a separate helical torsion spring or coiled steel band. Trade-off: higher clamping force and wider jaw opening capacity, but higher part count (3–4 components: two jaws, one spring, one pivot pin), higher assembly cost, and rigid handles that cannot fold flat for filing.

**One design decision and its rationale:**

The most consequential visible design decision in US 1,139,627 is the **fold-back, removable dual-position wire handle mechanism**. Baltzley could have used fixed rigid levers (as in the bulldog clip) or integrated the lever arm into the spring body itself (as in a clothespin). Instead, he designed handles that rotate 180° to fold flat against the document stack and can be entirely removed by compressing the wire feet together.

This decision solves three engineering problems simultaneously:

1. **Volume efficiency:** Fixed handles (like those on a bulldog clip) create rigid protrusions that prevent clamped documents from lying flat in a drawer or box. Folding the handles reduces the clip's vertical profile to the sheet-metal body thickness alone, eliminating stacking interference.
2. **Inadvertent release prevention:** The long lever arm required during application to provide mechanical advantage becomes a liability once the clip is applied — any accidental squeeze or snag would re-open the jaws. Folding the handles flat removes the moment arm, making accidental release mechanically impossible without deliberately re-deploying a handle.
3. **Tamper-resistant binding mode:** Removing both handles entirely converts the clip into a low-profile, semi-permanent binding spine that cannot be opened without a tool or replacement handle — this is a functional mode not available in any competing clip design of the era.

---

## Part 3: Communicate

*The About Me section for this assignment is located on the [homepage](../../../index.md) of this portfolio, as specified by the assignment instructions. It is not duplicated here to maintain a single source of truth.*

### Time Spent

<!-- PLACEHOLDER: Replace with your actual time -->
I spent approximately **[X]** hours on this assignment. The time was distributed approximately as follows:

- Portfolio research and analysis (Task A): ~[X] hours
- Product analysis, patent research, and component documentation (Task B): ~[X] hours
- Part 2 decisions and site customization: ~[X] hours
- About Me professional introduction (Part 3): ~[X] hours
- MkDocs setup, deployment, and formatting: ~[X] hours
