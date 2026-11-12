<style>

.a10-actions{padding:16px 20px;background:#eef4f8;border-left:4px solid #185a78;border-radius:4px;margin:20px 0 30px;line-height:2}
.a10-figure{margin:24px 0;padding:14px;border:1px solid #dce3e9;border-radius:8px;background:#f8fafc;break-inside:avoid}
.a10-figure img{display:block;width:100%;height:auto;max-height:680px;object-fit:contain;margin:auto}
.a10-figure.handwork img{max-height:850px}.a10-figure.diagram{background:#fff}.a10-figure.diagram img{max-height:380px}
.a10-figure:has(img[src$="fos-detail.webp"]) img{max-width:400px}
.a10-figure figcaption{font-size:.82em;line-height:1.6;color:#465968;margin-top:12px}
.a10-figure.handwork{max-width:680px;margin-left:auto;margin-right:auto}
.a10-pair{display:grid;grid-template-columns:1fr 1fr;gap:18px;align-items:start}.a10-pair .a10-figure{margin:12px 0}
.a10-eq{padding:18px 22px;background:#f1f6f9;border-left:3px solid #185a78;border-radius:3px;line-height:1.9;margin:20px 0;overflow-x:auto;font-variant-numeric:tabular-nums;break-inside:avoid}
.a10-pdf{border:1px solid #dce3e9;border-radius:8px;padding:14px;margin:24px 0;background:#fff}.a10-pdf-title{font-weight:700;display:block;margin-bottom:12px}.a10-pdf-page{display:block;width:100%;height:auto}.a10-reader{margin-top:12px}.a10-reader summary{cursor:pointer;color:#185a78;font-size:.85em}.a10-reader object{margin-top:12px}
.md-content:has(.a10-marker) table{font-size:.8rem;min-width:0!important}.md-content:has(.a10-marker) th,.md-content:has(.a10-marker) td{padding:10px 12px!important}
@media(max-width:760px){.a10-pair{grid-template-columns:1fr}.a10-eq{padding:14px;font-size:.9em}.a10-figure{padding:10px}.a10-actions{padding:12px}}

</style>
<div class="a10-marker"></div>

# A10 - Lead screw tensile tester

Rick Bhattacharya · Antonio Chiocca · Patrick Klauser<br>
MEGR 2157 · Total time spent: **10 hours**

<div class="a10-actions"><a href="files/A10-team-report.pdf">Submission PDF</a> · <a href="files/tensile-tester.f3z">Tester assembly</a> · <a href="files/crosshead.f3d">Crosshead CAD</a></div>

## Objective

We designed a benchtop tensile tester with two identical lead screws and a moving 6061 aluminum crosshead. The design requirements are a 2-kN specimen load, a crosshead speed of 1–50 mm/min, and a minimum safety factor of 4. We sized the screws and crosshead, selected matching nuts and flanges, and compared the initial and rounded-corner crossheads using FEA.

The assembly includes the frame, screws, nuts, flanges, and crosshead. The grip connection, screw end supports, and mechanical synchronization are outside the modeled assembly.

<figure class="a10-figure cad" id="a10-figure-1"><img src="images/assembly.webp" alt="Tester assembly modeled by Rick Bhattacharya. The two screws and nut/flange assemblies position the moving crosshead inside the T-slot frame." loading="lazy"><figcaption><strong>Figure 1.</strong> Tester assembly modeled by Rick Bhattacharya. The two screws and nut/flange assemblies position the moving crosshead inside the T-slot frame. <a href="images/assembly.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

## Team contributions

| Team member | Contribution |
|---|---|
| Rick Bhattacharya | Modeled the tester assembly and crosshead, prepared the crosshead drawing, and completed one of the FEA studies. |
| Antonio Chiocca (AJ) | Worked through the nut-thread and crosshead calculations, checked the screw calculations, and helped with FEA. |
| Patrick Klauser | Worked through the lead screw diameter, rotational speed, and torque calculations and completed another FEA study. |

## Requirements and design inputs

| Input | Value |
|---|---|
| Maximum specimen load, W | 2,000 N |
| Number of lead screws | 2, identical |
| Nominal axial load per screw, F | 1,000 N, assuming centered loading and equal sharing |
| Required safety factor, n | 4 |
| Required crosshead speed | 1–50 mm/min |
| Minimum screw length | 18 in |
| Selected CAD screw | McMaster 99030A981, 1018 steel, 1/4″-16 Acme, right hand, single start, 18 in |
| Matching nut / flange in CAD | 95072A881 / 95082A641 |
| Screw lead, ℓ | 0.0625 in/rev = 1.5875 mm/rev |
| Assumed steel yield strength | 370 MPa; a material-condition assumption |
| Crosshead material | 6061 aluminum |
| Crosshead length / width | 8.00 in / 2.00 in |
| Crosshead thickness | 0.563 in |
| Distance between screw centers | 6.00 in |
| Maximum permitted crosshead deflection | 0.100 mm |

The screw centers are 6 in apart, leaving the specimen region between them.

## Lead screw sizing — Patrick Klauser

### Axial load and minimum root diameter

Knowns: W = 2,000 N, two screws, n = 4, and assumed steel yield strength Sᵧ = 370 MPa. Unknowns: minimum screw area and root diameter. With the specimen centered between the screws, each nut carries 1,000 N.

<div class="a10-eq">
ΣF<sub>y</sub> = 0: R<sub>L</sub> + R<sub>R</sub> − W = 0<br>
R<sub>L</sub> = R<sub>R</sub> = W/2 = <strong>1,000 N</strong><br><br>
σ = F/A ≤ S<sub>y</sub>/n<br>
A<sub>min</sub> = nF/S<sub>y</sub><br>
A = πd<sub>r</sub>²/4<br>
d<sub>r,min</sub> = √[4nF/(πS<sub>y</sub>)]<br><br>
σ<sub>allow</sub> = 370/4 = <strong>92.5 MPa</strong><br>
A<sub>min</sub> = 4(1,000)/370 = <strong>10.81 mm²</strong><br>
d<sub>r,min</sub> = √[4(4)(1,000)/(π × 370)] = <strong>3.710 mm = 0.1461 in</strong>
</div>

The minimum root diameter from axial stress is 0.1461 in. The selected screw has a nominal outside diameter of 0.250 in. We assumed a 370-MPa yield strength for cold-finished 1018 steel; the purchased screw’s material condition must meet that assumption. [Online Metals: 1018 properties](https://www.onlinemetals.com/en/product-guide/alloy/1018).

<figure class="a10-figure handwork" id="a10-figure-2"><img src="images/patrick-diameter.webp" alt="Patrick Klauser: design constraints, axial screw sizing, FBD, and minimum root diameter." loading="lazy"><figcaption><strong>Figure 2.</strong> Patrick Klauser: design constraints, axial screw sizing, FBD, and minimum root diameter. <a href="images/patrick-diameter.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

### Rotational speed range

Knowns: single-start 1/4″-16 thread and v = 1–50 mm/min. Unknowns: screw speed N and angular velocity ω.

<div class="a10-eq">
p = 1/16 in = 1.5875 mm<br>
ℓ = p × number of starts = <strong>1.5875 mm/rev</strong><br>
v = Nℓ → N = v/ℓ<br><br>
N<sub>min</sub> = 1/1.5875 = <strong>0.6299 rpm</strong><br>
N<sub>max</sub> = 50/1.5875 = <strong>31.496 rpm</strong><br>
ω = 2πN/60 = <strong>0.0660–3.298 rad/s</strong>
</div>

The required screw speed is 0.6299–31.496 rpm. We corrected the angular-velocity units in the initial calculation: 31.496 rpm corresponds to 0.5249 rev/s or 3.298 rad/s. Both screws must rotate together to keep the crosshead level.

### Torque at maximum specimen load

The worksheet inputs are Q = 1,000 N per screw, μ = 0.80, lead ℓ = 0.0625 in/rev, and mean thread radius r<sub>m</sub> = 0.1048 in. The friction coefficient and radius are worksheet assumptions. The radius has not been verified against the selected screw’s pitch diameter.

The worksheet equation treats the thread as square. An Acme thread has a 29° included angle, so the friction term is corrected using the half-angle α = 14.5° and μ′ = μ/cos α. [Acme torque derivation, pp. 190–195](https://www.iare.ac.in/sites/default/files/COURSE%20RESOURCES.pdf); [Autodesk power-screw calculation](https://help.autodesk.com/cloudhelp/2016/ENU/InventorLT-Help/files/GUID-149FFEF7-5A5A-482D-98DC-97F6958898D4.htm).

<div class="a10-eq">
Q = 1,000 N = <strong>224.81 lbf</strong><br>
μ′ = μ/cos(14.5°)<br>
tan λ = ℓ/(2πr<sub>m</sub>)<br>
F<sub>t</sub> = Q(tan λ + μ′)/(1 − μ′ tan λ)<br>
T = F<sub>t</sub>r<sub>m</sub><br><br>
T = Qr<sub>m</sub>(ℓ + 2πμ′r<sub>m</sub>)/(2πr<sub>m</sub> − μ′ℓ)<br>
F<sub>t</sub> = <strong>224.728 lbf</strong><br>
T = <strong>23.551 lbf·in per screw</strong>
</div>

Using μ directly in the square-thread equation gives 22.817 lbf·in with the same inputs. The Acme-angle correction gives 23.551 lbf·in. Both are conditional thread-torque calculations; neither includes thrust-bearing friction, transmission losses, or crosshead weight.

The final handwritten page records 33.8 lbf·in from approximately 0.21 kip × 0.161 in. The 0.161-in value is a diameter in the thread calculation and cannot be used as the mean radius of a 0.250-in-diameter screw. The calculation above retains the earlier worksheet radius consistently. A final drive-torque selection requires the actual pitch radius and friction conditions.

### Combined axial load and torque

The 0.1461-in root-diameter result checks axial stress only. To check whether the selected 1/4-in screw could meet n = 4 under the worksheet’s μ = 0.80 assumption, we also combined axial and torsional stress using the Acme thread torque above.

<div class="a10-eq">
σ<sub>a</sub> = 4Q/(πd²)<br>
τ = 16T/(πd³)<br>
σ<sub>vM</sub> = √(σ<sub>a</sub>² + 3τ²)<br>
n = S<sub>y</sub>/σ<sub>vM</sub><br><br>
For an optimistic solid section with d = 0.250 in:<br>
σ<sub>a</sub> = <strong>4.580 ksi</strong>; τ = <strong>7.677 ksi</strong><br>
σ<sub>vM</sub> = <strong>14.063 ksi</strong><br>
n = 53.664/14.063 = <strong>3.816</strong>
</div>

Even this full-diameter solid-section estimate is below n = 4 with the worksheet torque assumptions. The actual threaded root is smaller. The axial-only calculation therefore does not approve the selected screw for combined loading; the screw selection and its friction assumptions remain unresolved. [Combined-stress yield criterion](https://help.solidworks.com/2022/english/solidworks/cworks/r_Maximum_von_Mises_Stress_Criterion.htm).

<figure class="a10-figure handwork" id="a10-figure-3"><img src="images/patrick-speed.webp" alt="Patrick Klauser: rotational speed and torque calculations." loading="lazy"><figcaption><strong>Figure 3.</strong> Patrick Klauser: rotational speed and torque calculations. <a href="images/patrick-speed.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

<figure class="a10-figure handwork" id="a10-figure-4"><img src="images/patrick-final.webp" alt="Patrick Klauser: final handwritten torque calculation." loading="lazy"><figcaption><strong>Figure 4.</strong> Patrick Klauser: final handwritten torque calculation. <a href="images/patrick-final.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

## Nut and flange analysis — Antonio Chiocca

We selected bronze nut 95072A881 and mounting flange 95082A641. The nut’s internal 1/4″-16 Acme thread matches the screw, and its external 9/16″-18 thread fits the flange. Four mounting bolts at each flange transfer the screw reaction into the crosshead.

<div class="a10-pair"><figure class="a10-figure cad" id="a10-figure-5"><img src="images/nut.webp" alt="Imported externally threaded bronze nut, McMaster 95072A881." loading="lazy"><figcaption><strong>Figure 5.</strong> Imported externally threaded bronze nut, McMaster 95072A881. <a href="images/nut.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure><figure class="a10-figure cad" id="a10-figure-6"><img src="images/flange.webp" alt="Imported nut mounting flange, McMaster 95082A641." loading="lazy"><figcaption><strong>Figure 6.</strong> Imported nut mounting flange, McMaster 95082A641. <a href="images/flange.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure></div>

### Internal thread bending

The worksheet assumes F = 224.81 lbf per nut, p = 0.0625 in, engagement length L<sub>e</sub> = 0.375 in, and equal loading across six threads. It uses d<sub>r</sub> = 0.161 in for the bending-strip circumference. This is a conservative worksheet idealization; the actual nut-root diameter and thread thickness were not verified. Unknowns: bending stress under that model and required yield strength.

<div class="a10-eq">
N<sub>t</sub> = L<sub>e</sub>/p = 0.375/0.0625 = <strong>6 threads</strong><br>
F<sub>thread</sub> = F/N<sub>t</sub><br>
M<sub>thread</sub> = (F/N<sub>t</sub>)(p/4)<br>
Z<sub>thread</sub> = (πd<sub>r</sub>)(p/2)²/6<br>
σ<sub>b</sub> = M/Z = <strong>6F/(N<sub>t</sub>πd<sub>r</sub>p)</strong><br><br>
σ<sub>b</sub> = 6(224.81)/[6π(0.161)(0.0625)] = <strong>7.111 ksi</strong><br>
Required S<sub>y,nut</sub> ≥ nσ<sub>b</sub> = 4(7.111) = <strong>28.45 ksi</strong>
</div>

The calculated bending stress is 7.111 ksi. A safety factor of 4 requires a nut yield strength of at least 28.45 ksi under this equal-thread-loading model. A verified nut yield strength was not recorded, so a numerical nut safety factor is not reported.

<figure class="a10-figure handwork" id="a10-figure-7"><img src="images/aj-nut-crosshead.webp" alt="Antonio Chiocca: nut-thread bending, crosshead sizing, and support sketches." loading="lazy"><figcaption><strong>Figure 7.</strong> Antonio Chiocca: nut-thread bending, crosshead sizing, and support sketches. <a href="images/aj-nut-crosshead.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

## Crosshead beam analysis — Antonio Chiocca

We used the flange diameter to establish a minimum crosshead width. The selected flange is 1 39/64 in, or 1.6094 in, in diameter. A 2-in width gives room around that interface. The drawing places the screw centers 6 in apart within an 8-in overall length; the outer 1-in portions extend beyond the screw centers.

Knowns: W = 2,000 N, support span L = 152.4 mm, width b = 50.8 mm, and crosshead thickness h = 14.3002 mm (0.563 in). The worksheet uses E = 9,993.1 ksi, approximately 68,900 MPa, for 6061 aluminum. Unknowns: bending stress and center deflection.

### Bending strength

For a simply supported beam with a centered point load:

<div class="a10-eq">
R<sub>L</sub> = R<sub>R</sub> = W/2 = <strong>1,000 N</strong><br>
M<sub>max</sub> = WL/4 = <strong>76,200 N·mm</strong><br>
I = bh³/12 = <strong>12,379.7 mm⁴</strong>; c = h/2<br>
σ<sub>max</sub> = Mc/I = 3WL/(2bh²)<br>
σ<sub>max</sub> = <strong>44.01 MPa</strong>
</div>

The beam calculation uses the gross cross section. We examined the mounting-hole stress concentrations separately in FEA.

### Deflection and support restraint

The original worksheet uses WL³/(384EI), which is not the center-point-load equation. For the centered specimen load, the corrected equations are:

<div class="a10-eq">
Simply supported: δ<sub>max</sub> = WL³/(48EI) = WL³/(4Ebh³)<br>
δ<sub>simple</sub> = <strong>0.1729 mm</strong><br>
<br>
Fully fixed ends: δ<sub>max</sub> = WL³/(192EI)<br>
δ<sub>fixed</sub> = <strong>0.04323 mm</strong>
</div>

The worksheet’s initial sizing result is approximately 0.560 in; the CAD drawing specifies 0.563 in. Recalculating the center-point-load deflection at the CAD dimensions gives 0.1729 mm for simple supports and 0.04323 mm for fixed ends. Only the fixed-end result meets the 0.100-mm limit, so the mounting restraint affects the conclusion.

<figure class="a10-figure handwork" id="a10-figure-8"><img src="images/aj-screw.webp" alt="Antonio Chiocca: screw-load FBD, axial sizing, rotational speed, and torque working." loading="lazy"><figcaption><strong>Figure 8.</strong> Antonio Chiocca: screw-load FBD, axial sizing, rotational speed, and torque working. <a href="images/aj-screw.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

## CAD assembly and drawing — Rick Bhattacharya

We imported the McMaster screws, nuts, flanges, and T-slot framing, then modeled the crosshead around the two flange interfaces.

| Component | Source / design role |
|---|---|
| Lead screws | [99030A981](https://www.mcmaster.com/99030A981/), two 18-in precision Acme screws in CAD |
| Bronze nuts | [95072A881](https://www.mcmaster.com/95072A881/), two |
| Mounting flanges | [95082A641](https://www.mcmaster.com/95082A641/), two |
| Short framing members | [47065T414](https://www.mcmaster.com/47065T414/), imported 1-ft framing |
| Uprights | [47065T21](https://www.mcmaster.com/47065T21/), imported 2-ft framing |
| Crosshead | Custom 6061 aluminum component |

<figure class="a10-figure cad" id="a10-figure-9"><img src="images/interface.webp" alt="Underside of the crosshead showing the two nut/flange interfaces and screw-clearance locations." loading="lazy"><figcaption><strong>Figure 9.</strong> Underside of the crosshead showing the two nut/flange interfaces and screw-clearance locations. <a href="images/interface.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

The crosshead has two Ø0.255-in screw-clearance holes and eight Ø0.26-in mounting holes. The mounting-hole groups sit around the two screw axes. The original plate had square outside corners; the revision rounds those corners while retaining the two mounting regions.

<div class="a10-pair"><figure class="a10-figure cad" id="a10-figure-10"><img src="images/original.webp" alt="Initial crosshead with square outside corners and two flange-hole groups." loading="lazy"><figcaption><strong>Figure 10.</strong> Initial crosshead with square outside corners and two flange-hole groups. <a href="images/original.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure><figure class="a10-figure cad" id="a10-figure-11"><img src="images/revised.webp" alt="Revised crosshead with rounded outside corners. The mounting regions and hole groups are retained." loading="lazy"><figcaption><strong>Figure 11.</strong> Revised crosshead with rounded outside corners. The mounting regions and hole groups are retained. <a href="images/revised.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure></div>

### Crosshead multiview drawing

The crosshead drawing includes top, front, side, and isometric views, overall dimensions, screw spacing, and hole diameters.

<div class="a10-pdf"><a class="a10-pdf-title" href="files/Crosshead.pdf">Crosshead drawing · PDF</a><img class="a10-pdf-page" src="images/drawing-page.png" alt="Crosshead drawing, rendered directly from the original PDF" loading="lazy"><details class="a10-reader"><summary>PDF viewer with zoom controls</summary><object type="application/pdf" data="files/Crosshead.pdf" aria-label="Crosshead drawing" width="100%" height="650"><a href="files/Crosshead.pdf">Open PDF</a></object></details></div>

### Parameters and interface intent

The crosshead uses a 6-in screw-center spacing and two matching flange-hole patterns. The Ø0.255-in center holes provide screw clearance; the eight Ø0.26-in holes attach the flanges. The specimen load acts midway between the screw axes.

## Crosshead FEA and geometry revision — Rick Bhattacharya, Patrick Klauser, and Antonio Chiocca

We compared the initial plate and the rounded-corner revision using static stress results in Fusion. The design load path is a centered 2-kN specimen force into the crosshead, balanced by reactions through the nut/flange mounting regions. The constraint symbols in the recorded plots are located at the mounting holes. These idealized restraints represent the local attachment regions rather than the flexibility of the entire tester frame.

### Recorded results

| Metric | Initial plate | Rounded-corner revision |
|---|---:|---:|
| Maximum von Mises stress | 2.853 ksi / 19.67 MPa | 3.557 ksi / 24.52 MPa |
| Maximum plotted resultant displacement | Approximately 0.003 mm | Approximately 0.012 mm |
| Minimum FOS | Not numerically recorded | 11.212 |
| Critical stress region | Near the flange mounting holes | Near the flange mounting holes |
| Largest displacement region | Between the mounting regions | Between the mounting regions |

The rounded-corner study showed **24.7% higher peak stress** and approximately four times the displacement of the initial study. The revised study reports a minimum FOS of 11.212 and maximum resultant displacement of approximately 0.012 mm. These are results for the recorded model; the applied load and vertical grip displacement were not separately documented.

<div class="a10-pair"><figure class="a10-figure cad" id="a10-figure-12"><img src="images/stress-before.webp" alt="Initial study: maximum von Mises stress 2.853 ksi. The strongest stress concentrations are near mounting holes. The displayed deformation is exaggerated." loading="lazy"><figcaption><strong>Figure 12.</strong> Initial study: maximum von Mises stress 2.853 ksi. The strongest stress concentrations are near mounting holes. The displayed deformation is exaggerated. <a href="images/stress-before.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure><figure class="a10-figure cad" id="a10-figure-13"><img src="images/stress-after.webp" alt="Revised study: maximum von Mises stress 3.557 ksi. The critical region remains near the attachment holes. The apparent curvature is the displayed deformation." loading="lazy"><figcaption><strong>Figure 13.</strong> Revised study: maximum von Mises stress 3.557 ksi. The critical region remains near the attachment holes. The apparent curvature is the displayed deformation. <a href="images/stress-after.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure></div>

<div class="a10-pair"><figure class="a10-figure cad" id="a10-figure-14"><img src="images/disp-before.webp" alt="Initial study: maximum plotted resultant displacement approximately 0.003 mm." loading="lazy"><figcaption><strong>Figure 14.</strong> Initial study: maximum plotted resultant displacement approximately 0.003 mm. <a href="images/disp-before.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure><figure class="a10-figure cad" id="a10-figure-15"><img src="images/disp-after.webp" alt="Revised study: maximum plotted resultant displacement approximately 0.012 mm." loading="lazy"><figcaption><strong>Figure 15.</strong> Revised study: maximum plotted resultant displacement approximately 0.012 mm. <a href="images/disp-after.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure></div>

<div class="a10-pair"><figure class="a10-figure cad" id="a10-figure-16"><img src="images/fos-before.webp" alt="Initial safety-factor plot. The upper legend value is 8; an exact numerical minimum was not recorded." loading="lazy"><figcaption><strong>Figure 16.</strong> Initial safety-factor plot. The upper legend value is 8; an exact numerical minimum was not recorded. <a href="images/fos-before.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure><figure class="a10-figure cad" id="a10-figure-17"><img src="images/fos-after.webp" alt="Revised safety-factor plot. The target is 4, and the displayed blue field is above the upper scale." loading="lazy"><figcaption><strong>Figure 17.</strong> Revised safety-factor plot. The target is 4, and the displayed blue field is above the upper scale. <a href="images/fos-after.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure></div>

<figure class="a10-figure cad" id="a10-figure-18"><img src="images/fos-detail.webp" alt="Revised study result panel: minimum safety factor 11.212, based on yield strength." loading="lazy"><figcaption><strong>Figure 18.</strong> Revised study result panel: minimum safety factor 11.212, based on yield strength. <a href="images/fos-detail.webp" target="_blank" rel="noopener">Full size</a>.</figcaption></figure>

The initial FOS plot is capped at 8; its exact minimum was not recorded. Crosshead mass and volume changes were not recorded. Peak stress remains near the attachment holes, and displacement is greatest between the supports. The plots show resultant displacement; vertical grip displacement and twisting were not measured separately.

### Interpretation of the studies

Mesh-refinement results and element counts were not recorded. The response plots also do not show the applied load magnitude. These two geometry studies therefore document the recorded before-and-after response without establishing mesh convergence. [Fusion mesh convergence guidance](https://help.autodesk.com/cloudhelp/ENU/Fusion-Simulate/files/SIM-MESH-CONVERGENCE.htm).

The beam and FEA results depend on the support restraints and applied load. The recorded plots do not establish that both FEA studies used the same 2-kN load.

## Bill of materials

The purchased components total **$299.91**, excluding crosshead material and machining.

| Item | Quantity | Component | Cost per item | Line total | Purchase link |
|---|---:|---|---:|---:|---|
| 1 | 1 | 36-in Acme lead screw stock | $12.74 | $12.74 | [98935A803](https://www.mcmaster.com/98935A803/) |
| 2 | 2 | Nut mounting flange | $37.06 | $74.12 | [95082A641](https://www.mcmaster.com/95082A641/) |
| 3 | 2 | Bronze lead screw nut | $35.78 | $71.56 | [95072A881](https://www.mcmaster.com/95072A881/) |
| 4 | 5 | 1-ft T-slot framing member | $17.15 | $85.75 | [47065T414](https://www.mcmaster.com/47065T103-47065T414/) |
| 5 | 2 | 2-ft T-slot framing member | $27.87 | $55.74 | [T-slot framing](https://www.mcmaster.com/products/extrusions/t-slotted-framing-rails-1~~/) |
| | | **Total** | | **$299.91** | |

The BOM lists one 36-in stock screw; the CAD uses two 18-in precision screws. These are different catalog selections. Two finished 18-in screws require stock allowance for cutting.

<div class="a10-pdf"><a class="a10-pdf-title" href="files/A10-BOM.pdf">Bill of materials · PDF</a><img class="a10-pdf-page" src="images/bom-page.png" alt="Bill of materials, rendered directly from the original PDF" loading="lazy"><details class="a10-reader"><summary>PDF viewer with zoom controls</summary><object type="application/pdf" data="files/A10-BOM.pdf" aria-label="Bill of materials" width="100%" height="650"><a href="files/A10-BOM.pdf">Open PDF</a></object></details></div>

## Lessons learned

Splitting the specimen load between two screws simplified the axial sizing, but it did not remove the need to define the support arrangement. The root diameter carries the axial stress, and the mean thread diameter enters the torque calculation. Using the outside diameter for both would hide that difference.

The speed calculation was sensitive to units. Dividing mm/min by mm/revolution gives rpm directly. Converting that result into radians per second requires an additional factor of 2π/60. Writing the units at each step caught the mislabeled intermediate result in our first worksheet.

The crosshead work showed why support conditions belong beside the result. The same plate gives a different deflection when its ends can rotate than when its mounting regions are fixed. A small displacement in the solver does not explain that restraint by itself.

Rounding the outside corners changed the recorded response, but the peak stress stayed near the flange holes. That made the connection regions the main focus of our interpretation. The rounded-corner revision showed higher stress and displacement in the recorded studies.

**Total time spent: 10 hours.**

## CAD files and supporting documents

| File | Contents |
|---|---|
| [Tester assembly — Fusion F3Z](files/tensile-tester.f3z) | Assembly archive with its referenced components |
| [Crosshead — Fusion F3D](files/crosshead.f3d) | Crosshead CAD model |
| [Original drawing export](files/Crosshead.pdf) | Original multiview drawing by Rick Bhattacharya |
| [Bill of materials](files/A10-BOM.pdf) | Original cost sheet |
| [Bill of materials CSV](files/A10-BOM.csv) | Editable, typed cost table with purchase links |
| [Submission PDF](files/A10-team-report.pdf) | Team report, calculations, figures, and original drawing |
| [Original handwritten work](files/A10-original-work.zip) | The five original calculation photographs |

## References

- MEGR 2156/2157, *Lead Screw System Design Part 1*: assignment requirements, load, speed range, safety factor, and crosshead deflection limit.
- [McMaster precision Acme screws and nuts](https://www.mcmaster.com/products/lead-screws/thread-size~1-4-16/): thread compatibility, selected screw and bronze nut.
- [McMaster nut mounting flanges](https://www.mcmaster.com/products/nonmetallic-acme-nuts/): 95082A641 mounting dimensions.
- [Roton Acme engineering data](https://www.roton.com/products/acme-lead-screws-nuts/engineering-data/): reference root diameter and screw/nut selection context. Roton values are not a certification of a different manufacturer's screw.
- [Online Metals 1018 guide](https://www.onlinemetals.com/en/product-guide/alloy/1018): reference steel properties.
- [IARE Machine Design course notes](https://www.iare.ac.in/sites/default/files/COURSE%20RESOURCES.pdf), pp. 190–195: Acme thread angle and corrected thread torque.
- [Autodesk power-screw calculation](https://help.autodesk.com/cloudhelp/2016/ENU/InventorLT-Help/files/GUID-149FFEF7-5A5A-482D-98DC-97F6958898D4.htm): mean screw diameter, thread-angle correction, and strength checks.
- [SOLIDWORKS von Mises criterion](https://help.solidworks.com/2022/english/solidworks/cworks/r_Maximum_von_Mises_Stress_Criterion.htm): combined-stress yield check.
- [Missouri S&T mechanics formula sheet](https://web.mst.edu/jthomas/classes/2210/formulas/formula_sheet.pdf): bending and center-point-load deflection equations.
- [Autodesk Fusion mesh convergence](https://help.autodesk.com/cloudhelp/ENU/Fusion-Simulate/files/SIM-MESH-CONVERGENCE.htm): refinement and consistent-location stress comparison.
