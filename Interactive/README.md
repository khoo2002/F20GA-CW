# F20GA-CW
## Files structure
Inside the Code_Project will have a lamp.html(main file) and meshes folder. Inside the meshes folder is all the .obj(mesh) and .mtl(materials) components files.
```
Code_Project/
├── lamp.html
└── meshes/
    ├── lamp_body.obj
    ├── lamp_body.mtl
    ├── switch.obj
    ├── switch.mtl
    ├── pendants.obj
    ├── pendants.mtl
    ├── chains.obj
    └── chains.mtl
```
## Video Demo
### Part 1 and 2
This video introduces what we completed in Part 1 Importing and Drawing, and Part 2 Materials, Light and Shading.

https://github.com/user-attachments/assets/b5521c81-b7d2-48d1-be73-4b7ca0fb692d

If the video is not working, visit the microsoft stream link to view:
<a href="https://heriotwatt-my.sharepoint.com/:v:/g/personal/zk2022_hw_ac_uk/EevWhTyJmfJCqNiM796nc20B3iv1sr7PC8Co_DCLLtjMig?e=nrGDbW&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D">https://heriotwatt-my.sharepoint.com/:v:/g/personal/zk2022_hw_ac_uk/EevWhTyJmfJCqNiM796nc20B3iv1sr7PC8Co_DCLLtjMig?e=nrGDbW&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D</a>

### Part 3

## Part 1 Importing and Drawing
Step 1: Splitting and Optimizing the Model To ensure the imported model was efficient and performed well, I imported the lamp into Blender and used the Decimate Modifier to reduce the number of vertices on each part. Now the total is only 9601 vertices. This step optimized the model and reduced the load on the browser during rendering, which is crucial for performance.

