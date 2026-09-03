# MEGR 2156 Assignment 2: Truss Stress

## 1. Primary Objective & Truss Design Concept

**Primary Objective:**
The main goal of this project was designing a lightweight planar truss using A500 steel. It had to safely handle two opposing 20 kN point loads (one pushing up at C and one pulling down at D) while fitting within the strict a = 0.4 m and b = 0.3 m spatial constraints from the assignment prompt.

![Original Problem Constraints](images/media_1788402874737.png)

**Thinking Process & Geometry Layout:**
I started out by mapping the required nodes: A for the pin, B for the roller, and C and D for the loads. My priority was keeping the frame as simple as possible to save on weight. I checked the static determinacy equation (m + r = 2j) to figure out the minimum number of members I could get away with. With 4 joints (j=4) and 3 reaction forces (r=3), I needed exactly 5 members (m=5) to maintain rigidity.

I connected the outer perimeter (AB, BC, CD, AD) and ran a single internal diagonal member (AC) so the frame wouldn't collapse. This layout minimized weight while fully supporting the twisting moment caused by the C and D loads.

![Overall Truss Design](images/media_1788400563701.jpg)

---

## 2. Static Analysis & Internal Forces (Phase 1)

I needed to figure out exactly how much force was running through the truss before sizing the steel members. I found the global reactions using basic static equilibrium equations. From there I worked through the Method of Joints to solve for the tension and compression in every single piece. The diagonal member AC ended up taking the most force, making it the driving factor for the rest of my design.

![Global Reactions and Joint B](images/media_1788400563705.jpg)

![Joints D, C, and A](images/media_1788400563708.jpg)

**Internal Force Summary:**

* **F_AD:** 33.33 kN (Tension)
* **F_CD:** 26.67 kN (Tension)
* **F_BC:** -11.11 kN (Compression)
* **F_AB:** 8.89 kN (Tension)
* **F_AC:** -37.97 kN (Compression) <-- **Maximum Internal Force**

---

## 3. Truss Structure Sizing (Phase 2)

Knowing the maximum internal force allowed me to size the A500 steel members so they wouldn't fail under the load. The assignment required a safety factor of 3.5. I divided the steel's yield strength by that factor to find the absolute minimum cross-sectional area required. Estimating the total weight of the truss was pretty straightforward after that since I just multiplied the required area by the combined centerline length of all five members.

**Knowns:**

* Maximum Internal Force (F_max): 37.97 kN (or 37,970 N)
* Safety Factor (SF): 3.5
* Yield Strength of A500 Steel (sigma_y): 228 MPa (228 x 10^6 N/m^2)
* Total Length (L_tot): 1.2m + 0.4m + 0.5m + 0.5m + 0.854m = 3.454 m
* Density of A500 Steel (rho): 7800 kg/m^3

**Unknowns:**

* Minimum cross-sectional area (A)
* Approximate mass of the truss

![Truss Member Sizing Calculations](images/media_1788400563738.jpg)

**Results & Derivations:**

**Step 1: Calculate Minimum Cross-Sectional Area**
The area is calculated using the maximum internal force (37,970 N), the safety factor (3.5), and the yield strength (228 x 10^6 N/m^2).

Symbolic Equation: A = (F_max * SF) / sigma_y
Numerical Solution: A = (37,970 N * 3.5) / (228 x 10^6 N/m^2)
A = 0.0005829 m^2 (or 582.9 mm^2)

**Step 2: Calculate Approximate Mass**
First, find the total volume by multiplying the area by the total length of all members, then multiply by density.

Volume = A * L_tot
Volume = 0.0005829 m^2 * 3.454 m = 0.002013 m^3
Mass = Volume * rho
Mass = 0.002013 m^3 * 7800 kg/m^3 = 15.8 kg

---

## 4. Connecting Pin Sizing (Phase 3)

I went with hardened tool steel for the joint pins to ensure they could handle the shear forces without snapping. I assumed a standard single-shear connection and applied a safety factor of 4 against the maximum internal force to find the minimum pin area. After calculating the diameter, I found the total pin weight by assuming the wall bracket would match the exact thickness of the truss members.

**Knowns:**

* Maximum Shear Force (V_max): 37.97 kN x 224.81 = 8,536 lbf
* Yield Shear Strength (tau_y): 170 ksi (170,000 lbf/in^2)
* Pin Density (rho): 0.278 lb/in^3
* Safety Factor (SF): 4
* Connection Type: Single Shear

**Unknowns:**

* Minimum pin cross-sectional area (A_pin)
* Approximate combined weight of the pins

![Pin Sizing Calculations](images/media_1788400563736.jpg)

**Results & CAD Dimension Derivations:**

* **Minimum Pin Area (A_pin):** 0.2008 in^2 (diameter of ~12.84 mm)
* **Approximate Pin Weight:** 0.446 lbs

