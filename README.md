# Unity-MSDF-Fonts
### Basic tool to convert Unity fonts to use Multichannel Signed Distance Field fonts

Multichannel SDF font rendering provides much sharper text rendering that maintains its sharpness without pixelization no matter how large the text is. 

This just takes Unity fonts and converts them to MSDF fonts using [MSDFGen](https://github.com/Chlumsky/msdfgen). At the moment this is a hack with a few hours of work and will probably be extended into a more useful thing in the future if people care enough. 

This tool is made for static fonts that are baked out in the editor. It was mostly made targeted at VRChat worlds because Text Mesh Pro is fairly broken in VRChat. The main advantage that multi channel SDFs have is that they can maintain corners. Normal SDFs will usually get rounded corners on text. The MSDFGen github has a good example comparting to regular SDFs https://github.com/Chlumsky/msdfgen.

#### Default Unity Text Rendering
<img src="https://i.imgur.com/stcsq5M.png" width="80%" height="80%" />

#### MSDF Text Rendering
<img src="https://i.imgur.com/SgnKuqv.png" width="80%" height="80%" />

### Usage
1. Install the package from the releases page 
2. Find a font that you like and use it on UI Text or Text Meshes
3. Select the font asset and change the font size to somewhere between 30 and 60 and change the Character from Default to ASCII Default Set and click the Apply button. **This step is important, if you do not change the character, the atlas generator will not know what to generate!** If you need to support non-latin languages, you will need to change the Character to UTF and use a font that supports the extra characters. At some point I might make the script look at what characters are used in the scene to find the necessary characters. 
4. Open the atlas generator under the Window drop down Merlin > MSDF Font Generator
5. Drag the font asset into the Font Asset slot in the generator and click *Generate Atlas*
6. Once the atlas generation has finished, the new font atlas will be selected in your project files. 
7. Make a new material for your text. If you are putting this on a Text Mesh, select the `Merlin/MSDF Text Mesh Font` shader. If it is UIText use the `Merlin/UI/MSDF UI Font` shader.
8. Drag the generated atlas texture into the MSDF Texture slot on the material.
9. Apply the new material to your UI Text or Text Meshes.
10. You should now have MSDF text on your text now. If you see artifacts that look like melting, go back to step 3 and increase the font size until the artifacts go away.
