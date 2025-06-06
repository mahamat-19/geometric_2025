Cubic B-Spline Curve Visualization
A web-based tool to create and interact with smooth B-Spline curves using control points.
Features
✔ Add & Move Points – Click "Add" to place points or drag them to change the curve shape.
✔ Clear Points – Click "Clear" to reset the canvas.
✔ Toggle Control Points – Show/hide control points with a checkbox.
How to Use
1.	Open index.html (Chrome, Firefox, Edge).
2.	Add points by clicking the "Add" button or clicking directly on the canvas.
3.	Drag points to see the curve update in real time.
4.	Click "Clear" to remove all points and start over.
How It Works
1) In the index.html file you can a B-spline approximation that:
•	creates control points and display them (by adding button).
•	The BSpline class uses these as control points to generate a B-spline curve using a basis function and a uniform knot vector.
•	The curve is recalculated every time the control points are changed.

2) In the Cbspline.html file you can see a cubic B-spline interpolation that :

•	Compute uniform knot vectors and B-spline basis functions (Cox-de Boor recursion).
•	Solving a linear system N⋅P=QN \cdot P = QN⋅P=Q to determine control points so that the B-spline passes through all interpolation points.
•	Drawing the resulting spline using standard cubic B-spline evaluation.
