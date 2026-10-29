# A8 - Gearbox Design

Rick Bhattacharya · MEGR 2157<br>
Total time spent: **5 hours**.

[Download the submission PDF](files/A08-submission.pdf) · [Download the assembly export](files/Gearbox-assembly.3mf) · [Download the CAD source files](files/A08-CAD-source.zip)

## Objective

For this assignment, I worked from the required gear ratio and output conditions to size the shafts and journal bearings, then built a gearbox layout in SOLIDWORKS. I used the calculations to establish the shaft diameters and bearing requirements before arranging the gears inside a rectangular housing.

The gearbox uses an 18-tooth input pinion and a 48-tooth output gear. The larger gear increases torque while reducing speed. My final assembly view shows the gears and shafts inside the open housing so their arrangement is visible.

<figure class="a8-figure cad" id="a8-figure-1"><a href="images/01-assembly.webp" target="_blank" rel="noopener"><img src="images/01-assembly.webp" alt="Open housing assembly showing the 48-tooth gear, 18-tooth pinion, and protruding shafts." loading="lazy"></a><figcaption><strong>Figure 1.</strong> Open housing assembly showing the 48-tooth gear, 18-tooth pinion, and protruding shafts. <a href="images/01-assembly.webp">Full size</a>.</figcaption></figure>

## Design inputs and assumptions

| Parameter | Input / pinion shaft | Output / gear shaft |
|---|---:|---:|
| Number of gear teeth, z | 18 | 48 |
| Pitch diameter, D<sub>p</sub> | 0.375 in | 1.000 in |
| Shaft diameter, d | 0.125 in | 0.250 in |
| Shaft length, L | 1.000 in | 1.000 in |
| Speed, N | Calculated | 1,100 rpm |
| Torque, T | Calculated | 1.250 in·lbf |
| Allowable shear stress used | 4,000 psi | 8,500 psi |

Both gears have a 20° pressure angle. The tooth ratio is 48:18, which simplifies to the required **24:9**. I treated the gear train as ideal, so transmitted power is the same at the input and output. Following the assignment, I ignored shaft bending from the gear forces for the shaft strength calculation and checked torsional shear stress.

For the bearing calculations, I used two supports per shaft and placed the gear load midway between them. This gives equal reactions at the two bearings. It is an analytical support model; the bearing reactions depend on the actual support and gear positions in a finished assembly.

The gear-to-shaft connection is intended to be a press fit. The shaft-to-bearing interface requires a running/sliding fit. These interfaces have different purposes: the gear must transmit torque with the shaft, while the bearing must allow the shaft to rotate.

## Speed, torque, and power

The input speed follows from the gear ratio. With an ideal train, torque changes inversely with speed.

<div class="a8-equations">
N<sub>i</sub>z<sub>i</sub> = N<sub>o</sub>z<sub>o</sub><br>
N<sub>i</sub> = 1,100(48/18) = <strong>2,933.3 rpm</strong><br><br>
T<sub>i</sub>N<sub>i</sub> = T<sub>o</sub>N<sub>o</sub><br>
T<sub>i</sub> = 1.250(18/48) = <strong>0.46875 in·lbf</strong><br><br>
H = TN / 63,025<br>
H<sub>i</sub> = (0.46875)(2,933.3) / 63,025 = <strong>0.02182 hp</strong><br>
H<sub>o</sub> = (1.250)(1,100) / 63,025 = <strong>0.02182 hp</strong>
</div>

The power check agrees at both ends. The input rotates faster and carries less torque than the output.

<figure class="a8-figure handwork" id="a8-figure-2"><a href="images/02-work1.webp" target="_blank" rel="noopener"><img src="images/02-work1.webp" alt="Handwritten input-speed, torque, power, and shaft-design setup." loading="lazy"></a><figcaption><strong>Figure 2.</strong> Handwritten input-speed, torque, power, and shaft-design setup. <a href="images/02-work1.webp">Full size</a>.</figcaption></figure>

## Input shaft design

### Knowns, unknowns, and free-body diagram

