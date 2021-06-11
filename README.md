**ShaderPrecompiler**

A small utility to precompile shader in order to avoid game stuttering when objects first come
into sight, and their shaders get lazily compiled.

Just add the ShaderPrecompiler-Node in the viewframe of your active game camera. The script will
recursively walk the scene tree and add a quad-mesh for each found material on a MeshInstance with
a copy of that material, thus forcing compilation of the shader.

Then, for a few frames (5 by default), all these are rotated randomly and illuminated by an omni- and a spotlight.
After that, the node frees itself and all its created mesh children. Also, a signal is emitted that 
can be used to notify other nodes that the shaders are now compiled. 

To hide the generated objects for the time of these frames, place the Node behind a wall, or below a floor.
It just needs to be within the camera frustum but not actually visible.
Alternatively: Implement a loading screen or something that then gets hidden (e.g., using the built-in signal)


For objects that need to be pre-compiled but are not (yet) in the scene-tree, just add them to the Node itself,
as shown on the screenshot.
![Screenshot](images/manualObject.png?raw=true "Manually added object")


Enjoy!