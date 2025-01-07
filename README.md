# Camera_Waypoints
In this tutorial, we will:
- Create and Configure the Map and Player
- Apply the camera to the Player
- Create waypoints for the camera to travel between
- Tweak the camera's movement to better suit a railshooter

> [!NOTE]
> This tutorial is made for a 3D Unity Project

## Setting up: Map
To start off, you'll need to create a plane for the player to travel across.

1. Click the `GameObject` tab in the top left menu -> `3D Object` -> `Cube`

  ![image](https://github.com/user-attachments/assets/9b15712e-bf90-4d64-8c19-df1989a58422)

2. Click the Cube in `Heirarchy` and rename it to 'Floor' (or whatever will help you distinguish it from the player)
   
3. In the `Inspector` tab on your right, under the `Transform` tab, change the values of X and Z next to `Scale` to however long and wide you want your map.
   
 <img width="955" alt="image" src="https://github.com/user-attachments/assets/20cafe5e-00fa-4bad-83b6-a95c1e251afd" />
 
> [!NOTE]
> Ensure that you have the right object selected in your Heirarchy before changing the Transform values

4. Change the Z value next to `Position` to move the cube so it has the `Main Camera` positioned on the far right of your map

5. Scroll down in the Inspector until you see the `Add Component` button. Click it and type `RigidBody` into the search bar. This will add collision to the object.

![image](https://github.com/user-attachments/assets/f61a4732-9baa-49f7-af10-dcd17005c870)

6. Within the Rigidbody tab, change the value of `Mass` to 1000. This will prevent other objects from being too heavy and flipping the map (in theory at least).

## Setting up: Player
Now that you have a map, let's create the Player.

1. Click `GameObject` -> `3D Object` -> `Capsule` (You could use any shape really, but I'd recommend Capsule or Cylinder since they have height)

2. Similar to before, rename the Capsule/Cylinder to 'Player'

3. Scale up to your desired size and position above the extruded cube where you want the player to start.

<img width="950" alt="image" src="https://github.com/user-attachments/assets/58e8504c-7fe8-4c52-b8bc-c9e084ef5efa" />
(Click the highlighted icon before changing the Scale values if you want them to be scaled up together)

4. Add a `RigidBody` to the Player. Unlike the previous object, this time you want `Use Gravity` to be ticked.

![image](https://github.com/user-attachments/assets/1ee90561-8703-4278-8dce-14e805cb69c8)

## Setting up: Map
To start off, you'll need to create a plane for the player to travel across.






