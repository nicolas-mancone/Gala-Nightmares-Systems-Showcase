# 🎭 Gala nightmare - Gameplay Systems (Global Game Jam 2026)

> **Theme:** "Mask"
> **Context:** Developed in 48 hours at Roma Game Dev.
> **Original Team Repo:** [GGJ2026 - Gala nightmare](https://github.com/Patagatto/GGJ2026)

**Gala nightmare** is a local multiplayer HD-2D beat 'em up made in **Unreal Engine 5.7**.
This repository highlights the specific systems I worked on: the **Shared Camera** and the **Character Logic**.

---

## 📸 Demo

| Shared Camera Logic | HD-2D Combat |
| :---: | :---: |
| ![Camera Demo](https://github.com/user-attachments/assets/3445a26b-d1d8-4be0-8ed9-59c202d9a00e) | ![Combat Demo](https://github.com/user-attachments/assets/89046276-4d3b-417d-9792-cf34f5f810e7) |
| *Keeps both players on screen* | *2D Sprites in 3D environment* |

---

## 📹 1. Shared Camera System
I created a custom Camera Actor designed to handle local multiplayer.

* **Dynamic Tracking:** The camera calculates the center point between all players to keep the action focused.
* **Auto-Zoom:** It zooms in and out based on how far apart the players are.
* **Screen Bounds:** I implemented logic to stop players from walking off-screen. If a player tries to leave the camera view, the system clamps their position so they don't get lost.

---

## 🤺 2. HD-2D Character (`AGGJCharacter`)
I used **Paper2D** and **PaperZD** to handle the 2D sprites within the 3D world.

* **Perspective Fix:** Since the camera is angled at -40°, the 2D sprites looked flattened. I applied a procedural scale adjustment to make them look correct from the player's perspective.
* **Movement Physics:**
    * **Roll/Dodge:** Instead of just playing an animation, I modified the friction and deceleration values during the roll to make it slide smoothly.
    * **Lunge:** When attacking, the character automatically moves slightly towards the enemy to make hitting them feel more satisfying (Magnetism).

---

## ⚔️ 3. Combat & Mask Mechanics
* **Precise Hitboxes (AnimNotifies):**
    * I used **AnimNotifies** to sync collisions with the sprite animation.
    * **Repositioning:** When an attack frame plays, a Notify moves the hitbox to the exact location of the weapon/fist.
    * **Timing:** Another Notify activates the collision only during the "active frames" and disables it immediately after, ensuring precise hits.
* **Mask System:** The core mechanic of the jam.
    * **Time Limit:** Masks drain over time.
    * **Reward:** Hitting enemies adds time back to the mask.
    * **Buffs:** Different masks give different bonuses (Lifesteal, Speed, Armor).

---

## 🛠️ Tools Used
* **Engine:** Unreal Engine 5.7
* **Plugins:** Paper2D, PaperZD
* **Language:** C++ & Blueprints

> *Note: This project serves as a technical proof-of-concept for mixing 2D sprites with 3D physics and camera logic in Unreal Engine 5.*
