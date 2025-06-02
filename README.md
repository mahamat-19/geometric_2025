A JavaScript implementation of cubic (degree 3) B-spline interpolation with interactive HTML5 .
Features
•	Cubic B-spline interpolation (degree = 3)
•	Real-time curve calculation as points are added
•	Pure JavaScript implementation with no external dependencies
How It Works:
Usage
1.	Open index.html in your browser
2.	Interact with the visualization:
•	Use the "Add Point" button to add random points (as this is a cubic spline so click 3 times.)
•	Use the "Clear Points" button to start over
•	Use the checkboxes to show/hide control points and interpolation points
Implementation (the core purpose):
1.	Calculates the control points that make a B-spline pass exactly through these points
2.	Renders the smooth interpolating curve along with the original points
3.	The core algorithm consists of two main classes:
1.	BSplineInterpolator Class:
•	Handles the mathematical interpolation using cubic B-splines (degree = 3)
•	Solves the system of equations to find control points that make the curve pass through the given points
•	Uses Gaussian elimination for solving the linear system
2.	BSpline Class:
•	Evaluates the B-spline curve at any parameter t
•	Implements the basic functions recursively
•	Handles the knot vector (ensures smooth connection between curve sections) and parameter space
