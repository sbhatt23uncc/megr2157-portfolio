## A1 - Building Your Professional Portfolio

## Objective

To build a professional engineering portfolio hosted on GitHub Pages using MkDocs, and to practice the Analyze, Decide, and Communicate framework through portfolio analysis, product analysis, and documented design decisions.

## Decide

### Decision 1: Homepage Identity

The homepage of this portfolio is written for someone visiting for the first time, whether that is a grader, a classmate, or a future employer. It opens with the course name and the Analyze/Decide/Communicate framework because that tells the reader how each assignment is structured, not just where to find them. The semester arc section gives a quick map of how assignments build on each other so the reader does not have to click through every sidebar link to understand the progression. Everything on the homepage is there to help the reader orient themselves faster, and anything that only served my own self-expression was left out. The About Me page covers who I am. The homepage covers what this portfolio is and how it works.

### Decision 2: One Intentional Customization

I changed the primary theme color from the template default of green to indigo in the mkdocs.yml configuration file. The Material for MkDocs theme uses the primary color for the top navigation bar, sidebar highlights, and link accents. The default green has a WCAG contrast ratio of roughly 3.1:1 against the white content background, which falls below the 4.5:1 recommendation for text-adjacent UI elements. Indigo achieves about 5.9:1 against the same background, making navigation elements easier to pick out at a glance when scanning the page. On top of the contrast improvement, indigo is a color commonly associated with aerospace instrumentation and avionics displays, which fits the focus of my engineering work better than a generic green that has no connection to the content of this portfolio.

### Decision 3: Documentation Standard

Every entry in this portfolio will state the governing equation or model, define all variables with units, present at least one alternative that was considered with a reason for its rejection, and justify the final selection with a rationale tied to a stated requirement, all documented so that another engineer could reproduce the analysis without asking me a question.

## Analyze

### Task A - Analyzing Portfolios

**Portfolio #1** - [https://rjmeade.github.io/](https://rjmeade.github.io/)

**A. Navigability:** The site uses a single-page layout with project cards sorted by discipline (aerospace, robotics, optimization). Every project is one click from the landing page. A visitor scanning for a specific project can find it in about 15 seconds without digging through nested menus, which is well under the 60-second threshold.

**B. Reproducibility:** Some projects include analytical formulations and optimization parameters. The path planning project defines geometric boundary conditions, and the aircraft project outlines topology optimization objectives like minimizing compliance under volume fraction constraints. However, there are no downloadable CAD files, mesh configurations, or dimensioned drawings. A reader could follow the reasoning and replicate the logic, but they would have to rebuild the geometry from scratch to actually fabricate anything.

**C. Evidence of Reasoning:** This is where the portfolio does well. Instead of just showing finished CAD models, it walks through the iteration process. The aircraft structure was shaped by stress distributions under gust loading rather than by guessing at shapes. The UGV chassis design traces back to impact deceleration equations and mass budgets. You can see why each design looks the way it does, not just what the final result is.

**D. Professional Tone:** The writing uses domain-specific terms like topology optimization, convex cellular decomposition, and impact attenuation without filler or hype. Claims are supported by context like project scope and engineering roles held. It reads like something you could hand to an employer without needing to edit it first.

**Portfolio #2** - [https://julianzacharfink.com/](https://julianzacharfink.com/)

**A. Navigability:** Projects are organized by semester with a consistent internal structure that goes Problem Definition, then Technical Specs, then Calculations, then CAD/Manufacturing, then Validation. Once you learn the layout of one project page, you can predict where to find equivalent content in every other project. Time to locate a specific calculation or bill of materials is about 20 seconds.

**B. Reproducibility:** This portfolio sets a higher bar than Portfolio 1. The plastic compactor project includes a 3:1 compaction ratio, lead screw torque calculations, gear ratios, and a full bill of materials with unit costs. Between the kinematic sketches, power ratings, and cost breakdowns, a team could build a working prototype from this documentation alone without contacting the author.

**C. Evidence of Reasoning:** Every design choice traces back to a constraint or trade study. The sorting system project explains why standard NIR sensing failed on carbon-black plastics due to total absorption, which justified switching to short-wave infrared spectroscopy. Motor selection was balanced against duty cycle limits and noise requirements. Pugh matrices and failure mode analyses are included, so you can follow the full decision chain from requirements to the final design.

**D. Professional Tone:** Written in a formal engineering report style with precise terminology like kinematic synthesis, transmission efficiency, and Design for Manufacturing and Assembly. The language is focused on specs, tolerances, and constraints rather than subjective opinions. It meets the standard of a document you would submit to an employer in the sense that every claim is backed by data or a stated constraint rather than a personal preference.

### Task B - Product Analysis

**Product:** Binder Clip