The input shaft is 1.000 in long and 0.125 in in diameter. Its transmitted torque is 0.46875 in·lbf, and I used 4,000 psi as the allowable torsional shear stress. The unknowns are maximum shear stress and minimum required diameter.

For steady rotation, the shaft has equal and opposite end torques. Its torque balance is T<sub>drive</sub> - T<sub>gear</sub> = 0. The internal torque magnitude for this calculation is 0.46875 in·lbf. The shaft and support free-body diagrams are included in the handwritten work below.

### Equations and result

For a solid circular shaft, c = d/2 and J = πd⁴/32. Substituting into τ = Tc/J gives:

<div class="a8-equations">
τ<sub>max</sub> = 16T / (πd³)<br>
τ<sub>allow</sub> ≥ 16T / (πd³)<br>
d<sub>min</sub> = [16T / (πτ<sub>allow</sub>)]<sup>1/3</sup><br><br>
τ<sub>i</sub> = 16(0.46875) / [π(0.125)³] = <strong>1,222.3 psi</strong><br>
d<sub>min,i</sub> = [16(0.46875) / (π × 4,000)]<sup>1/3</sup> = <strong>0.0842 in</strong>
</div>

The 0.125-in input shaft exceeds the calculated minimum diameter and its shear stress is below 4,000 psi. **I retained the specified 0.125-in diameter.** This conclusion applies to the torsion model and allowable stress used here.

## Output shaft design

### Knowns, unknowns, and free-body diagram

The output shaft is 1.000 in long and 0.250 in in diameter, with 1.250 in·lbf of torque at 1,100 rpm. I used 8,500 psi as its allowable shear stress. The unknowns are maximum shear stress and minimum diameter. The output shaft FBD has equal and opposite 1.250-in·lbf torques at its ends.

### Equations and result

<div class="a8-equations">
T<sub>gear</sub> - T<sub>load</sub> = 0<br>
τ<sub>o</sub> = 16(1.250) / [π(0.250)³] = <strong>407.4 psi</strong><br>
d<sub>min,o</sub> = [16(1.250) / (π × 8,500)]<sup>1/3</sup> = <strong>0.0908 in</strong>
</div>

The output diameter is greater than the calculated minimum, and the computed shear stress is below 8,500 psi. **I retained the specified 0.250-in diameter.**

<figure class="a8-figure handwork" id="a8-figure-3"><a href="images/03-work2.webp" target="_blank" rel="noopener"><img src="images/03-work2.webp" alt="Handwritten torsion equations, shaft FBD, and gear-force calculations. The typed shaft sections separate the input and output results." loading="lazy"></a><figcaption><strong>Figure 3.</strong> Handwritten torsion equations, shaft FBD, and gear-force calculations. The typed shaft sections separate the input and output results. <a href="images/03-work2.webp">Full size</a>.</figcaption></figure>

## Gear forces and bearing reactions

### Force model

The known output torque is 1.250 in·lbf, the output pitch diameter is 1.000 in, and the pressure angle is 20°. I solved for tangential force F<sub>t</sub>, radial force F<sub>r</sub>, resultant gear load W, and bearing reactions R<sub>A</sub> and R<sub>B</sub>.

<div class="a8-equations">
T<sub>o</sub> = F<sub>t</sub>(D<sub>p,o</sub>/2)<br>
F<sub>t</sub> = 2T<sub>o</sub>/D<sub>p,o</sub> = 2(1.250)/1.000 = <strong>2.500 lbf</strong><br>
F<sub>r</sub> = F<sub>t</sub>tan φ = 2.500 tan 20° = <strong>0.9099 lbf</strong><br>
W = √(F<sub>t</sub>² + F<sub>r</sub>²) = <strong>2.6604 lbf</strong>
</div>

The meshing gears exert equal and opposite forces on each other. I used the magnitude of the resultant load for each shaft's bearing sizing calculation.

### Support equilibrium

For a centered load over bearing span S, the moment equation about support A gives R<sub>B</sub>S = W(S/2). Force equilibrium then gives the other reaction.

