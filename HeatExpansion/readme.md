# heat expansion compensation stuff 

## General
Heat sources: 
- hotend
- bed heater
- friction
- motors

A lot of work has been done on compensation for errors in printing resolution due to heat expansion (check out [tanaes](https://github.com/tanaes) nice work on the topic). Kinematic coupling for beds and titan or steel backers for gantry extrusions beeing the probably most popular solutions. But they usually come with some general flaws.

### [Annex K3](https://github.com/Annex-Engineering/Gasherbrum-K3):
While the Bed is directly mounted to extrusions, the kinematic coupling covers the expansion (and tilt) of the bed extrusions. The gantry rails are mounted in plastic or directly on the gantry extrusions. The design is inherently flawed concerning heat expansion of  rails, frame (except bed extrusions) and bed.

### Voron [Trident](https://github.com/VoronDesign/Voron-Trident) / [Salad Fork](https://github.com/PrintersForAnts/Salad_Fork) / [2.4](https://github.com/VoronDesign/Voron-2) / [Micron](https://github.com/PrintersForAnts/Micron)
Titan and Steelbackers exist for the gantry extrusions. Kinematic mounting for the Bed. The bed extrusions are mounted to the Z Rails using spherical bearings. Stock builds don´t have any solution for heat expansion errors. The designs are inherently flawed concerning expansion of the rails, frame, and bed. Also, the Z-Axis on these printers only work because of plastic beeing wobbly, due to massive overconstrain.

### Backers as a solution:
Backers follow a simple idea. If heat expansion creates a force in one direction that results in bending, we just need to create another force pulling in the opposite direction to compensate. But it neglects a lot of things: Thermal expansion is still happening and will induce stress into the system at various points. And they have a few obvious downsides since they are not 3D printable, take up space that could be utilized, expensive and add weight. It would be easier to not have this force in the first place, making compensating it unnecessary.

### Kinematic coupling for Beds:
Direct mounted Beds like on the [CroXY](https://github.com/CroXY3D/CroXY) are a simple and nice solution. But having extrusions to which the bed is mounted allows simple implementation of overtravel and cheaper beds. This benefit is kind of destroyed with the currently available kinematic couplings for beds, since they are usually CNC milled or cut from steel or titanium. Since this also adds unnecessary weight for moving Z machines and makes extrusion-mountable, 3D printed kinematic coupling for beds a necessity. 

### What about the Z-Rails?
Z Rails expand too. The solution with backers is just really inconvenient if panels are directly mounted from the opposite site. So usually no solution is applied.

## Mounting Linear Rails to Aluminium Extrusions:
The different heat expansion coefficient of the materials from the linear rails and extrusions results in a different elongation. Since they are static coupled, one of them can´t expand as much as necessary. This induces stress and, depending on the friction between the materials and material properties, leads to a bow. If we do not want this stress in our system, we need to allow the different elongation while preserving accuracy. The obvious solution for a 3D Printer is mounting the rail different.

Only one steel TNut is needed per rail. This one is mounted in the middle, the screw is fully tightend. This screw ideally locks all necessary degrees of freedom. Since it is not ideal, we support it a little. For all other holes in the rail, use a 3D printed TNut (preferably material with low friction coefficients). This nut should not apply ANY force in mounting direction of the rail, so just tighten them extremly gently with a little bit of loctide or something. Ideally, the printed nut fills the slot of the extrusion and is touching both, extrusion and rail. You can use a little bit of friction reducing material (grease, oil) between extrusion and nut. Also between Extrusion and Rail. Make sure the chosen material is compliant with the other components used. Now, heat expansion of the extrusion and the rail is decoupled. They can both elongate at their pace, since the printed TNuts can slide in the extrusion.

Note: The shape of your extrusions becomes a critical part for this kind of mount. Using quality extrusions is a necessity, else your rails might wobble in undesired directions.

Without the steel TNut tightend the rail should not wobble on the extrusion, but only move in the direction of the slot. You might have to tune your printer/slicer first.

## Bed
For the bed, we can use the exact same method. Instead of screwing it directly to the extrusions, we screw it on a plastic carriage that slides in the extrusion. This carriage needs low friction and high accuracy. On a V2.4 this still leaves the bed overconstrained. On a Trident style printer, this will result in a bed that is not expanding similar in all directions. Due to the T-like mounted bed extrusions, the fixed point of the bed moves to the front. This is probably irrelevant for small, 3-Axis machines, but might be an issue otherwise. Mounting the Bed extrusions Y-like solves this.

## Frame
With all rails decoupled from the frame, the frame can expand in all directions. Make sure that if your panels are directly bolted to the frame, the screws should not be tight and the mount holes in the panel should be a little oversized to allow elongation of the frame. Consider using only one steel TNut and TNuts printed in a material with low friction coefficients.


## This Repository
The STL Uploaded is for 15x15 extrusions according to the SF 150mm CAD. The f3d file can be used as an example how the Nut needs to be shaped to adapt for other extrusions. The STL should be printed with a 0.2 Nozzle, else issues might occure.

## Why no Data?
I enjoy using my brain and I don´t have enough time to test evertyhing by myself. Data is highly appreciated. This repository does not intend to deliver a final answer or solution, but wants to introduce a possibly better approach for the problem at hand.
