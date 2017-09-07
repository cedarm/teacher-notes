## Setup
 - enable pie menus
 - remove default objects
 - cycles
 - experimental (adaptive subdiv)
 - frame size
 - sampling
   - samples, squared, 32/12 (render/preview)
   - clamp indirect 5.0, or try new denoising
 - filmic

## Modelling

### box
 - 1 unit cube
 - origin bottom center
 - r z -52
 - g x 0.65
 - g y 0.15
 - g z 0.005 (explain)

### cylinder
 - 1 unit diamater
 - origin bottom center
 - 1.65 tall
 - g x -0.23
 - g y 1.46
 - g z 0.005 (explain again)

### sphere
 - 1 unit diamater
 - origin bottom center
 - g x -0.83
 - g y -0.10
 - g z 0.005

### table
 - name the object
 - origin _top_ center
 - dims <4, 4, 3>
 - g y 0.15

## Materials

 - cycles

### painted wood material
 - Mix Shader (diffuse/glossy mix)
 - Diffuse BSDF, 0.76 white (top)
 - Glossy BSDF, 1.00 white (bottom)
 - fresnel mix factor
 - roughness 0.4

### table material
 - standard fresnel mix
 - diffuse 0.33 white
 - roughness 0.2

### principled shader

## Modifiers

### cube bevel
 - 3 segments
 - bevel width 0.005

### cylinder
 - see solid view
 - set smooth shading
 - add bevel
   - see wireframe view
   - bevel width 0.02
   - 3 segments
   - see problem in solid view
   - limit angle 30 degrees
   - see solution in wireframe and solid view
   - bevel width 0.005
 - add subsurf
   - see wireframe view, be careful
   - catmull-clark
   - 2 levels
   - adaptive (dicing rate 1.0)

### sphere
 - set smooth shading
 - add subsurf
   - see wireframe view, be careful
   - catmull-clark
   - 2 levels
   - adaptive (dicing rate 1.0)

## Camera

 - add camera
 - 36mm sensor
 - 105mm lens
 - clear loc/rot (Alt-G, Alt-R)
 - r x 77
 - g z 1
 - g zz 8.8 (local Z)
 - DOF

## Lighting

### main light
 - mesh
   - plane, name it KeyLight
   - dims <0.4, 0.4, 0>
   - g -15 <tab> -7.5 <tab> 7
   - rotate about individual origins
   - r y 114
   - r z 44
 - material, name it KeyLight
   - emission shader, 1.0 white
   - strength 8000

### bounce board
 - mesh
   - plane (origin at center)
   - dims <7, 5, 0>
   - r y 75
   - g z 2.4
   - g x 1.8
   - g y 0.25
 - material
   - standard fresnel mix
   - diffuse 0.90 white
   - roughness 0.2

### backdrop
 - duplicate bounce board, Shift-D ESC (not Alt-D)
 - same material
 - dims <11, 8, 0>
 - clear loc/rot (Alt-G, Alt-R)
 - r x 90
 - g y 21
 - g z -2

### turn down ambient light
 - world, surface, background color, 0.00 black

### shade
 - view wireframe
 - mesh
   - duplicate KeyLight, Shift-D g zz 0.5
   - dims <1.0, 1.0, 0>
   - name object Shade
   - new material, name it Shade
     - diffuse 0.01 black
     - roughness 0.1
   - g yy 0.55 (somewhere between 0.50 - 0.80)

### other light
 - emission shader, 1.0 white
 - strength 100
