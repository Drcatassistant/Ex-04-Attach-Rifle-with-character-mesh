# Ex-04-Attach Rifle with character mesh and implementation bullet spawn from Rifle 
# Experiment: Attaching Rifle to Character Mesh and Implementing Bullet Spawn from Rifle

## Aim
To attach a rifle to a character's skeletal mesh and implement the functionality for bullets to spawn from the rifle's muzzle when fired.

## Procedure

1. **Setup the Rifle Mesh:**
   - Import the rifle mesh into the game engine (e.g., Unreal Engine).
   - Create a socket on the character's skeleton (typically on the "hand_r" or similar bone) using the Skeleton Editor.
   - Name the socket appropriately (e.g., `RifleSocket`).

2. **Attach Rifle to Character:**
   - In the character blueprint or code, attach the rifle to the socket using:
     ```cpp
     RifleMesh->AttachToComponent(GetMesh(), FAttachmentTransformRules::SnapToTargetIncludingScale, "RifleSocket");
     ```

3. **Define Muzzle Location:**
   - Add a scene component (e.g., `MuzzleLocation`) as a child of the rifle mesh at the desired position of the muzzle.
   - This will serve as the bullet spawn point.

4. **Implement Bullet Spawning:**
   - Create a bullet actor class with a projectile component.
   - In the character’s shooting function, spawn the bullet at `MuzzleLocation` with appropriate rotation:
     ```cpp
     FVector MuzzlePos = MuzzleLocation->GetComponentLocation();
     FRotator MuzzleRot = MuzzleLocation->GetComponentRotation();
     GetWorld()->SpawnActor<ABullet>(BulletClass, MuzzlePos, MuzzleRot);
     ```

5. **Add Input Binding (Optional):**
   - Bind a key or mouse input to trigger the firing function in the character class.
     
## Output

![image](https://github.com/user-attachments/assets/71fdf9c4-ae45-49d1-a741-d88dd018e241)

![WhatsApp Image 2025-05-15 at 13 53 28_d2c083ab](https://github.com/user-attachments/assets/7e12f9f6-3842-4827-8ffe-a1d94a6371df)


## Result

- The rifle was successfully attached to the character mesh using a custom socket.
- Bullets spawned correctly from the muzzle of the rifle when the firing input was triggered.
- The implementation resulted in a functional shooting mechanism where bullets originated from the correct position and direction.