**Step 1: Calculate Minimum Required Area**

The area is derived from the maximum internal shear force (8,536 lbf), the safety factor (4), and the yield shear strength of the tool steel (170,000 psi).

A_pin = (V_max * SF) / tau_y
A_pin = (8,536 lbf * 4) / 170,000 psi
A_pin = 0.2008 in^2

Convert the area from square inches to square millimeters to match the metric CAD environment:
0.2008 in^2 * (25.4 mm / 1 in)^2 = **129.5 mm^2**

**Step 2: Solve for Pin Diameter**

Because pins are cylindrical, I used the area of a circle equation to solve for the radius, and then just doubled it for the CAD diameter dimension.

Area = pi * r^2
129.5 mm^2 = pi * r^2
r^2 = 129.5 / pi = 41.22 mm^2
r = sqrt(41.22) = 6.42 mm
d = 2r = 2(6.42) = **12.84 mm**

**Step 3: Calculate Pin Length**

The assignment specifies a single-shear connection, which means the CAD extrusion has to be long enough to pass entirely through the solid truss member and into the mounting plate (gusset) behind it. To establish a defined length for the volume calculation, I assumed the mounting plate was identical in thickness to the A500 truss member (24.14 mm).

L_pin = Truss Thickness + Gusset Thickness
L_pin = 24.14 mm + 24.14 mm
L_pin = 48.28 mm

![Pin Engineering Drawing](images/media_1788402819284.jpg)

---

## 5. CAD Verification (Phase 4)

To double-check my hand calculations, I jumped into SolidWorks and built a 3D model using the exact dimensions I just solved for. I modeled the truss as a single merged part with a solid 24.14 mm square profile, and extruded the pins as separate cylinders. Once the model was laid out, I pulled up the mass properties tool to see how the physical CAD weight compared to my theoretical math.

![Truss SolidWorks Sketch](images/media_1788402819302.png)

* **Calculated 1D Theoretical Mass:** 15.8 kg
* **Verified 3D CAD Mass:** 14.41 kg

---

## 6. Lessons Learned & Mistakes Log

This assignment really showed me how a single bad assumption can derail an entire engineering design. Early on I accidentally assumed the 20 kN load at node C was pointing down instead of up. Fixing that one flipped arrow completely changed the way internal forces were distributed across the truss. I also learned a lot about the gap between theoretical math and physical reality. My hand-calculated mass (15.8 kg) came out noticeably heavier than the CAD mass (14.41 kg). The 1D math double-counts the steel where the beams overlap at the joints, whereas the 3D CAD model merges those overlapping volumes together.

---

## 7. MEGR 2157: Failure Modes Analysis

### Part 1 - Truss Members

* **Expected Failure Mode:** The expected failure mode for the truss members really depends on the direction of the load. The tension members (AB, AD, CD) will most likely fail by **yielding**. They will elongate permanently once the normal stress passes the 228 MPa limit. The compression members (BC, AC) face a completely different problem. They will fail via **Euler buckling** long before the material reaches its compressive yield limit. Long and slender structural elements naturally become geometrically unstable under heavy compressive loads.
* **Material Classification:** A500 structural steel is classified as a **ductile** material, meaning it experiences significant plastic deformation (stretching or bending) before snapping.
* **Support & Reasoning:** In mechanics of materials we know tensile stress is uniformly distributed across the cross-section (sigma = F/A). This makes yielding the primary concern. Compressive stress introduces lateral deflection risks. Compressive stability relies heavily on the area moment of inertia (I) rather than just the raw cross-sectional area.
* **Design Modification:** If I wanted to reduce the likelihood of buckling in the compression members without adding too much weight, I would change the cross-sectional geometry from a solid square rod to a hollow square tube. This pushes the material further from the neutral axis and massively increases the area moment of inertia while keeping the cross-sectional area identical.

### Part 2 - Pin Connections

* **Expected Failure Mode:** The pins are most likely to fail through **transverse shear fracture**. A secondary possibility is that the connection could fail via bearing yielding, where the harder tool steel pin crushes the softer A500 steel pinhole.
* **Support & Reasoning:** The Machinery's Handbook (Working Stress section) notes that pins in a single-shear configuration experience the entire 8,536 lbf internal load concentrated across one microscopic slip plane. Hardened tool steel is brittle and won't deform plastically to absorb energy. If the ultimate shear strength is exceeded, the pin will just snap cleanly right at that shear plane.
* **Design Modification:** The best way to improve this joint would be redesigning it from a single-shear connection to a **double-shear connection**. Placing the truss member inside a clevis bracket or sandwiching it between two welded gusset plates perfectly splits the shear force across two distinct shear planes on the pin. This immediately cuts the applied shear stress in half (tau = F/2A) without needing a larger or heavier pin.
