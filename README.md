# vulkan-imgui-cmake
Sample project to test dependencies for Vulkan and GLFW, built by CMake

## Install dependencies
Install CMake (3.25+).

You can either download manually from the [official CMake Download](https://cmake.org/download/)

Or through `winget` on Windows, `brew` on macOS, or through your package manager on any Linux distro.

```shell
winget install -e --id Kitware.CMake
```

```shell
brew install cmake
```

```shell
sudo apt install cmake
```

Install Vulkan SDK (latest).

Install from: [official LunarXchange SDK Download](https://vulkan.lunarg.com/sdk/home).
This is a recommended manual install for all systems.

Install GLFW (3.4):

On Windows:

Recommended: use [`vcpkg`](https://github.com/microsoft/vcpkg):

```shell
vcpkg install glfw3:x64-windows
```

Manually download from [official GLFW Download](https://www.glfw.org/download)

On macOS:

```shell
brew install glfw
```

On Linux, you most likely will have an official package.

## Building

First, clone the repo to a location on your computer to your liking.

```shell
git clone https://github.com/diego-gt/vulkan-imgui-cmake
```

Move into that directory with `cd`. The next steps assume that you're on this root directory.

CMake Presets are provided to make this easier, however, at the time of writing these are macOS only. Make sure to make any modifications you see fit. You most likely will only need to set your preferred compiler with the `CXX` variable and remove the `LDFLAGS` and `CPPFLAGS` variables from the `"environment"` section.

Configure the project. If you modified or added your own presets, change the preset name to the one you want to use.

```shell
cmake --preset windows-debug
```

Build the project. Same consideration related to the preset name applies.

```shell
cmake --build --preset windows-debug
```

If everything was built correctly, you should see your binary executable in `$project_dir/build/src/` if you used the same presets.

Run the built executable

```shell
./build/src/vktest
```

Now you should see a window pop up with the default demo from the `imgui` project.
