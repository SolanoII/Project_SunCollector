# Project Trazyn

## Download

- **Current preview - Demo 1.6 (November 2026):** [Project_Trazyn-demo_1_6.zip](Project_Trazyn-demo_1_6.zip)
- Old version - Demo 1.5 (November 2026): [OldVersions/Project_Trazyn-demo_1_5.zip](OldVersions/Project_Trazyn-demo_1_5.zip)
- Old version - Demo 1.4 (November 2026): [OldVersions/Project_Trazyn-demo_1_4.zip](OldVersions/Project_Trazyn-demo_1_4.zip)
- Old version - Demo 1.3 (November 2026): [OldVersions/Project_Trazyn-demo_1_3.zip](OldVersions/Project_Trazyn-demo_1_3.zip)
- Old version - Demo 1.2 (November 2026): [OldVersions/Project_Trazyn-demo_1_2.zip](OldVersions/Project_Trazyn-demo_1_2.zip)
- Old version - Demo 1.1 (November 2026): [OldVersions/Project_Trazyn-demo_1_1.zip](OldVersions/Project_Trazyn-demo_1_1.zip)
- Old version - Demo 1.0 (September 2026): [OldVersions/Project_Trazyn-demo_1_0.zip](OldVersions/Project_Trazyn-demo_1_0.zip)

How to play: extract the zip anywhere and run `ProjectTrazyn.exe` from the extracted folder (keep it next to the `GameData` folder).
Requirements: Windows 10/11, a GPU with OpenGL 4.3. If Windows complains about a missing `VCRUNTIME140.dll` / `MSVCP140.dll`,
install the Microsoft Visual C++ Redistributable 2015-2022 (x64). If SmartScreen shows "Windows protected your PC", click "More info" -> "Run anyway".
Your profile is saved in `%APPDATA%\ProjectTrazyn`.
On first launch the game picks a graphics quality (Low, Medium, High or Max) for your graphics card; you can change it in
Options -> GRAPHICS. Press F3 in game to see FPS and where the frame time goes.

## What's new in Demo 1.6

- **Squads and lobbies (peer to peer)**: create a squad in the garage (SQUADRA button) and share its 6-digit code (COPY / PASTE buttons).
  Your squadmates stand next to your unit in the garage with their name above their head, and the camera widens to frame everyone.
  - *Open* lobbies are listed and anyone can join; *closed* lobbies are listed but the leader accepts or refuses each request
    (the code still lets you straight in); *private* lobbies are hidden and only the code works.
  - Ready / not ready, kick, ping of every squadmate.
- **Best connection hosts the game**: every player measures latency and packet loss towards everyone else. Whoever opens the lobby
  is the host; if someone with a clearly better connection for everyone joins, the host role moves to them on its own, without
  interrupting. If the host leaves or crashes, the next best player takes over within a few seconds and continues from the last state.
- **New SERVER screen**: list of open lobbies (local network and matchmaking server) with host, players, status (in lobby / in game)
  and ping; you can also join a game that has already started. On the right: open your own lobby, make it visible or private, copy its code,
  set the matchmaking server address.
- **Play online without opening ports**: the new matchmaking server (`TrazynServer.exe`, a separate small program) keeps the lobby list
  and the 6-digit codes, introduces players to each other so their routers open up to each other, and relays the messages when two
  routers just won't connect. Only the person running it opens one port (UDP 27640); the game itself stays peer to peer.
- **Fixes**:
  - everything a match leaves behind is now reset when you leave a match or start a new one (shots still in flight, tracers, corpses,
    cloak, half-finished vaults, melee or reload in progress, scope);
  - you could get stuck inside a wall after vaulting: the landing spot is now checked (other distances are tried, or no vault), and a
    body that ends up inside a wall is pushed out on the nearest side.
- The co-op/versus match itself is not synchronized yet: the START (TEST) button tests the connection and the host hand-over.

**How to play online**
- *Same house / same network*: the 6-digit code works out of the box.
- *Hamachi (or ZeroTier, Radmin VPN)*: the host opens an **open** lobby; the others type the host's Hamachi address followed by
  `:27650` (for example `25.61.120.33:27650`) in the code field and press ENTER. Allow the game on public networks in the Windows firewall.
- *Matchmaking server*: one person runs `TrazynServer.exe` with UDP port 27640 forwarded on their router; everyone writes
  `that-address:27640` in the SERVER screen and presses CONNECT. Then codes and the lobby list work over the internet.

## What's new in Demo 1.5

