# Prince of Persia: The Sands of Time RTX Remix compatibility mod
This modification converts SoT's shader based rendering pipeline into fixed-function rendering, which enables compatibility with RTX Remix.

`d3d9.dll` hijacks the game's D3D9 device to make Prince of Persia: The Sands of Time compatible with RTX Remix's path tracer. The game uses VS 1.1 vertex shaders for all geometry — the proxy intercepts every draw call and converts to the D3D9 fixed-function pipeline that Remix understands.

# What to expect
> [!CAUTION]
> This mod is in its early stages of development. Expect flickering, missing, or broken textures/effects. It only enables RTX Remix. Assets are not replaced.

## Known issues and limitations
- Water gets a solid blue placeholder. Animated ripple patterns and proper reflections on pools are not rendered.
- Time powers' screen overlay effects are greatly simplified.
- Fog	is disabled.
- Multiplicative-blend particles are skipped. Complex VS-computed particle motion (ripples, sparkles) is reduced to flat textured quads in world space.
- Some effects may look off (wrong color/no animation/distorted/not like in the original rendering pipeline) or be missing.
- Captured joints in the remix toolkit have no hierarchy and all originate from the same root. This results in spikey looking skeletons.
- Indexed blending for skinned meshes is not supported with RT disabled. You will see distorted character geometry if you disable RT. To test the FF pipeline with RT disabled, press F10 to switch to CPU skinning. Press F10 again to switch back to indexed blending. Note that skeletons are not captured in CPU skinning mode.

# Installation
1. Install the game.
2. Install the [Sands of Time fix compilation](https://www.moddb.com/games/prince-of-persia-the-sands-of-time/downloads/sands-of-time-fix-compilation).
3. Install [RTX Remix](https://github.com/NVIDIAGameWorks/rtx-remix/releases).
4. Place [`d3d9.dll`](https://github.com/kaminoer/pop-sot-rtx/releases/tag/v0.1) in the game folder (for example `C:\Program Files (x86)\Ubisoft\Ubisoft Game Launcher\games\Prince of Persia Sands of Time`).
5. If you want, you can use my `rtx.conf` file (place it in the game folder next to `d3d9.dll`). It has some initial work done with tagged light, UI, sky, etc. textures. Note that this is NOT complete.
