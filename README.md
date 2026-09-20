# NauSamples

Native and browser examples for the sibling NauEngineLite checkout. This repository contains the former engine `samples/` tree, including its Git history. The original sample sources and assets retain the copyright and BSD-3-Clause terms in [NAU-LICENSE.txt](NAU-LICENSE.txt); the repository's initial [LICENSE](LICENSE) is also retained.

Initialize the `NauSamples` submodule from the parent Nau checkout. Configure from `NauEngineLite`, using its existing presets. `NAU_SAMPLES_SOURCE_DIR` selects this source directory and defaults to the sibling `NauSamples` folder. Sample binaries retain their engine build locations; minimal browser delivery remains in `build/web-minimal-debug/package` and `build/web-minimal-release/package`.

```powershell
Set-Location ../NauEngineLite
cmake --preset win_vs2022_x64
cmake --build build/win_vs2022_x64 --config Debug --target SceneBaseSample
```

For a custom checkout, pass `-DNAU_SAMPLES_SOURCE_DIR=<absolute path>` when configuring. Native builds need the documented engine toolchain and dependencies; browser builds need the pinned external Emscripten SDK. Reconfigure in a clean build directory after migrating from engine-local samples. See the parent build.md and prerequisites.md for setup and browser commands.

Source builds use the configured sample root for assets. Installed SDK builds use the SDK's own `samples/` directory. Generated shader caches and build artifacts are regenerated and are not migration inputs.

The original sample tree at engine commit `02574c7104725c6c60358c7d579a0e11da2f174b` is preserved by extracted commit `b460dfaad4777ba4cfcd7d8ece808373ffa73b74`, merged with the destination's initial commit. Integration edits follow that merge.