- **Shooting that hits hard**:
  - every weapon type has its own layered sound (lasgun, hot-shot, long-las, autogun, shotgun, sniper, bolter, plasma, melta, flamer,
    launcher, grav) instead of one shared sample, with random variations so no two shots sound the same;
  - distant gunfire: far shots arrive late like real sound and only the echoing boom carries across the map;
  - bullets that miss you by a hair whizz past your head; explosions finally have a sound, near and far;
  - impacts sound different on flesh, armour, walls, earth and energy; a tick confirms every hit and a heavier note confirms the kill;
  - muzzle flashes and explosions light up the scene, brass casings fly out and bounce, bullet holes and scorch marks stay on walls
    and ground (laser, plasma and melta marks glow while they cool down);
  - camera shake and FOV punch on firing, explosions and incoming hits; enemies flinch where they are hit;
  - melee hits "land": a split-second hit-stop, then the shake.
- **Every body has its own weight**: a Gretchin trembles at everything, its own gun yanks it around and its steps are tiny;
  a Space Marine is a rock under fire, its guns sound deeper, its armoured boots are heard from afar and the ground shakes for
  small creatures walking next to it. Orks and Ogryns sit in between.
- **New options** in AUDIO: camera shake strength (0-150%) and hit-stop on/off.
- **Bug fixes**:
  - particles and tracers were visible through walls;
  - damage arrived before the projectile you see (bolts and plasma killed while still in flight) and melee hit before the swing
    reached the target: now damage lands when the shot or the blade gets there;
  - dead units turned back into blocks: now the animated body stays and falls with the ragdoll, and the ragdoll starts facing the
    same way as the unit;
  - footsteps on dirt, metal and wood were silent.
- **New interface**: a single grimdark style for every screen, half gothic (pointed arches, burnished brass, Roman numerals) and half
  futuristic (chamfered panels, instrument grids), with new fonts. The research tree has been redesigned (unit cards with tier,
  state and progress towards the next research, glowing branches, drag to pan with the right mouse button), together with the top bar,
  the shop, the pause menu and the health, stamina and ammo HUD.
- **Faster rendering**: all map blocks are drawn in a single call (also in the shadow pass) and character bones are uploaded once
  per character instead of once per clothing piece.

## What's new in Demo 1.4

- **Grimdark rendering overhaul**:
  - real-time shadows for every animated character, body, clothing and armour included; fixed the sun shadows, which never worked;
  - skin with subsurface scattering: soft reddish light-to-shadow transition, light shining through ears and fingers;
  - ambient occlusion: darker corners, folds and contact points;
  - a sky with moving clouds, height fog with drifting dust, grimdark colour grading (cold shadows, warm lights, muted colours,
    vignette and film grain);
  - FXAA anti-aliasing.
- **Battlefield materials**: maps are no longer flat-coloured blocks. Mud with puddles and craters, cracked rockcrete, rusty riveted metal,
  sandbags, burnt wood, trench earthworks, dead trees and rubble, plus scattered debris across the field.
- **Worn gear**: clothing and armour are muted and dirty. Mud climbs from the boots, dust settles on the shoulders, dried blood stains the cloth,
  rust and scorch marks cover the armour. No bright colours: everything looks like a universe heading towards its end.
- **Options menu**:
  - working volume sliders (master, effects, voices, music);
  - a dark ambient soundtrack (organ drone, distant choir, cathedral bell, wind and far artillery) that ducks under the fighting;
  - a new GRAPHICS tab that controls every effect: shadows, ambient occlusion, bloom, brightness, skin, grime, map materials,
    debris, sky, fog and colour grading.
- **Performance for weaker PCs**:
  - four quality levels (Low, Medium, High, Max), chosen automatically on first launch for your graphics card or integrated GPU;
  - render resolution scaling, half-resolution ambient occlusion, shadow resolution setting and a VSync toggle;
  - off-screen culling: objects and characters you can't see are no longer drawn;
  - F3 performance overlay with FPS and CPU/GPU timings.
- **Ready for real art**: the engine now loads characters made by artists (FBX or glTF) with full PBR textures (colour, normal maps,
  roughness/metal/occlusion, emissive). It recognises Mixamo and Unreal skeletons and adapts the game animations to rigs exported
  from Blender or Maya.
- **Log file**: `sunengine_log.txt` next to the exe, useful when reporting a problem.

## What's new in Demo 1.3

- **Marksmanship instead of random spread**: shots go where you aim; low Ballistic Skill means more recoil, grazing hits and an upward
  spray arc, high skill means pin-point shots. A careful first shot from a crouch is accurate, and lining up a perfect shot takes longer
  for poor marksmen.
