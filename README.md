# GAME_PROGRAM-EX-5
## Making the Player Collect Ammo and Increase Bullet Spawn Count

## Aim
To implement a gameplay feature where the player collects ammo pickups placed in the game world. When the player collects ammo, the ammo count increases, allowing additional bullet spawns (shots).

## Procedure

### 1. Setup Player Character
- Open the PlayerCharacter Blueprint.
- Add a new Integer variable named **AmmoCount**.
- Set an initial default value (example: `AmmoCount = 10`).
- Ensure a shooting system exists that checks AmmoCount before firing.

### 2. Create Ammo Pickup Blueprint
- In the Content Browser: Right-click → Blueprint Class → Actor → Name it **BP_AmmoPickup**.
- Add the following components:
  - **Static Mesh**: Represents the ammo item (bullet, crate, etc.).
  - **Sphere Collision**: Used to detect player overlap.

#### Event Graph (BP_AmmoPickup)
- Use **OnComponentBeginOverlap** on the Sphere Collision.
- Cast the overlapping actor to **PlayerCharacter**.
- Increase the player's AmmoCount (example: `AmmoCount += 5`).
- Optionally play a pickup sound or visual effect.
- Destroy the BP_AmmoPickup actor.

### 3. Update Shooting Logic (Optional)
- Before spawning a bullet:
  - Check if `AmmoCount > 0`.
- If true:
  - Spawn the bullet.
  - Decrease AmmoCount by 1.

### 4. Place Ammo in the World
- Drag instances of **BP_AmmoPickup** into the level.
- Adjust their mesh, placement, and collision radius as needed.

## Output
<img width="1028" height="462" alt="image" src="https://github.com/user-attachments/assets/235c451e-7cd2-4028-be20-253e35bb984b" />


<img width="1033" height="654" alt="image" src="https://github.com/user-attachments/assets/6d0bfc69-3b10-4127-b27d-5bd39a01645d" />

<img width="1033" height="549" alt="image" src="https://github.com/user-attachments/assets/9885b733-480d-4185-80fc-7d8e7aaf8a59" />

<img width="1030" height="683" alt="image" src="https://github.com/user-attachments/assets/e144cb63-6a0e-4bc3-9666-aa67cb26ced8" />

## Result
- The player begins with a limited number of bullets.
- When the player overlaps with an ammo pickup:
  - The ammo is collected.
  - The player's AmmoCount increases.
- The player can now fire additional bullets depending on the updated ammo count.