<div class="a8-equations">
ΣM<sub>A</sub> = 0: R<sub>B</sub>S - W(S/2) = 0<br>
R<sub>B</sub> = W/2<br>
ΣF = 0: R<sub>A</sub> + R<sub>B</sub> - W = 0<br>
R<sub>A</sub> = R<sub>B</sub> = W/2 = <strong>1.3302 lbf</strong><br>
W<sub>b</sub> = <strong>1.3302 lbf per bearing</strong>
</div>

The isolated bearing FBD balances the shaft load with the reaction from the housing. The load directions reverse between the input and output shaft diagrams, but the reaction magnitudes are equal in this centered-load model.

<figure class="a8-figure handwork" id="a8-figure-4"><a href="images/04-work3.webp" target="_blank" rel="noopener"><img src="images/04-work3.webp" alt="Output shaft torque FBD, centered bearing-support diagrams, and individual bearing equilibrium." loading="lazy"></a><figcaption><strong>Figure 4.</strong> Output shaft torque FBD, centered bearing-support diagrams, and individual bearing equilibrium. <a href="images/04-work3.webp">Full size</a>.</figcaption></figure>

## Journal bearing design

### Material and reference limits

I used oil-impregnated sintered bronze as the bearing material for the calculations. The reference limits used in my work are shown below. These are material reference values, rather than a claim that every bronze sleeve bearing has the same rating. [PIC Design material reference](https://www.pic-designcatalog.com/b10-14.html).

| Property | Value used |
|---|---:|
| Allowable projected pressure, P<sub>allow</sub> | 2,000 psi |
| Allowable sliding velocity, V<sub>allow</sub> | 1,200 ft/min |
| Allowable PV | 50,000 psi·ft/min |
| Ultimate tensile strength, S<sub>ut</sub> | 14,000 psi |
| Ultimate-strength design factor, n<sub>u</sub> | 4 |
| Allowable hoop stress, S<sub>ut</sub>/n<sub>u</sub> | 3,500 psi |

### Length, pressure, velocity, and PV

The unknowns are the minimum bearing length, operating pressure, sliding velocity, and PV. I used projected area dL for the pressure calculation. The minimum length must satisfy both the pressure and PV limits; the velocity limit is checked separately.

<div class="a8-equations">
A<sub>projected</sub> = dL<br>
P = W<sub>b</sub>/(dL)<br>
V = πdN/12 &nbsp; [d in inches; V in ft/min]<br>
PV = W<sub>b</sub>V/(dL)<br><br>
L<sub>P</sub> ≥ W<sub>b</sub>/(dP<sub>allow</sub>)<br>
L<sub>PV</sub> ≥ W<sub>b</sub>V/[d(PV)<sub>allow</sub>]<br>
L ≥ max(L<sub>P</sub>, L<sub>PV</sub>)
</div>

For the input bearing:

<div class="a8-equations">
V<sub>i</sub> = π(0.125)(2,933.3)/12 = <strong>95.99 ft/min</strong><br>
L<sub>P,i</sub> ≥ 1.3302/[(0.125)(2,000)] = <strong>0.00532 in</strong><br>
L<sub>PV,i</sub> ≥ (1.3302)(95.99)/[(0.125)(50,000)] = <strong>0.02043 in</strong>
</div>

For the output bearing:

<div class="a8-equations">
V<sub>o</sub> = π(0.250)(1,100)/12 = <strong>71.99 ft/min</strong><br>
L<sub>P,o</sub> ≥ 1.3302/[(0.250)(2,000)] = <strong>0.00266 in</strong><br>
L<sub>PV,o</sub> ≥ (1.3302)(71.99)/[(0.250)(50,000)] = <strong>0.00766 in</strong>
</div>

I used **0.250 in as the nominal bearing length** for both shaft sizes. At that length, the operating values are:

| Check | Input bearing | Output bearing | Reference limit |
|---|---:|---:|---:|
| Journal diameter | 0.125 in | 0.250 in | Shaft size |
| Nominal length | 0.250 in | 0.250 in | Above calculated minima |
| Projected pressure | 42.57 psi | 21.28 psi | 2,000 psi |
| Sliding velocity | 95.99 ft/min | 71.99 ft/min | 1,200 ft/min |
| PV | 4,086 psi·ft/min | 1,532 psi·ft/min | 50,000 psi·ft/min |

All three operating checks are below the reference limits. The input bearing controls the length calculation because its smaller journal and higher speed produce the larger PV requirement.

<figure class="a8-figure handwork" id="a8-figure-5"><a href="images/05-work4.webp" target="_blank" rel="noopener"><img src="images/05-work4.webp" alt="Bronze reference limits and input bearing length from pressure and PV." loading="lazy"></a><figcaption><strong>Figure 5.</strong> Bronze reference limits and input bearing length from pressure and PV. <a href="images/05-work4.webp">Full size</a>.</figcaption></figure>

<figure class="a8-figure handwork" id="a8-figure-6"><a href="images/06-work5.webp" target="_blank" rel="noopener"><img src="images/06-work5.webp" alt="Output bearing length and setup for the sleeve wall-thickness model." loading="lazy"></a><figcaption><strong>Figure 6.</strong> Output bearing length and setup for the sleeve wall-thickness model. <a href="images/06-work5.webp">Full size</a>.</figcaption></figure>

### Bearing wall thickness

I modeled the sleeve as a thick cylinder with a uniform equivalent internal pressure p and zero external pressure. I used the projected bearing pressures above for p. This is a simplified wall-stress calculation; it does not include the actual contact-pressure distribution, interference with the housing, or thermal effects.

The knowns are journal diameter D<sub>i</sub>, pressure p, and allowable hoop stress σ<sub>allow</sub> = 3,500 psi. The unknowns are minimum outside diameter D<sub>o,min</sub> and minimum radial wall thickness t<sub>min</sub>.

<div class="a8-equations">
σ<sub>θ,max</sub> = p(D<sub>o</sub>² + D<sub>i</sub>²)/(D<sub>o</sub>² - D<sub>i</sub>²)<br>
(σ<sub>allow</sub> - p)D<sub>o</sub>² = (σ<sub>allow</sub> + p)D<sub>i</sub>²<br>
D<sub>o,min</sub> = D<sub>i</sub>√[(σ<sub>allow</sub> + p)/(σ<sub>allow</sub> - p)]<br>
t<sub>min</sub> = (D<sub>o,min</sub> - D<sub>i</sub>)/2<br><br>
t<sub>min,i</sub> = (0.125/2){√[(3,500 + 42.57)/(3,500 - 42.57)] - 1}<br>
t<sub>min,i</sub> = <strong>0.000765 in</strong><br><br>
t<sub>min,o</sub> = (0.250/2){√[(3,500 + 21.28)/(3,500 - 21.28)] - 1}<br>
t<sub>min,o</sub> = <strong>0.000762 in</strong>
</div>

These small values are theoretical stress minima. They are not practical wall thicknesses to manufacture. A catalog sleeve needs enough material for handling, installation, and its specified housing fit as well as the calculated load.

For component selection, the bearing types are **oil-embedded bronze sleeve bearings for a 1/8-in shaft** and **oil-embedded bronze sleeve bearings for a 1/4-in shaft**, with a nominal 1/4-in length for this calculation. The supplier's outside diameter and installed-bore requirements determine the corresponding housing seat. [McMaster-Carr sleeve bearings](https://www.mcmaster.com/products/journal-bearings/sleeve-bearings-3~/).

<figure class="a8-figure handwork" id="a8-figure-7"><a href="images/07-work6.webp" target="_blank" rel="noopener"><img src="images/07-work6.webp" alt="Sleeve wall-stress FBD, thick-cylinder model, and input/output thickness calculations." loading="lazy"></a><figcaption><strong>Figure 7.</strong> Sleeve wall-stress FBD, thick-cylinder model, and input/output thickness calculations. <a href="images/07-work6.webp">Full size</a>.</figcaption></figure>

## Housing sketch and assembly concept

My sketch uses a rectangular housing body with a removable front component. The two attachment locations shown above and below the opening establish the intended screw-fastened connection. A removable front gives access to the gears and shafts during assembly and disassembly.

I considered making the housing follow the gear outlines more closely, but kept the rectangular layout for this model. It gives a simple starting shape for the cavity and leaves a rim around the front opening. The sketch records the enclosure concept; the open CAD view below shows the internal arrangement.

<figure class="a8-figure handwork" id="a8-figure-8"><a href="images/08-work7.webp" target="_blank" rel="noopener"><img src="images/08-work7.webp" alt="Housing sketch showing the gear pair, enclosure, and two front attachment locations." loading="lazy"></a><figcaption><strong>Figure 8.</strong> Housing sketch showing the gear pair, enclosure, and two front attachment locations. <a href="images/08-work7.webp">Full size</a>.</figcaption></figure>

## Parametric CAD modeling

### Shafts and gear placement

I modeled the shafts as dimensioned circular profiles extruded to 1.000 in. The input diameter is 0.125 in and the output diameter is 0.250 in. The shaft drawings include 0.010-in × 45° end chamfers. The input screenshot rounds the displayed diameter to 0.13 in; the detailed drawing records the intended 0.125-in dimension.

<figure class="a8-figure cad" id="a8-figure-9"><a href="images/09-inputshaft.webp" target="_blank" rel="noopener"><img src="images/09-inputshaft.webp" alt="Input shaft CAD: 1.000-in length. The diameter display is rounded; the drawing specifies 0.125 in." loading="lazy"></a><figcaption><strong>Figure 9.</strong> Input shaft CAD: 1.000-in length. The diameter display is rounded; the drawing specifies 0.125 in. <a href="images/09-inputshaft.webp">Full size</a>.</figcaption></figure>

<figure class="a8-figure cad" id="a8-figure-10"><a href="images/10-outputshaft.webp" target="_blank" rel="noopener"><img src="images/10-outputshaft.webp" alt="Output shaft CAD: 1.000-in length and 0.250-in diameter, with chamfered ends." loading="lazy"></a><figcaption><strong>Figure 10.</strong> Output shaft CAD: 1.000-in length and 0.250-in diameter, with chamfered ends. <a href="images/10-outputshaft.webp">Full size</a>.</figcaption></figure>

I used the McMaster-Carr models for the 18-tooth pinion, **7880K19**, and 48-tooth gear, **7880K24**. Their pitch diameters establish the shaft center distance:

<div class="a8-equations">
C = (D<sub>p,i</sub> + D<sub>p,o</sub>)/2<br>
C = (0.375 + 1.000)/2 = <strong>0.6875 in</strong>
</div>

I placed the shaft axes 0.6875 in apart. Using the outside diameters for this distance would space the gears incorrectly because the pitch circles establish the nominal mesh. The screenshot records the center-distance dimension used in the layout.

<figure class="a8-figure cad" id="a8-figure-11"><a href="images/11-mesh.webp" target="_blank" rel="noopener"><img src="images/11-mesh.webp" alt="Gear layout with the 0.6875-in center-distance dimension." loading="lazy"></a><figcaption><strong>Figure 11.</strong> Gear layout with the 0.6875-in center-distance dimension. <a href="images/11-mesh.webp">Full size</a>.</figcaption></figure>

### Housing dimensions and design intent

The housing drawing records a **2.400-in width, 1.900-in height, and 0.900-in overall depth**. The front opening is surrounded by a 0.250-in rim, and the back-wall callout is 0.100 in. I used the gear arrangement to establish the cavity position and placed the shaft openings in the rear wall.

The important relationships are the fixed shaft center distance, the shaft diameters, the cavity around the gear teeth and hubs, and the bearing seats. A clearance around the tooth tips is separate from the fit at the rotating journals. The final view communicates the component arrangement; it is not a physical rotation or interference test.

### CAD drawings

The drawings document the two shafts and the housing body. Each preview opens the original PDF so the dimensions can be read at full size. They are also reproduced in the submission report's drawing appendix.

<figure class="a8-figure drawing" id="a8-figure-12"><a href="files/input-shaft.pdf" target="_blank" rel="noopener"><img src="images/12-drawinginput.webp" alt="Input shaft drawing: diameter, length, end chamfer, and multiple views." loading="lazy"></a><figcaption><strong>Figure 12.</strong> Input shaft drawing: diameter, length, end chamfer, and multiple views. <a href="files/input-shaft.pdf">Open original drawing PDF</a>.</figcaption></figure>

<figure class="a8-figure drawing" id="a8-figure-13"><a href="files/output-shaft.pdf" target="_blank" rel="noopener"><img src="images/13-drawingoutput.webp" alt="Output shaft drawing: diameter, length, end chamfer, and multiple views." loading="lazy"></a><figcaption><strong>Figure 13.</strong> Output shaft drawing: diameter, length, end chamfer, and multiple views. <a href="files/output-shaft.pdf">Open original drawing PDF</a>.</figcaption></figure>

<figure class="a8-figure drawing" id="a8-figure-14"><a href="files/housing-body.pdf" target="_blank" rel="noopener"><img src="images/14-drawingbase.webp" alt="Housing body drawing with overall dimensions, cavity, and hole callouts." loading="lazy"></a><figcaption><strong>Figure 14.</strong> Housing body drawing with overall dimensions, cavity, and hole callouts. <a href="files/housing-body.pdf">Open original drawing PDF</a>.</figcaption></figure>

## Results

| Design quantity | Input side | Output side |
|---|---:|---:|
| Speed | 2,933.3 rpm | 1,100 rpm |
| Torque | 0.46875 in·lbf | 1.250 in·lbf |
| Transmitted power | 0.02182 hp | 0.02182 hp |
| Calculated torsional shear stress | 1,222.3 psi | 407.4 psi |
| Minimum shaft diameter | 0.0842 in | 0.0908 in |
| Retained shaft diameter | 0.125 in | 0.250 in |
| Load per bearing, centered-support model | 1.3302 lbf | 1.3302 lbf |
| Minimum length from pressure and PV | 0.02043 in | 0.00766 in |
| Nominal length used | 0.250 in | 0.250 in |
| Theoretical minimum sleeve wall | 0.000765 in | 0.000762 in |

Both shafts meet the torsional strength checks with the specified diameters. A 0.250-in bearing length satisfies the pressure, speed, and PV checks for the bronze reference data and assumed bearing loads. The CAD layout uses the calculated 0.6875-in gear center distance and shows how the shafts and gears fit within the open rectangular housing.

## Lessons learned and mistakes

**Pitch diameter controls gear spacing.** I had to distinguish the pitch circles from the outside tooth diameters when positioning the gears. Adding the pitch radii gave a clear center-distance dimension to use in CAD.

**A diameter display can hide useful precision.** The input-shaft screenshot shows 0.13 in after rounding, while the intended dimension is 0.125 in. I used the detailed drawing to communicate the shaft size rather than relying on the rounded screenshot alone.

**Strength and fit answer different questions.** A shaft can pass a torsion calculation while still requiring a properly specified fit at each interface. The gear hub needs to transmit torque, and the bearing bore needs clearance for rotation. Treating every hole as the same nominal shaft diameter would miss that distinction.

**Bearing pressure uses projected area.** I used dL rather than the full curved surface area. The input bearing also showed why pressure alone is insufficient: its higher speed makes the PV check more restrictive than the pressure-only length check.

**A theoretical minimum is not a manufacturing dimension.** The wall-stress calculation produced thicknesses below one thousandth of an inch because the load is small relative to the assumed material strength. A usable sleeve still needs a practical wall and an appropriate installed fit.

**Assembly details need their own dimensions.** Working through the housing made the relationship between shaft position, gear hubs, bearing support, and the removable front more apparent. The equations establish the operating loads, while the component layout determines where those loads enter the housing.

Total time spent on calculations, sketching, CAD, and documentation: **5 hours**.

## CAD and source downloads

| File | Contents |
|---|---|
| [Assembly export](files/Gearbox-assembly.3mf) | Final exported mesh geometry for viewing the assembly |
| [CAD source package](files/A08-CAD-source.zip) | Two shaft parts, two gear parts, gear STEP files, the working assembly saves, and the 3MF export |
| [Input shaft drawing](files/input-shaft.pdf) | Original 0.125-in shaft drawing |
| [Output shaft drawing](files/output-shaft.pdf) | Original 0.250-in shaft drawing |
| [Housing body drawing](files/housing-body.pdf) | Original housing drawing |
| [Original work and screenshots](files/A08-original-work.zip) | All seven handwritten pages and four CAD screenshots |
| [Submission report](files/A08-submission.pdf) | Report with full-page handwritten work and original drawing appendices |

The 3MF is a mesh export. The source package retains the original native SOLIDWORKS component and working assembly filenames so their references can be kept together.

## References

- Course assignment: *A8: Gear Box Design*, MEGR 2157. Required output conditions, shaft dimensions, assumptions, and drawing requirements.
- *Machinery's Handbook*: shaft torsion, gearing, and plain-bearing methods referenced by the assignment.
- [McMaster-Carr 7880K19 pinion](https://www.mcmaster.com/7880K19/) and [7880K24 gear](https://www.mcmaster.com/7880K24/): gear component models and nominal geometry.
- [PIC Design bronze bearing reference](https://www.pic-designcatalog.com/b10-14.html): material data used for the bearing pressure, velocity, PV, and strength assumptions.
- [McMaster-Carr journal sleeve bearings](https://www.mcmaster.com/products/journal-bearings/sleeve-bearings-3~/): sleeve-bearing component selection.

<style>
.a8-figure { margin: 1.6rem 0 2rem; padding: .85rem; border: 1px solid #dce2eb; border-radius: .5rem; background: #f7f9fc; }
.a8-figure img { display: block; max-width: 100%; height: auto; max-height: 760px; margin: auto; object-fit: contain; }
.a8-figure.handwork img { max-height: 920px; }
.a8-figure figcaption { margin-top: .65rem; color: #465469; font-size: .82rem; line-height: 1.5; }
.a8-equations { padding: 1rem 1.15rem; margin: 1rem 0; border-left: 4px solid #4051b5; background: #f0f3fa; line-height: 1.85; overflow-wrap: anywhere; }
@media print {
 @page { size: Letter; margin: 16mm 15mm 18mm; }
 .md-header,.md-tabs,.md-sidebar,.md-footer,.md-top,.md-content__button { display:none !important; }
 .md-main__inner,.md-grid,.md-content { margin:0 !important; max-width:none !important; padding:0 !important; }
 .md-typeset { font-family: Arial, sans-serif; font-size: 10pt; line-height:1.4; color:#172232; }
 .md-typeset h1 { font-size:24pt; } .md-typeset h2 { font-size:16pt; margin-top:1.2em; } .md-typeset h3 { font-size:12pt; }
 .md-typeset h1,.md-typeset h2,.md-typeset h3 { break-after:avoid; }
 .md-typeset table:not([class]) { font-size:8.3pt; min-width:0; width:100%; }
 .md-typeset table:not([class]) th,.md-typeset table:not([class]) td { padding:6px 8px; }
 .md-typeset table,.a8-equations,.a8-figure { break-inside:avoid; }
 .md-typeset p { break-inside:avoid; }
 .a8-figure.handwork,.a8-figure.drawing { display:none; }
 .a8-figure img { max-height:260px; }
 .a8-figure { padding:8px; margin:14px 0; }
 .a8-figure figcaption { font-size:8pt; }
 .a8-equations { padding:9px 12px; line-height:1.55; }
 .md-typeset ul { break-inside:avoid; }
 a { color:#283f81; text-decoration:none; }
 .md-typeset .headerlink { display:none; }
}
</style>
