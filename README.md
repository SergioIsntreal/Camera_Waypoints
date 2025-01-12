# Camera Waypoints

### In this tutorial, we will be creating Waypoints that the Camera/Player will follow automatically

> [!IMPORTANT]
> In this tutorial, you will need any version of Unity and VisualStudio released within the last 5 years
> 
> This tutorial is made for a 3D Project
> 
> For this tutorial, you'll need a premade map for your player to travel across.

## Quick way to make a map

Right click in `Heirarchy` -> `3D Object` -> `Terrain`. In the `Inspector`, you can modify and expand the map to your liking.

![image](https://github.com/user-attachments/assets/3f1390da-111b-4f28-a2fb-2c1d95bf3209)

> This is optional, but I added some extruded cubes (`Heirarchy` -> `3D Object` -> `Cube`) on the map so that you can see more of a visual change when the player moves.

<img width="668" alt="image" src="https://github.com/user-attachments/assets/af1ded51-7d86-4580-b49d-51058a72771d" />

> To keep the Heirarchy tidy, I recommend creating an empty gameObject ( `GameObject` -> `Create Empty`), renaming it to 'Map' or something similar, and dragging your terrain and cubes into it to parent.

> [!IMPORTANT]
> It is recommended that before you start, your `Main Camera` is placed on the map roughly where you want the player to start. Keep in mind that the Y position of the Camera should be at the player's eye level.


### To start, let's create the Waypoints

1. Under `Heirarchy`, right click -> `GameObject` -> `Sphere`, and rename it to 'Waypoint'. This will be the first position your player travels to, so place it accordingly. **Make sure it has the same position on the Y Transform as the Main Camera.**

2. To create more, duplicate the waypoint by pressing Ctrl + D. It's important that you place them in the order of which you want the player to travel. Once you have all your Waypoints, shift select them all and right click, `Create Empty Parent`. Rename to 'Path' (Press F2 to rename a gameObject in the Heirarchy).

![image](https://github.com/user-attachments/assets/fb7c124b-88ed-4f1c-a9cf-ecb3a6abb67e)

> Here I scaled them up so they'd be visible from afar, but they shouldn't be visible when you run the game. Make sure `Mesh Renderer` is unticked.


### Now to write the script for the Camera to follow the Waypoints
  
1. Right Click in the `Project` window, -> `Create` -> `C# Script` and name the script 'FollowWP'. Double click to open in VisualStudio.




