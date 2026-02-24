## SDL3 App From Source + ImGui Sample
This is a sample for building and using SDL3, SDL_mixer, SDL_image, SDL_ttf,
and Dear ImGui from source using C++ and CMake. It also demonstrates optional
Debug hotreload support for UI code on Linux and Android, plus platform setup
such as macOS/iOS bundles.
See [src/main.cpp](src/main.cpp) for the code. 

### Building And Running
Are you a complete beginner? If so, read [this](https://github.com/Ravbug/sdl3-sample/wiki/Setting-up-your-computer)!
Otherwise, install CMake and your favorite compiler, and follow the commands below:
```sh
# You need to clone with submodules, otherwise SDL/ImGui dependencies will be missing.
git clone https://github.com/x6prl/sdl3-imgui-sample --depth=1 --recurse-submodules
cd sdl3-imgui-sample
cmake -S . -B build
```
You can also use an init script inside [`config/`](config/). Then open the IDE project inside `build/` 
(If you had CMake generate one) and run!

### Hotreload (Linux/Android Debug builds)
Hotreload is enabled by default where supported (`ENABLE_HOTRELOAD=ON`):

- Linux
- Android

To rebuild only the reloadable module on desktop:
```sh
cmake --build build --target app_hotreload
```

Android helper for pushing updated `libapp_hotreload.so` without reinstalling:
```sh
./config/android-push-hotreload.sh --abi arm64-v8a
```

## Supported Platforms
I have tested the following:
| Platform | Architecture | Generator |
| --- | --- | --- |
| macOS | x86_64, arm64 | Xcode |
| iOS | x86_64, arm64 | Xcode |
| tvOS | x86_64, arm64 | Xcode |
| visionOS* | arm64 | Xcode |
| Windows | x86_64, arm64 | Visual Studio |
| Linux | x86_64, arm64 | Ninja, Make |
| Web* | wasm | Ninja, Make |
| Android* | x86, x64, arm, arm64 | Ninja via Android Studio |

*See further instructions in [`config/`](config/)

Note: UWP support was [removed from SDL3](https://github.com/libsdl-org/SDL/pull/10731) during its development. For historical reasons, you can get a working UWP sample via this commit: [df270da](https://github.com/Ravbug/sdl3-sample/tree/df270daa8d6d48426e128e50c73357dfdf89afbf)

## Updating Submodules
Update all project submodules:
```sh
git submodule update --init --remote
```
This includes `SDL`, `SDL_ttf`, `SDL_mixer`, `SDL_image`, and `src/imgui`.

## Reporting issues
Is something not working? Create an Issue or send a Pull Request on this repository!
