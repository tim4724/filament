# Filament Release Notes log

**If you are merging a PR into main**: please add the release note below, under the *Release notes

**If you are cherry-picking a commit into an rc/ branch**: add the release note under the
appropriate header in [RELEASE_NOTES.md](./RELEASE_NOTES.md).

## Release notes for next branch cut
- gltf: `KHR_materials_iridescence` is now supported
- gltf: `KHR_materials_anisotropy` is now supported

- engine: fix PCSS soft shadows of point and spot lights using the directional light's bulb radius
- engine: fix a shader program leak when rendering PCSS or VSM shadows with the program cache
  disabled
- vulkan: with the `backend.vulkan.enable_pipeline_cache_persistence` feature flag, the backend
  keeps its `VkPipelineCache` across runs through `Platform::setBlobFunc`, as the GL backend does
  for program binaries; the blob functions must be set before the `Engine` is created
- utils: `bitset` is no longer over-aligned to 16 bytes, which fixes a crash (SIGBUS) creating
  Vulkan descriptor-set layouts on 32-bit ARM
- engine: on Vulkan, a View rendered into the swap chain after others now clears its viewport
  instead of loading it when `ClearOptions::clear` is set and no earlier View overlaps it
- gl: on PowerVR Rogue GE9215, material-instance uniforms are no longer batched and buffer updates
  no longer go through `glMapBufferRange`
