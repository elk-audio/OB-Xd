# OB-Xd

Modified for headless plugin build for [Elk Audio OS](https://elk.audio)

## Building Instructions

1. Open the ´.jucer´ file with the projucer.
2. Enter the path to the VST2 SDK in the field "VST (LEGACY) SDK Folder" in the exporters menu and save to generate the Linux Makefile.
3. Navigate to the folder `OB-Xd/Builds/LinuxMakefile/`.
4. Set up the cross-compilation toolchain with:  

   ```bash
   $ unset LD_LIBRARY_PATH
   $ source /opt/elk-sika64-sdk/environment-setup-aarch64-elk-linux
   ```

5. (optional) Add flags for more aggressive optimizations than the default ones from the toolchain with:  

   ```bash
   $ export CXXFLAGS="-O3 -pipe -ffast-math -felimnate-unused-debug-types"
   ```

6. Finally cross compile the plugin using  

   ```bash
   $ AR=aarch64-elk-linux-gcc-ar make CONFIG=Release CFLAGS="-DJUCE_HEADLESS_PLUGIN_CLIENT=1" V=1 TARGET_ARCH="-march=armv8-a -mtune=cortex-a72"
   ```

## Additional notes

* Make sure to use our [JUCE fork](https://github.com/stez-mind/JUCE/tree/mind/headless_plugin_client) with the branch `mind/headless_plugin_client`.
* If the compilation fails with an error similar to:  

  ```bash
  fatal error: pluginterfaces/vst2.x/aeffect.h: No such file or directory
  ```
  
  you need to manually add the path to the vstsdk to the makefile to the variable called `CPPFLAGS`.
* For further compilation help. Look at our [documentation](https://github.com/elk-audio/elk-docs/blob/master/documents/building_plugins_for_elk.md).