- **Combat effects per weapon type**: lasguns, autoguns, bolters, plasma, melta and flamers each have their own projectile, muzzle flash
  and impact; melee attacks leave slash trails.
- **Readable rock-paper-scissors melee**: visible wind-ups and recovery delays between attacks, so you can read and counter
  Normal, Fast and Heavy attacks.
- **Better bodies and clothing**: Ork, Aspirant and Astartes bodies rebuilt from the base human anatomy, procedural skin, cloth and
  armour detail, new clothing textures, Mk VII power armour on the animated body.
- **Every race moves differently**: Orks swagger hunched with wide arms, Gretchin scurry crouched and look around nervously,
  Space Marines walk heavy and upright, Ogryns lumber and sway. Extra bones: Gretchin ears and jaw, Ork jaw (roars on WAAAGH! and charges),
  Ogryn jaw and belly, Astartes pauldrons.
- **Muscle tone and race skin**: sharper muscle definition, veins on Orks, Space Marines and Ogryns, mottled warty skin for Orks and Gretchin.
- **Squig model**: the Gretchin's squig is now a proper creature (huge toothy maw, eyes, spines, clawed feet) that hops, bites and ragdolls.
- **Showcase**: new SHOWCASE tab with all races side by side and every animation; the research tree has a 3D PREVIEW button for each unit.
- **New customization screen**: full-screen editor with a live 3D preview of your unit (drag to rotate, wheel to zoom, idle/aim/walk/run),
  skin tone presets, equipment and armour changes shown instantly, Save or Undo.

## What's new in Demo 1.2

