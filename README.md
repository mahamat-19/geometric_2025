<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Python Spline Interpolation in Browser</title>
    <script src="https://cdn.jsdelivr.net/pyodide/v0.23.4/full/pyodide.js"></script>
  </head>
  <body>
    <h1>Spline Interpolation Calculator</h1>
    <p>
      Enter your x and y values as Python lists, like:
      <code>x = [1, 2, 3]; y = [1, 4, 9]</code>
    </p>
    <textarea
      id="input"
      rows="4"
      cols="50"
      placeholder="Enter data points here..."
    ></textarea
    ><br />
    <button id="runButton">Run Interpolation</button>
    <p><b>Output:</b></p>
    <div id="output"></div>

    <script>
      // Load Pyodide
      let pyodide;
      async function loadPyodideAndPackages() {
        pyodide = await loadPyodide();
        await pyodide.loadPackage(["numpy", "matplotlib", "scipy"]);
      }
      loadPyodideAndPackages();

      // Run Python code when button is clicked
      document.getElementById("runButton").onclick = async function () {
        const inputCode = document.getElementById("input").value;

        const pythonCode = `
import numpy as np
from scipy.interpolate import CubicSpline
import matplotlib.pyplot as plt
import io, base64

# Input data from user
${inputCode}

# Validate input
if len(x) != len(y):
    raise ValueError("x and y must have the same length")

# Perform cubic spline interpolation
cs = CubicSpline(x, y)
x_new = np.linspace(min(x), max(x), 100)
y_new = cs(x_new)

# Create plot
plt.figure()
plt.plot(x, y, 'o', label="Original Data Points")
plt.plot(x_new, y_new, label="Cubic Spline Interpolation")
plt.legend()
plt.title("Cubic Spline Interpolation")
plt.grid()

# Save plot as base64 string
buf = io.BytesIO()
plt.savefig(buf, format="png")
buf.seek(0)
img_str = "data:image/png;base64," + base64.b64encode(buf.read()).decode("utf-8")
buf.close()
img_str
            `;

        try {
          // Run the Python code
          const result = await pyodide.runPythonAsync(pythonCode);
          // Display the result as an image
          document.getElementById(
            "output"
          ).innerHTML = `<img src="${result}" alt="Spline Interpolation Result" />`;
        } catch (err) {
          // Display error messages
          document.getElementById("output").innerText = `Error: ${err}`;
        }
      };
    </script>
  </body>
</html>