**Patent:** [US 1,139,627](https://patents.google.com/patent/US1139627A/en) - "Paper-binding clip"

**Inventor:** Louis E. Baltzley (Washington, D.C.)

**Filed:** July 2, 1910 | **Granted:** May 18, 1915

Baltzley invented the clip to help his father, a writer, organize manuscript pages without punching holes or sewing them together.

**A.** The binder clip converts stored elastic strain energy in a preloaded sheet-metal flexure spring into a sustained compressive normal force across a stack of paper. That normal force generates enough static friction between the sheets and between the steel and paper surfaces to prevent the sheets from sliding apart or separating. It does this without punching holes, tearing, or permanently deforming the paper. The engineering function is force transmission through elastic deflection to produce friction-based retention of a planar sheet stack.

**B.** The governing model is Hooke's Law applied to a flexure spring. The triangular body of the clip acts as a symmetric dual-cantilever beam, and the clamping force depends on how far the jaws are spread apart by the paper stack. From Euler-Bernoulli beam theory, the clamping force is proportional to the Young's modulus of the spring steel, the width of the clip body, the cube of the steel thickness, and the deflection of the jaws, and it is inversely proportional to the cube of the flange length. The key variables are the clamping force in Newtons, the Young's modulus of tempered spring steel (about 200 GPa), the steel sheet thickness, the clip width, the flange length from apex to lip, and the paper stack thickness.

For the clip to hold the paper in place, the friction force must exceed any pull-out force. This is governed by Coulomb's friction law, where the friction force equals the coefficient of static friction (about 0.4 to 0.5 for steel on paper) multiplied by the clamping force.

The wire handles work as Class 1 levers that pivot against the body. The mechanical advantage is roughly 5:1 to 10:1, which is why you can open a clip that exerts over 10 N of clamping force with just a couple newtons of finger pressure.

One assumption that makes this model valid is that the spring steel stays within its elastic limit. If the material yielded plastically, the clip would take a permanent set and gradually lose clamping force with each use cycle. Hooke's Law only holds when the stress remains below the yield strength of the material.

**C.** Photographs of each component:

**Component 1: Clip Body (Spring Steel Triangle)**

![Photograph of the binder clip body, a single piece of spring steel bent into a triangular shape](clip_body.jpg)

The body is stamped and bent from a single strip of high-carbon tempered spring steel into a triangular cross-section. The sheet thickness is the single most important geometric parameter because stiffness scales with the cube of thickness, so even a small change in gauge dramatically changes clamping force. This is why different clip sizes use different steel thicknesses, not just scaled-up dimensions. The bend at the top (the apex) is radiused rather than sharply folded. A sharp corner would create a stress concentration that accelerates fatigue cracking at the highest-stress point. The radius spreads bending strain over a wider arc. The length of each flange determines the throat depth (how much paper fits) but longer flanges also reduce clamping force because force is inversely proportional to the cube of the flange length. The edges at the bottom are curled outward into cylindrical channels. These serve three purposes at once: they act as journal bearings for the wire handle pivots, they prevent sharp steel edges from cutting the paper under clamping pressure, and they stiffen the edge to resist buckling when the clip is opened wide.

**Component 2: Wire Handle (Left)**

![Photograph of one of the binder clip wire handles, a bent steel wire loop](handle_left.jpg)

Each handle is a single piece of nickel-plated steel wire bent into a loop with inward-pointing cylindrical feet at the ends. The lever arm length provides the 5:1 to 10:1 mechanical advantage that makes the clip openable by hand. Without the handles, you would need pliers to pry the jaws apart. The wire diameter is sized for stiffness rather than strength because any bending in the handle during squeezing wastes motion that does not translate into jaw opening. The inward-pointing tips sit inside the body's curled lips and form a simple hinge joint that allows roughly 270 degrees of rotation, so the handles can fold flat against the paper stack.

**Component 3: Wire Handle (Right)**

![Photograph of the second binder clip wire handle, identical to the first](handle_right.jpg)

Identical to the left handle. Having two symmetric handles means the opening force acts as a balanced couple, so both jaws open evenly. If there were only a single handle, the clip would twist during opening and one side would release before the other, making it difficult to insert paper evenly.

**D.** Two alternative solutions that perform the same primary function of compressive retention of a sheet stack:

1. **Gem paper clip (wire loop clip):** A single continuous formed wire that uses torsional and flexural deflection to grip a small bundle. It is cheaper and simpler with zero assembly, but is limited to about 10-20 sheets and bends out of shape permanently under moderate force.

2. **Bulldog clip (pivot-jaw clip):** Two stamped jaw halves joined by a pivot pin with a separate torsion spring. It provides a stronger grip and wider jaw opening, but uses more parts (3-4 components), costs more to manufacture, and the rigid handles cannot fold flat for filing.

One design decision that stands out in the patent is the fold-back removable handle mechanism. Baltzley could have used fixed rigid handles like the bulldog clip or built the lever into the spring body itself like a clothespin. Instead, he designed handles that rotate 180 degrees to fold flat and can be fully removed by squeezing the wire feet together. This solves a real problem: fixed handles stick out and prevent clipped documents from lying flat in a drawer or on a shelf. Folding the handles eliminates the protruding lever arm entirely. It also prevents accidental release, because once the handles are folded down, there is no moment arm for a bump or snag to act on. Removing the handles entirely turns the clip into a low-profile semi-permanent binding that cannot be opened without a tool, which was a feature no competing clip design offered at the time.

## Communicate

The About Me section for this assignment is located on the About Me page of this portfolio, accessible through the navigation sidebar. It includes my professional introduction, my response to the question about defending an engineering decision, and time spent on this assignment.