- **New research trees** for every faction, with branches that split and rejoin:
  - *Imperial Guard*: Conscripts → Whiteshields → Guardsman / Schola Progenium Cadet, then Special Weapon Team, Ogryn and Kasrkin,
    command (Captain → Colonel → Lord General), Tempestus (Scions → Specialist → Tempestor → Tempestor Prime) and the Commissariat.
  - *Orks*: Slugga and Shoota branches (Stormboyz, 'Ard Boyz, Kommandos **or** Tankbustas, Flash Gitz) meeting at the Nobz → Meganobz → Warboss,
    and the Loota branch up to the Big Mek Boss in Mega Armour.
  - *Space Marines*: Aspirant → Scout Squad → Firstborn, then Tactical, Assault, Heavy Support and Reconnaissance branches up to the Captains.
  - **Mastery**: to unlock the next unit you must first research all the gear of the current one (gold star). Some units need two masteries.
- **Unit kits**: every playable unit now has its own base loadout and unlockable gear (weapons, armour pieces, equipment) to research and buy:
  Conscript, Whiteshield (deployable lascannon), Guardsman (flamer, plasma, melta, long-las, grenade launcher, vox caster that calls in a Conscript),
  Schola Progenium Cadet (carapace armour, hot-shot weapons, ammo crate), all five Ork units, Aspirant, Scout (auspex radar, camo cloak, sniper,
  heavy bolter) and Firstborn (Mk VII power armour, power pack boost, krak grenade, Imperial insignia aura).
- **Faction mechanics on the V key**: Orks unleash the **WAAAGH!** when the bar is full (it drains if you stop fighting);
  the Imperial Guard gets **Follow Orders**, charged by staying close to your squad, with a radial menu of four 10-second orders
  (Take AIM!, Take Cover, MOVE MOVE MOVE!, Fix Bayonets!). Turning your back on the enemy drains it.
- **Bolt weapons** fire huge rocket-propelled shells with a smoke trail and an explosive impact; normal guns fire thin tracers.
- **Camo cloak**: the body turns into a transparent, liquid-like refraction of the background; AI enemies can't see you beyond 6 m.
- **Squads**: unlimited units within the point cap, with a maximum per unit type; every unit is a respawn. Crouch with CTRL,
  Gretchin can slowly climb tall walls, procedural animations for melee, grenades, items and building.

## What's new in Demo 1.1

- **VS BOT mode (5 vs 5)**: your squad (up to 5 units, empty slots filled by AI allies) against 5 bots on a new symmetrical map,
  "Trenches of Solemnace": hidden and protected spawns, trenches, bunkers, trees and ruins. Win by wiping out the enemy squad,
  or by having more points on the field when the 10 minutes run out. If you die, you take control of a living ally.
- **Point-based queues** like the tiers in WoT: up to 20 points, 21-100 and 101-300. The menu tells you if your squad is eligible;
  allies and enemies are randomized close to the cap but never above it.
- **Bot AI by role**: marksmen keep their distance, shoot easy targets and reposition to cover when threatened; versatile units
  decide from what they see whether they can win a melee; melee units charge no matter what.
- **Garage, research and shop**: local profile with Energy and study points, research tree for Imperial Guard, Space Marines and Orks,
  new profiles start with the root unit of each branch (Conscript, Neophyte, Gretchin).
- **New units and bodies**: Conscripts, Whiteshields, Ogryn, Scouts, Phobos, Gravis, Gretchin, Yoof, Shoota and Loota Boyz;
  animated 3D bodies for humans, orks, ogryns, neophytes, astartes and gretchin (F2 switches between the animated model and the hitbox blocks).
- **Combat**: per-block hitboxes (head, torso, arms, legs), hit feedback, melee that hits the real hitboxes, parry ring under your feet,
  shields / "perfect deflect" can parry ranged shots, shots now converge on the crosshair.
- **Testing Lobby**: a shooting range with a training dummy for every skeleton, showing damage and hit location.
- **Rebalanced stats and costs** for every unit, weapon and armor piece.

---

This is my first project, many of you can recognize the main name and many names inside from other famous ip, my idea is to share this project to their game-developing team in
hope to get recognized as what i am trying to do, i'm a solo developer from Italy, and this is what my free time has produced. 
The main idea for this game was to give to players a similar but more complex Kill Team (TSG from Games Workshop) experience.
My first wish was to give a compelling idea to players to compete on each other, and the first name that resonate with that idea was Trazyn
from the book "The infinite and the Diviner", and from it derived an idea. Not-CANON fan fictional idea (had to specify):
Trazyn multiplied himself an infinity of times, all of his clone have been unleashed losing connection to the real-one and started to claim the one and only name
these Trazyn (the players) coulnd't find a way out of this riddle, who was the one. So instead of killing each other they started using the Museum 
functionality to prove themself as the wittest and smartest and why not, the better Trazyn above all. Using as puppets the armies stored in his museum
the many Trazyn will match and compete each other in a series of trial and between themselves to reach the Rank 1.
This game will have: Pvp ranking system with seasonal content, Pve, Pvpve, asimettrical Pvp events. All to earn Titles, Skins and many more feature
The menu will resemble the Hangar from World of Tanks with a similar matchmaking but very different from all other FPS.
Your whole gameplan starts from before matchmaking, building your team with a point system for every type of matchmaking (like the Tanks tier in WoT)
Basically every unit in your squad will use a point buy system where the better the unit/equip, more it will costs.
This opens the game from the very beginning, what will your squad be componed by.

This is the Concept and the final idea. Thank you for reading it.

Now, what is done:
Gameplay wise will feature a similar third person shooter like Gears of war/Space marine 2
Melee wise it will have a Rock paper scissor style, Heavy counter Fast, Fast counters Normal, and Normal Counters Heavy. Parry has a strict timing but it will reward with a Stun like mechanic.
there are 4 stances, 2h Ranged & 1h Ranged, 2 1h Ranged, 1h Ranged & 1h Melee, 2h Melee (thinking on 2 1h Melee)
You will have the standard Buttons as 
WASD movement
Q parry
Shift sprint
F melee attack (every ranged weapon has locked a predetermined attack from the 3 types)
Left click shoot
right click aim
space vault
if you have a melee weapon equipped you get access to melee attack variation, keep pressed F for a Heavy attack, C for a Fast attack.
All melee weapons implemented right now have already different combos, try them out if they make sense

The gamemode to test is a straight up survival against some orks that run at you, storm you with numbers and attack when you are less confident. 
they have a very basic horde system to not attack you all simultaneously but with a stack of 4, after which they will go on cooldown and wait for the others to strike
You can kill them, parry them and inturrept them with Fast attacks since they only have Normal attacks to kill you

What is not done:
Animation, Texture, Audio, Graphics. I am not an artist, i am not an animator, and i've built this in my living room (so no clear audio)

I wish to use the GW content to make this the very much attended Eternal Crusade from many and many years ago (i backed that project with a pc that couldnt even handle it)

Since it's not really Canonically but very in a Trazyn way i hope they can handle the fact that you can compose a team with 3 Guardsman and an Ork without compliance

If anyone finds this out and find the idea cool, wish to give their wishes, wants to support me or insult me for using Trazyn in a non-canon way (BUT WAY MORE COMICAL)
this is my email: millo.leonardo99@gmail.com
Feel free to reach me out and to share your opinion/ideas, every bit, piece or full concept is appreciated, nothing will be wasted. Cya in the museum
