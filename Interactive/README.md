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
This video introduces what we completed in Part 1 Importing and Drawing, and Part 2 Materials, Light and Shading.

https://github.com/user-attachments/assets/b5521c81-b7d2-48d1-be73-4b7ca0fb692d

## Part 1 Importing and Drawing
Step 1: Splitting and Optimizing the Model To ensure the imported model was efficient and performed well, I imported the lamp into Blender and used the Decimate Modifier to reduce the number of vertices on each part. Now the total is only 9601 vertices. This step optimized the model and reduced the load on the browser during rendering, which is crucial for performance.

![image](https://github.com/user-attachments/assets/bdc24d95-c71b-456d-8495-d65a8282f469)

Step 2: Exporting the Model Once the model was optimized and split into four parts, I exported each part into separate .obj files. To maintain material properties and other essential parameters, I made sure to export all relevant details, including colors and UV mappings. The files I ended up with were: chains.obj, lamp_body.obj, switch.obj, and pendants.obj.

![image](https://github.com/user-attachments/assets/bbf72fcf-818f-4d96-975c-fe3e5dc4c00b)

Step 3: Importing the Model into Three.js With the files ready, I wrote a Three.js script to handle importing and setting up the model in the scene. The script starts by creating a basic Three.js scene with a plane and a camera to provide a view of the lamp. The plane acts as the ground, and the camera is positioned strategically to showcase the entire model.

![image](https://github.com/user-attachments/assets/37d2c109-068b-461e-8610-9af8c97bac1b)

Step 4: Assembling the Model To assemble the lamp, I added a BoxHelper around each part. This tool helped me visualize the boundaries of each object and ensured they were correctly aligned when placed in the scene. Adjustments to the position, scale, and rotation were made so that the parts fit together seamlessly, forming a single cohesive lamp.

![image](https://github.com/user-attachments/assets/af2a26b6-cb6f-49cf-9280-91198f378cd0)

## Part 2 Materials, Light and Shading.

![image](https://github.com/user-attachments/assets/3e1a0e6b-b770-4707-8eb4-9351424e4ffa)
![image](https://github.com/user-attachments/assets/1040c665-358f-4fe5-8c10-43a33baa8045)

Step 5: Setting Up Materials Now, while I exported materials correctly from Blender, I ran into an issue: Three.js doesn’t support some of the advanced material features. To solve this, I used MeshPhysicalMaterial, which is a versatile material type in Three.js, capable of simulating realistic properties like metalness and roughness. I created custom materials for the metal parts of the lamp and the diamond-like pendants. I also made sure to apply the correct colors, especially for the lamp cover, to replicate the design in the original model.

Step 6: Adding Lighting and Controls Lighting is vital for showcasing the model’s details, so I included a HemisphereLight for ambient illumination and a DirectionalLight for casting shadows and highlighting the model’s form. This setup allows the lamp to be seen in both lit and unlit conditions. To make navigation easier and more interactive, I incorporated OrbitControls, enabling us to pan, zoom, and rotate the camera to view the lamp from different angles.