![image](https://github.com/user-attachments/assets/bdc24d95-c71b-456d-8495-d65a8282f469)

Step 2: Exporting the Model Once the model was optimized and split into four parts, I exported each part into separate .obj files. To maintain material properties and other essential parameters, I made sure to export all relevant details, including colors and UV mappings. The files I ended up with were: chains.obj, lamp_body.obj, switch.obj, and pendants.obj.

![image](https://github.com/user-attachments/assets/bbf72fcf-818f-4d96-975c-fe3e5dc4c00b)

Step 3: Importing the Model into Three.js(WebGPU library) and WebGPU(WebGPU library) With the files ready, I wrote a js script to handle importing and setting up the model in the scene. The script starts by creating a basic Three.js scene with a plane and a camera to provide a view of the lamp. The plane acts as the ground, and the camera is positioned strategically to showcase the entire model.

![image](https://github.com/user-attachments/assets/37d2c109-068b-461e-8610-9af8c97bac1b)

Step 4: Assembling the Model To assemble the lamp, I added a BoxHelper around each part. This tool helped me visualize the boundaries of each object and ensured they were correctly aligned when placed in the scene. Adjustments to the position, scale, and rotation were made so that the parts fit together seamlessly, forming a single cohesive lamp.

![image](https://github.com/user-attachments/assets/af2a26b6-cb6f-49cf-9280-91198f378cd0)

## Part 2 Materials, Light and Shading.

![image](https://github.com/user-attachments/assets/3e1a0e6b-b770-4707-8eb4-9351424e4ffa)
![image](https://github.com/user-attachments/assets/1040c665-358f-4fe5-8c10-43a33baa8045)

Step 5: Setting Up Materials Now, while I exported materials correctly from Blender, I ran into an issue: Three.js doesn’t support some of the advanced material features. To solve this, I used MeshPhysicalMaterial, which is a versatile material type in Three.js, capable of simulating realistic properties like metalness and roughness. I created custom materials for the metal parts of the lamp and the diamond-like pendants. I also made sure to apply the correct colors, especially for the lamp cover, to replicate the design in the original model.

Step 6: Adding Lighting and Controls Lighting is vital for showcasing the model’s details, so I included a HemisphereLight for ambient illumination and a DirectionalLight for casting shadows and highlighting the model’s form. This setup allows the lamp to be seen in both lit and unlit conditions. To make navigation easier and more interactive, I incorporated OrbitControls, enabling us to pan, zoom, and rotate the camera to view the lamp from different angles.

## Part 3 Interactive Features

### 1. **Camera Circular Motion with Button Toggle**
   - **Functionality**: The camera moves in a circular motion around the lamp and always looks at it.

https://github.com/user-attachments/assets/4341e8df-c6d2-48dd-b4bc-574183e5b237

   - **Implementation**: 
     - The camera rotates around a defined center (main object) at a set radius using button toggles.
     - **Code Snippet**:
       ```javascript
       button.addEventListener("click", () => {
         cameraMotionEnabled = !cameraMotionEnabled;
         targetAngle = Math.atan2(camera.position.z, camera.position.y, camera.position.x);
         center = mainObjectPosition;
         radius = camera.position.distanceTo(center);
       });
       ```

### 2. **Zoom In/Out by Mouse Wheel**
   - **Functionality**: Zooms the camera in and out based on the mouse wheel.

https://github.com/user-attachments/assets/878ea0fb-83e0-46b2-9210-994f0f9ff02f

   - **Implementation**: 
     - Handled by `OrbitControls`, which manages mouse input for zooming and camera orientation adjustments.

### 3. **Drag to Rotate Around the Lamp**
   - **Functionality**: Allows the user to drag the camera around the lamp.

https://github.com/user-attachments/assets/428b20b7-eda0-452b-9cb9-661e09982d54

   - **Implementation**: 
     - **OrbitControls** allows the camera to be rotated around the center of the scene.
     - Mouse drag event is processed by `OrbitControls` for camera rotation.

### 4. **WASD Keyboard Movement**
   - **Functionality**: Allows the user to move the camera using the WASD keys.

https://github.com/user-attachments/assets/19bfd347-63f3-4691-96fb-8919430bf196

   - **Implementation**: 
     - `FlyControls` handles the movement when WASD or arrow keys are pressed.
     - FlyControls are activated/deactivated based on keyboard input.
     - **Code Snippet**:
       ```javascript
       window.addEventListener('keydown', (event) => {
         if (['KeyW', 'KeyA', 'KeyS', 'KeyD'].includes(event.code)) {
           isFlyControlActive = !isFlyControlActive;
         }
       });
       ```

### 5. **Button to Control the Light On/Off**
   - **Functionality**: Toggles the light on/off with a button.

https://github.com/user-attachments/assets/c81c8789-8ab1-476d-809a-9d3dbcabdc31

   - **Implementation**: 
     - A button toggles the light's intensity and updates the text to reflect the current state of the light.
     - **Code Snippet**:
       ```javascript
       button.addEventListener("click", () => {
         toggleLight();
         animatePullSwitch(loadedObjects._switch);
         button.innerText = isLightOn ? "Turn Off Light" : "Turn On Light";
       });
       ```

### 6. **Hover Effect on Light Switch with Tooltip**
   - **Functionality**: The light switch highlights when the mouse pointer hovers over it.
   - **Implementation**: 
     - Raycasting detects when the mouse is over the light switch and applies a highlight effect.
     - **Code Snippet**:
       ```javascript
       window.addEventListener('mousemove', onMouseMove, false);
       function onMouseMove(event) {
         raycaster.setFromCamera(mouse, camera);
         let intersects = [];
         loadedObjects._switch.children.forEach(child => {
           intersects = intersects.concat(raycaster.intersectObject(child));
         });
         highlightSwitch(intersects.length > 0);
       }
       ```

### 7. **Interact with Light Switch**
   - **Functionality**: Clicking the light switch toggles the light and animates the pulling of the switch.

https://github.com/user-attachments/assets/667cda63-f7a0-4f2a-83a6-f4d20e3f3ebc

   - **Implementation**: 
     - A click on the switch triggers a toggle for the light and animates the switch being pulled.
     - **Code Snippet**:
       ```javascript
       window.addEventListener('click', (event) => {
         if (clickedObjects.length > 0) {
           toggleLight();
           animatePullSwitch(loadedObjects._switch);
         }
       });
       ```
