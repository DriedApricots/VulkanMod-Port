# VulkanMod Port

An unofficial port of [VulkanMod](https://github.com/xCollateral/VulkanMod) 0.6.8 by **Collateral** to new Minecraft versions (Fabric). This branch: Minecraft **26.2**. 26.3 is in progress.
Not affiliated with the VulkanMod project.

It contains the code of VulkanMod adapted to the new game version, plus fixes for bugs found while porting. There are
**no additional features or optimizations**. For a version with extra optimizations see
[VulkanMod+](https://github.com/DriedApricots/VulkanModPlus).

## Fixes made while porting

- Crash when minimizing the window or toggling fullscreen (invalid swapchain image index, device lost)
- Flickering / giant cubes on GPUs slower than the CPU: the GPU fence was a stub that always reported completion
- Camera judder 20 times per second caused by texture animation updates starting the frame early
- Section rebuilds lost when neighbouring chunks were not ready yet (missing or ghost blocks after teleports)
- Invisible End sky, sun and moon (buffers filled by copy were created without TRANSFER_DST)
- Crash with Fabric Renderer API block models ("No FeatureRenderer for type Extended Block Model")
- "Music & Sounds" button opening the Vulkan video settings
- Shader compatibility with mods that declare redundant uniform qualifiers (e.g. Xaero's Minimap)
- MAILBOX present mode preferred for uncapped FPS (IMMEDIATE tears and looked jerky on weaker GPUs)

## Requirements

- Minecraft 26.2, Fabric Loader 0.17+
- A GPU with Vulkan 1.2 support
- Not compatible with Sodium, Iris or VulkanMod+

## Building

```
./gradlew build
```

Requires JDK 25. The jar is written to `build/libs/`.

## License

[LGPL-3.0](LICENSE), same as VulkanMod. Bundled LWJGL, Fabric API modules and MixinExtras keep their own licenses, see
`src/main/resources/licenses/THIRD_PARTY.md`.

The port was made with the help of AI (Claude).
