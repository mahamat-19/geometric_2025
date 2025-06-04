A JavaScript implementation of cubic (degree 3) B-spline interpolation with interactive HTML5 .
Features
•	Open index.html in your browser
•	Interactive control points: use the "Add" button to insert points.
•	visibility: Show/hide control points.
•	Curve updates in real time as points are added
•	Clear functionality: the "Clear" button resets the curve.
How It Works
The B-Spline algorithm computes a smooth curve from a set of control points using:
•	Cubic B-Spline basis functions for interpolation.
•	1. Sliding Window: For every consecutive 4 control points, it evaluates the B-spline using the cubic formula.
•	2. Cubic Formula:The B-spline basis is approximated with the following equation for each coordinate (x or y): JS Functıon Name: bSplineFormula

