# Shaders-Implementation-In_OpenGL

## Zoom Factor in Vertex Shader (vShader.glsl)
The zoom factor is a crucial parameter for controlling the scale of the solar system in the vertex shader. It enables zooming in and out of the rendered scene.

## How it Works
In the vertex shader (vShader.glsl), the zoom factor is utilized to create a scaling matrix that modifies the position attribute (posAttr). This scaling matrix is applied to the original transformation matrix (matrix), allowing dynamic adjustments to the scale of the rendered objects.

Here's the relevant code snippet from the main() function in vShader.glsl:
```bash
void main() {
   col = colAttr;

   // Create a scaling matrix for zooming
   highp mat4 zoomMatrix = mat4(
       zoom, 0.0, 0.0, 0.0,
       0.0, zoom, 0.0, 0.0,
       0.0, 0.0, zoom, 0.0,
       0.0, 0.0, 0.0, 1.0
   );

   // Combine the original matrix with the zoom matrix
   gl_Position = matrix * zoomMatrix * posAttr;
}
```
The `zoom` uniform is multiplied with the `posAttr` to effectively scale the position of each vertex based on the zoom factor. This results in the desired zooming effect in the rendered scene.

Adjust the `zoom` uniform in your C++ code to control the zoom level dynamically.

## Modifying the Zoom
To modify the zoom level programmatically, you can set the `zoom` uniform from your C++ code. The `setZoomFactor` function in `OpenGLWindow` class demonstrates how this can be achieved.
```bash
void OpenGLWindow::setZoomFactor(double zoomFactor)
{
    mZoomFactor = zoomFactor;
    update(); // Trigger a repaint after changing the zoom factor
}
```

## Demo Video

Watch a brief video demonstrating the zoom functionality in action.

<a href="https://youtu.be/6AYh69gFmtE">
  <img src="https://github.com/UmeshEkhande/Shaders-Implementation-In_OpenGL/blob/main/Resources/s3.png" alt="Zoom Demo" width="300" height="169">
</a>


**Video Description:**
- Demonstrates zooming in and out of the solar system.
- Shows the interactive controls for adjusting zoom levels.

Click on the thumbnail above to view the full video.


---

