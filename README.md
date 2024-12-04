# F20GA-CW
This coursework, we decided to create a detailed lamp model with animated and interactive features, ideal for use in an indoor scene.

# Model Components
The lamp is divided into five main parts:
1. Chains – Supporting chains that connect to the ceiling.
2. Lamp Cover – The outer shell surrounding the bulb.
3. Bulb – The light source.
4. Diamond Pendants – Decorative elements hanging below the lamp cover.
5. Pull-type Light Switch – Used to turn the light on and off.

# Scene Setup
A simple indoor layout with ceiling and walls.

# Animation Details
Two main animations are incorporated:
1. Light Switch Activation – Pulling the light switch turns the bulb on or off.
2. Swing Movement – Initiating a swing motion from the top chain to create a gentle swaying effect.

# Interactive Features
The process of importing and rendering the lamp model utilized two key WebGPU-based libraries:
1. WebGPU
2. Three.js

The process began with preparing the lamp model to ensure efficient rendering in a browser environment. Using Blender, the lamp's geometry was optimized by applying the Decimate Modifier, which reduced the total vertex count to 9601. This significantly improved performance by lowering computational demands. The model was then divided into four components—chains, lamp body, switch, and pendants—and exported as individual .obj files. During export, special care was taken to preserve material properties, UV mappings, and essential parameters to retain the visual fidelity of the original design.

Once the files were ready, a Three.js script was used to create a scene leveraging the WebGPU renderer for improved performance and realism. The setup included a ground plane and a strategically placed camera for an optimal view of the assembled lamp. Each component of the lamp was imported and aligned using BoxHelper, which visualized the boundaries and helped in precise adjustments to position, scale, and rotation. This meticulous alignment ensured that the lamp was reassembled seamlessly, resulting in a unified and visually accurate model in the scene.

To achieve a realistic appearance, materials were recreated in Three.js using MeshPhysicalMaterial, which supports advanced properties like metalness and roughness. Custom materials were crafted for the metallic sections of the lamp and its diamond-like pendants, with particular attention to replicating the lamp cover’s original design. Lighting played a key role in highlighting the model, combining a HemisphereLight for ambient illumination and a DirectionalLight for dramatic shadows. Finally, OrbitControls were integrated, enabling smooth camera navigation for users to pan, zoom, and rotate, providing an interactive way to explore the model's details from all angles.

The model includes the following interactive features:

1. **Camera Circular Motion with Button Toggle**  
   The camera moves in a circular motion around the lamp and always looks at it. This motion can be toggled on/off using a button.

2. **Zoom In/Out by Mouse Wheel**  
   Zoom the camera in and out using the mouse wheel, allowing the user to get a closer or farther view of the lamp.

3. **Drag to Rotate Around the Lamp**  
   The camera can be dragged to rotate around the lamp, allowing users to explore the model from different angles.

4. **WASD Keyboard Movement**  
   Use the WASD keys to move the camera forward, backward, left, or right in the 3D space.

5. **Button to Control Light On/Off**  
   A button allows users to toggle the light on and off. The button text updates to reflect the current light status.

6. **Hover Effect on Light Switch**  
   When the pointer hovers over the light switch, a visual cue is provided to indicate that the switch can be interacted with.

7. **Interact with Light Switch**  
   Clicking on the light switch toggles the light on or off and animates the pulling of the switch for a more interactive experience.

