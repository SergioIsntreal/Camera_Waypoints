# Camera Waypoints

### In this tutorial, we will be creating Waypoints that the Camera/Player will follow automatically

> [!IMPORTANT]
> You will need any version of Unity and VisualStudio released within the last 5 years
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
  
1. Right Click in the `Assets` window, -> `Create` -> `C# Script` and name the script 'FollowWP'. Double click to open in VisualStudio.

2. Within the `public class` (press enter on **Line 6**), we are going to create an array to store the waypoints in. Type `public GameObject[] waypoints;`

3. Next we need to track the current waypoint, so hit `Enter` and type `int currentWP = 0;`
> [!NOTE]
> For clarity, the array index always starts at 0.

4. Hit enter and type in `public float speed = 120.0f;`. Because it's a public variable, you can edit it later in unity if the speed is too fast or slow.

5. Hit enter again and type in `public float turnSpeed = 10.0f;`. This variable is responsible for the rotation speed as the player turns from waypoint to waypoint.

![image](https://github.com/user-attachments/assets/fa1b2194-f3a2-4d93-b5cb-8e0c926581cf)

6. Within the curly brackets of `void Update()`, we're going to write a script that detects when the player has reached the Current Waypoint. Once reached, the current waypoint will increase by 1, in which the player will move onto the next one.

  `if(Vector3.Distance(this.transform.position, waypoints[currentWP].transform.position) < 3)
       currentWP++;`

7. Hit `Enter` twice and type in the following:

   `this.transform.Translate(0, 0, speed * Time.deltaTime);`

   This is what allows the player to move.

8. Now all we need is for the player to look at the waypoint they're travelling to. To do this, we need to create a `Quaternion` (responsible for smoother rotations)
   Hit `Enter` and type in:

   `Quaternion lookatWP = Quaternion.LookRotation(waypoints[currentWP].transform.position - this.transform.position);`

   `this.transform.rotation = Quaternion.Slerp(this.transform.rotation, lookatWP, turnSpeed * Time.deltaTime);`
   > (I'm not even gonna pretend I know what this all does. I just know it works.)

   Altogether, it should look something like this:

   ![image](https://github.com/user-attachments/assets/3fb2a9e9-da95-44d7-8f0d-0ecac6537710)

   Save the script and return to Unity.

### How to attach the script to the Camera

1. Drag and drop your `FollowWP` script onto the `Main Camera`. Scrolling down the `Inspector` will show the script's array.

<img width="458" alt="image" src="https://github.com/user-attachments/assets/4fff6390-6102-49ad-8ba0-fcc813a1fc6b" />

2. Enable the lock in the top right, shift select all your waypoints and drag them into the empty list.

<img width="467" alt="image" src="https://github.com/user-attachments/assets/d9a59598-cbcc-4a49-ad54-dbf78f3dce11" />

> [!NOTE]
> Ensure that the order in which they appear is correct. Also, remember to unlock your Inspector.


### And you're all set! The camera will follow the waypoints up until the last one.
