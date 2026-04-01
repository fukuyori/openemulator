# OpenEmulator installation instructions

These are developer instructions for building OpenEmulator. Users should download a pre-packaged [release](https://openemulator.github.io/) that is ready to use.

## macOS
We aim to be portable, but currently the only officially supported and tested platform is macOS.

To compile OpenEmulator for macOS you need Xcode and several external libraries not available by default. The simplest way to install them is using Homebrew.

### Setup
After cloning this repository, `cd` into it and retrieve the libemulation sources:

	git submodule update --init --recursive

### Dependencies
Install the required dependencies with Homebrew:

	brew install cmake libxml2 libzip portaudio libsndfile libsamplerate

Xcode command-line tools should also be available. If your local Xcode installation has not completed its first-run setup yet, run:

	xcodebuild -runFirstLaunch

### Build libemulation
When the dependencies are installed, build libemulation:

	cmake -Hmodules/libemulation -Bmodules/libemulation/build -DCMAKE_BUILD_TYPE=Release
	cmake --build modules/libemulation/build --config Release

### Build
Open OpenEmulator in Xcode to build, or run this command:

	xcodebuild -project OpenEmulator.xcodeproj -scheme OpenEmulator -configuration Release -derivedDataPath "$(pwd)/.deriveddata" SYMROOT="$(pwd)/build" build

This will create the application bundle `OpenEmulator.app` in the `build/Release` directory.

### Output

- Application bundle:

	`build/Release/OpenEmulator.app`

### Notes

- This fork has been adjusted for Apple Silicon Homebrew installations under `/opt/homebrew`.
- The Xcode project links against the Homebrew-installed libraries directly, so the dependencies above should be installed before building.
- The `-derivedDataPath` option keeps build products and intermediates inside the repository, which is useful in restricted or sandboxed environments.
