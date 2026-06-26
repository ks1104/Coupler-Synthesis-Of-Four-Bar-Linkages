# Coupler Synthesis of Planar Four-Bar Linkages

<p align="center">

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![GitHub Pages](https://img.shields.io/badge/Hosted_on-GitHub_Pages-222222?style=for-the-badge&logo=github)

</p>

An interactive web application for the **graphical synthesis, visualization, and kinematic analysis of planar four-bar linkages**.

The simulator combines classical graphical synthesis techniques taught in **Machines and Mechanisms** with modern browser-based visualization, allowing users to construct, analyze and animate mechanisms entirely within the browser.

Unlike conventional textbook figures, every construction is performed interactively and updates instantly as the geometry changes, making the application equally useful for education, experimentation and design exploration.

---

# 🌐 Live Demo

### Open the application

**https://ks1104.github.io/Coupler-Synthesis-Of-Four-Bar-Linkages/**

The website contains both

- Four-Position Coupler Synthesis
- Five-Position (Point Position Reduction) Coupler Synthesis

accessible from a single interface.

---

# Table of Contents

- Overview
- Features
- How the Software Works
- Four-Point Synthesis
- Five-Point (PPR) Synthesis
- Construction Procedure
- User Guide
- Mathematical Background
- Technologies Used
- Repository Structure
- Future Improvements
- References

---

# Overview

Graphical synthesis is one of the oldest and most elegant methods of designing mechanisms.

Given a finite number of prescribed positions of a coupler point, the objective is to construct a planar four-bar linkage capable of reproducing those positions.

Traditionally, this process is performed using

- ruler
- compass
- tracing paper
- perpendicular bisectors
- geometric inversion

Although conceptually beautiful, these constructions become difficult to visualize after only a few steps.

This project digitizes the complete construction procedure while preserving the original graphical methodology.

Instead of hiding the mathematics inside numerical optimization algorithms, every geometric construction is displayed exactly as it would be performed on paper.

Users can freely modify the construction and immediately observe how each design choice affects the final mechanism.

---

# Major Features

## Interactive Precision Point Editor

The prescribed precision positions (C1, C2, C3, C4 and C5) can be dragged anywhere on the workspace.

Every movement automatically updates

- all construction circles
- perpendicular bisectors
- crank locations
- rocker locations
- inversion points
- coupler geometry
- mechanism animation
- CAD analysis

This allows users to understand how changing the desired coupler positions influences the synthesized mechanism.

Unlike static textbook examples, every geometric dependency is recomputed in real time.

---

## Automatic Mid-Normal (Perpendicular Bisector) Construction

The application automatically constructs the perpendicular bisector of every selected precision-point pair.

For two precision positions

```
C1 -------- C3
```

their perpendicular bisector

```
        |
        |
--------+--------
        |
        |
```

contains every point that is equally distant from C1 and C3.

In graphical synthesis, this property is fundamental because the rocker ground pivot must remain equidistant from the selected precision positions.

The software visualizes these bisectors automatically, allowing users to understand why the ground pivots must lie on these lines.

---

## Multiple Construction Configurations

Different selections of precision-point pairs lead to different graphical constructions.

For four-position synthesis, the software supports all six valid combinations.

• C1 – C2

• C1 – C3

• C1 – C4

• C2 – C3

• C2 – C4

• C3 – C4

Similarly, the Point Position Reduction algorithm implements all fifteen valid pair combinations for five-position synthesis.

Changing the configuration instantly reconstructs the entire mechanism.

This enables users to compare different graphical solutions corresponding to the same prescribed positions.

---

## Arbitrary Ground Pivot Selection

One of the strongest features of the simulator is the ability to move the ground pivots.

For four-position synthesis,

the rocker pivot (HR)

and

the crank pivot (HC)

can be positioned anywhere along their respective perpendicular bisectors.

Changing either pivot affects

- crank length
- rocker length
- coupler length
- transmission angle
- Grashof condition
- coupler trajectory
- workspace

Users can therefore study how small geometric changes influence the performance of the entire linkage.

For five-position synthesis, the ground pivots are automatically determined by the Point Position Reduction construction.

---

## Adjustable Construction Radii

Classical graphical synthesis requires arbitrary construction circles.

The application allows users to modify

• Coupler Radius (r)

• Rocker Radius (R)

exactly as would be done using a compass.

Changing either radius produces an entirely different linkage while satisfying the same prescribed positions.

Every geometric construction updates instantly.

Whenever the chosen radius produces an impossible construction, the simulator reports the error instead of producing an invalid mechanism.

---

## Circle–Circle and Line–Circle Intersection Solver

Almost every graphical construction relies on geometric intersections.

The software analytically computes

• Circle–Circle Intersections

• Line–Circle Intersections

• Circumcenters

• Midpoints

• Perpendicular Bisectors

• Rigid Body Rotations

• Kinematic Inversion

All calculations are performed directly from geometric relationships instead of relying on numerical approximations.

Whenever two construction circles fail to intersect, the application immediately displays

"Invalid Geometry"

preventing impossible constructions from propagating further.
## Multiple Assembly Branches

Graphical synthesis rarely produces a unique solution. Most geometric constructions involve the intersection of circles, and every circle-circle intersection yields two possible points. As a result, a single synthesis problem may produce multiple mathematically valid four-bar mechanisms.

The simulator computes **all feasible assembly branches** and allows the user to switch between them instantly without repeating the construction.

The available branches include

- Upper and lower circle intersections
- Elbow-up and elbow-down configurations
- Alternate assembly modes

This feature is particularly useful for comparing different linkage geometries that satisfy exactly the same precision positions.

---

## Automatic Kinematic Inversion

Kinematic inversion is one of the central ideas in graphical mechanism synthesis.

Instead of solving for the rocker point directly, one precision position is held fixed while the remaining rigid bodies are rotated back into the reference frame. The transformed (inverted) positions are then used to determine the final rocker location.

The simulator performs this entire process automatically while simultaneously visualizing each intermediate construction.

The inversion process consists of

1. Choosing the reference precision position.
2. Holding that rigid body fixed.
3. Rotating every remaining position back into the reference frame.
4. Computing the inverted locations.
5. Constructing the circumcenter of the inverted points.
6. Determining the rocker point.

Since every inversion step is displayed graphically, users can understand the geometric reasoning behind the construction instead of treating it as a hidden computation.

---

## Complete Mechanism Animation

After synthesis, the constructed linkage can be animated continuously.

The animation accurately reproduces the motion of the synthesized four-bar mechanism and displays

- Input crank rotation
- Coupler motion
- Rocker oscillation
- Coupler-point trajectory
- Instantaneous linkage configuration

Users may

- Start or pause the animation
- Adjust simulation speed
- Switch between solution branches
- Observe the coupler curve as it is generated

The animation provides immediate visual confirmation that the synthesized linkage passes through the prescribed precision positions.

---

## Coupler Curve Generation

As the mechanism rotates, the trajectory traced by the coupler point is generated automatically.

The resulting coupler curve enables users to

- verify the generated motion,
- compare different linkage designs,
- visualize the synthesized path,
- estimate the mechanism's reachable workspace.

Because the coupler path is updated in real time, users can immediately observe how changing the construction parameters modifies the generated motion.

---

## Grashof Condition Analysis

One of the most important design checks performed by the simulator is the automatic evaluation of the **Grashof Criterion**.

After synthesis, the application computes the lengths of

- Ground Link
- Crank
- Coupler
- Rocker

These four lengths are sorted from shortest to longest.

The classical Grashof condition

```
Shortest Link + Longest Link <= Remaining Two Links
```

is then evaluated.

If the condition is satisfied, the linkage is classified as a **Grashof Linkage**, meaning that at least one link is capable of making a complete revolution.

Otherwise, the linkage is classified as **Non-Grashof**, indicating that all links merely oscillate.

Since the classification updates instantly whenever the geometry changes, users can investigate how moving pivots or changing radii affects linkage mobility.

---

## Transmission Angle Analysis

Efficient transmission of force depends strongly on the transmission angle.

For every configuration of the mechanism, the simulator continuously computes the transmission angle and reports

- Minimum transmission angle
- Maximum transmission angle

Mechanisms with extremely small or extremely large transmission angles are generally poor designs because force transmission becomes inefficient.

Displaying these values allows users to judge the quality of a synthesized mechanism instead of relying solely on geometric appearance.

---

## Workspace Estimation

As the coupler point moves, the simulator records its complete trajectory.

The minimum and maximum coordinates of this trajectory are then used to determine the workspace occupied by the coupler.

The CAD analysis panel reports

- Overall width
- Overall height
- Bounding box dimensions

allowing users to estimate the space required by the mechanism.

---

## Order Defect Detection

A mechanism should visit the prescribed precision positions in the intended sequence.

Although a synthesis may be geometrically valid, the crank may encounter the precision positions in the wrong order, making the mechanism unsuitable for practical applications.

The simulator automatically checks the angular ordering of all synthesized crank positions.

Whenever the ordering is violated, an **Order Defect** warning is displayed.

This feature is especially useful for students learning that a mathematically valid solution is not always a functionally correct mechanism.

---

## Real-Time Geometry Validation

During synthesis, every geometric construction is verified before it is accepted.

The application automatically detects

- Non-intersecting construction circles
- Impossible crank locations
- Degenerate circumcenters
- Invalid inversion geometry
- Impossible tracing-paper constructions
- Inconsistent linkage configurations

Instead of silently producing incorrect results, the simulator displays an informative **Invalid Geometry** message, allowing the user to modify the construction until a valid mechanism is obtained.

---

## CAD-Style Kinematic Dashboard

The application contains a continuously updating analysis panel that summarizes the most important characteristics of the synthesized linkage.

The dashboard displays

- Ground link length
- Crank length
- Coupler length
- Rocker length
- Grashof classification
- Minimum transmission angle
- Maximum transmission angle
- Order defect status
- Workspace dimensions

Every value updates automatically whenever

- a precision point is moved,
- a radius is changed,
- a construction configuration is selected,
- a synthesis branch is switched,
- the linkage is regenerated.

The dashboard transforms the simulator from a simple visualization tool into an interactive mechanism analysis package.

---

# How the Software Works

The application follows the same sequence of operations used in classical graphical synthesis.

```
User selects synthesis method
            │
            ▼
Choose construction configuration
            │
            ▼
Place or adjust precision points
            │
            ▼
Construct perpendicular bisectors
            │
            ▼
Locate ground pivots
            │
            ▼
Construct circles
            │
            ▼
Compute crank locations
            │
            ▼
Perform kinematic inversion
            │
            ▼
Locate rocker point
            │
            ▼
Construct complete linkage
            │
            ▼
Perform kinematic analysis
            │
            ▼
Animate mechanism
```

Every stage of the construction is visible to the user, making the software an effective educational tool for understanding graphical synthesis.
# Four-Position Coupler Synthesis

The Four-Position module implements the classical **Circle-Point Circle-Point graphical synthesis** technique used in planar mechanism design.

The objective is to construct a four-bar linkage capable of guiding a coupler point through four prescribed precision positions.

Unlike numerical optimization methods, this approach relies entirely on geometric constructions such as perpendicular bisectors, circle intersections, rigid-body transformations and kinematic inversion.

The simulator reproduces these constructions exactly as they would be performed using a ruler and compass while allowing every intermediate step to be visualized interactively.

---

## Construction Procedure

### Step 1 — Select the Base Point Pair

Choose one of the six possible precision-point pairs.

The selected pair determines the primary construction bisector and consequently influences the final linkage geometry.

Different selections generally produce different valid mechanisms.

---

### Step 2 — Construct the Mid-Normal

The simulator constructs the perpendicular bisector of the selected precision-point pair.

Every point on this line is equidistant from the two selected precision positions.

This property is fundamental because the rocker ground pivot must satisfy this geometric condition.

---

### Step 3 — Locate the Rocker Ground Pivot (HR)

The rocker ground pivot may be placed anywhere along the constructed mid-normal.

Changing its position directly affects

- Ground link length
- Rocker length
- Crank length
- Coupler orientation
- Transmission angle
- Grashof classification

This freedom allows users to investigate many different mechanisms satisfying the same precision positions.

---

### Step 4 — Construct the Rocker Circle

Using HR as the center, a construction circle of arbitrary radius R is drawn.

This circle is used to determine the rocker joints corresponding to the selected precision positions.

---

### Step 5 — Locate the First Crank Positions

Construction circles of radius r are drawn around the selected precision positions.

The intersections of these circles with the rocker circle determine the first crank locations.

Since every circle-circle intersection has two mathematical solutions, multiple branches become possible.

---

### Step 6 — Construct the Crank Mid-Normal

The first crank locations are joined and their perpendicular bisector is constructed.

The crank ground pivot HC must lie on this bisector because it must remain equidistant from the selected crank positions.

---

### Step 7 — Locate the Crank Ground Pivot (HC)

The crank ground pivot may now be positioned anywhere along the crank bisector.

Moving HC changes the entire mechanism geometry while preserving the graphical construction procedure.

---

### Step 8 — Draw the Crank Circle

Using HC as the center, the crank circle is constructed through the first crank locations.

---

### Step 9 — Determine Remaining Crank Positions

The remaining crank locations are determined by intersecting the crank circle with construction circles centered at the remaining precision positions.

---

### Step 10 — Construct the Rigid Bodies

Each precision position together with its corresponding crank location and rocker pivot forms a rigid body.

These rigid bodies represent the moving coupler in different positions.

---

### Step 11 — Perform Kinematic Inversion

One rigid body is held fixed.

All remaining bodies are rotated back into the reference frame.

This produces the inverted locations required for the final rocker construction.

---

### Step 12 — Construct the Rocker Point

The circumcenter of the inverted positions determines the rocker point.

Once this point has been obtained, the four-bar linkage is completely defined.

---

### Step 13 — Analyze the Linkage

The application automatically computes

- Link lengths
- Grashof condition
- Transmission angles
- Workspace
- Order defects

---

### Step 14 — Animate the Mechanism

The completed linkage can now be animated continuously while the CAD dashboard updates in real time.

---

# Five-Position Coupler Synthesis

The second module implements the **Point Position Reduction (PPR)** method.

Direct graphical synthesis for five prescribed positions is considerably more complicated than the four-position problem.

Point Position Reduction overcomes this difficulty by reducing the five-position problem into an equivalent four-position construction through the use of tracing-paper transformations.

The application implements this complete procedure interactively.

---

## Construction Procedure

### Step 1 — Select the Configuration

The simulator provides all fifteen valid Point Position Reduction configurations.

Each configuration specifies two independent precision-point pairs together with one remaining position.

---

### Step 2 — Construct Two Mid-Normals

The perpendicular bisectors of both selected point pairs are constructed.

The intersection of these bisectors uniquely determines the rocker ground pivot HR.

Unlike the four-position method, the user does not manually choose HR.

---

### Step 3 — Create the Tracing Paper

The tracing-paper construction is simulated digitally.

The selected bisectors and reference directions are copied onto the virtual tracing paper exactly as performed in manual graphical synthesis.

---

### Step 4 — Align the Tracing Paper

The tracing paper is aligned with the second bisector.

This transfers the geometric relationships from one pair of positions to another.

---

### Step 5 — Apply an Arbitrary Rotation

The tracing paper is rotated through a user-defined angle.

Changing this rotation produces different valid mechanisms satisfying the same prescribed positions.

---

### Step 6 — Transfer Construction Lines

The rotated construction lines are projected back onto the workspace.

These transferred lines become the reference directions for locating the crank positions.

---

### Step 7 — Locate Crank Positions

Construction circles intersect the transferred lines to determine the first crank locations.

---

### Step 8 — Determine the Crank Pivot

The crank ground pivot HC is obtained from the intersection of the transferred construction line and the crank perpendicular bisector.

---

### Step 9 — Determine Remaining Crank Positions

The crank circle is used to locate the remaining crank positions.

---

### Step 10 — Construct Rigid Bodies

Rigid-body triangles are constructed for all prescribed positions.

---

### Step 11 — Perform Kinematic Inversion

The inversion process is carried out exactly as in the four-position synthesis.

---

### Step 12 — Locate the Rocker Point

The rocker point is obtained from the circumcenter of the inverted positions.

---

### Step 13 — Complete the Mechanism

The complete four-bar linkage satisfying all five prescribed positions is constructed.

---

### Step 14 — Animate and Analyze

The synthesized mechanism may now be animated while all kinematic properties are evaluated continuously.

---

# User Guide

## Choosing a Synthesis Method

The homepage contains both synthesis modules.

Users may switch between

- Four-Position Coupler Synthesis
- Five-Position Point Position Reduction

without leaving the application.

---

## Changing Precision Positions

Simply drag any precision point on the canvas.

Every geometric construction updates automatically.

---

## Selecting a Configuration

Use the configuration selector to explore different graphical constructions.

Different configurations may produce entirely different mechanisms satisfying exactly the same precision positions.

---

## Adjusting Construction Parameters

The sidebar allows modification of

- Coupler radius
- Rocker radius
- Ground pivot locations (Four-Point)
- Tracing paper rotation (Five-Point)

Changing these parameters immediately regenerates the mechanism.

---

## Navigating Construction Steps

The **Previous** and **Next** buttons allow users to inspect every stage of the graphical synthesis.

This makes the application suitable for classroom demonstrations and self-learning.

---

## Running the Simulation

Once synthesis is complete,

click **Run Mechanism**

to animate the linkage.

The simulation may be paused, resumed or replayed at any time.

---

## Switching Assembly Branches

Use the **Switch Branch** button to cycle through every feasible assembly mode.

This enables direct comparison between mathematically distinct linkage solutions.
# Mathematical Background

The simulator combines concepts from **graphical mechanism synthesis**, **computational geometry**, and **kinematic analysis**. Every construction performed by the application follows the same geometric principles used in classical mechanism design.

The principal mathematical concepts implemented include

- Euclidean Geometry
- Circle–Circle Intersection
- Line–Circle Intersection
- Perpendicular Bisectors (Mid-Normals)
- Circumcenter Construction
- Rigid Body Transformations
- Rotation Matrices
- Kinematic Inversion
- Coupler Curve Generation
- Transmission Angle Analysis
- Workspace Estimation
- Order Defect Detection
- Grashof Criterion

Unlike numerical optimization approaches, every result is obtained through explicit geometric constructions, making the software an excellent educational tool for understanding graphical synthesis.

---

# Interface Overview

The application consists of two primary regions.

## Sidebar

The sidebar contains

- Construction controls
- Parameter selection
- Configuration selector
- Step-by-step construction guide
- Animation controls
- Branch switching
- Simulation parameters

The sidebar dynamically updates according to the selected synthesis method.

---

## Canvas

The drawing canvas visualizes

- Precision positions
- Construction circles
- Mid-normals
- Ground pivots
- Crank pivots
- Rigid body triangles
- Inverted positions
- Final linkage
- Coupler trajectory
- Animated mechanism

All graphical elements update interactively as the user modifies the design.

---

## CAD Analysis Panel

The built-in CAD dashboard continuously evaluates the synthesized mechanism.

Displayed quantities include

- Ground link length
- Crank length
- Coupler length
- Rocker length
- Grashof classification
- Minimum transmission angle
- Maximum transmission angle
- Order defect status
- Workspace dimensions

The panel updates automatically after every modification, allowing immediate comparison between different linkage designs.

---

# Technologies Used

The project is implemented entirely using standard web technologies.

- HTML5
- CSS3
- JavaScript (ES6)
- HTML5 Canvas API

No external libraries or frameworks are used.

Every geometric construction, animation routine and analytical computation has been implemented from scratch.

---

# Repository Structure

```
Coupler-Synthesis-Of-Four-Bar-Linkages
│
├── index.html                  # Main application (4-Point & 5-Point Synthesizers)
├── README.md
│
└── Assets (optional)
    ├── screenshots
    └── images
```

---

# Future Improvements

Possible extensions of this project include

- SVG and PDF export of graphical constructions
- DXF export for CAD software
- Coupler curve export
- Cognate linkage generation
- Burmester curve visualization
- Six-position synthesis
- Motion optimization algorithms
- Dynamic force analysis
- Velocity and acceleration analysis
- Instant center visualization
- Interactive dimension annotations
- Dark mode interface
- Mobile responsive layout
- Mechanism saving/loading functionality

---

# References

1. G. N. Sandor and A. G. Erdman, *Mechanism Design: Analysis and Synthesis*.
2. Robert L. Norton, *Design of Machinery*.
3. J. J. Uicker, G. R. Pennock and J. E. Shigley, *Theory of Machines and Mechanisms*.
4. Ferdinand Freudenstein, *Approximate Synthesis of Four-Bar Linkages*.
5. ME252 – Machines and Mechanisms, Indian Institute of Technology Kanpur.

---



# Acknowledgements

This project was developed as part of the coursework for **ME252 – Machines and Mechanisms** at the **Indian Institute of Technology Kanpur**.

The work draws inspiration from the classical graphical synthesis methods taught in mechanism design literature while presenting them in an interactive, browser-based environment for improved visualization and understanding.

---

# Author

**Kshitij Jain**



---

## If you found this project useful

If this project helped you understand graphical synthesis or mechanism design,

⭐ **Star the repository**

and feel free to share feedback or suggestions for future improvements.

---

<p align="center">

**Interactive • Educational • Graphical • Analytical**

*A modern visualization of classical mechanism synthesis.*

</p>
