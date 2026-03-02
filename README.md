<div align="start">
  <h1>Kernel Build Action for Redmi 12C / Poco C55 (earth)</h1>
  <h3><i>Powered By GitHub Actions</i></h3>
</div>

A workflow to automatically build an Android kernel

## Options

> [!NOTE]
> All options are located in [config.env](config.env)

| Base section options | Optional | Description | Example value |
|---------------------|----------|-------------|----------------|
| KERNEL_SOURCE | <div align="center">❌</div> | Link to kernel repository | `https://github.com/user25-dev/android_kernel_xiaomi_earth.git` |
| KERNEL_SOURCE_BRANCH | <div align="center">❌</div> | Branch name of kernel repository | <div align="center">`lineage-23.2`</div> |
| KERNEL_ARCH | <div align="center">❌</div> | The Linux kernel architecture | <div align="center">`arm64`</div> |
| KERNEL_IMAGE_NAME | <div align="center">❌</div> | Format of the kernel image for flashable AnyKernel3 zip | <div align="center">`Image.gz-dtb`</div> |

<br>

| Compiler section options | Optional | Description | Example value |
|--------------------------|----------|-------------|---------------|
| USE_CLANG | <div align="center">✅</div> | Enable Clang toolchain usage and accounting for options written below | <div align="center">`true`</div> |
| CLANG_SOURCE | <div align="center">❌</div> | Link to clang archive or repository | `https://android.googlesource.com/platform/prebuilts/clang/host/linux-x86/+archive/refs/heads/main/clang-r522817.tar.gz` |
| CLANG_BRANCH | <div align="center">✅</div> | Branch name of clang repository | <div align="center">`main`</div> |
| USE_GCC | <div align="center">✅</div> | Enable GCC toolchain usage and accounting for options written below | <div align="center">`false`</div> |
| USE_GCC_64 | <div align="center">✅</div> | Enable GCC 64-bit | <div align="center">`true`</div> |
| GCC_64_SOURCE | <div align="center">❌</div> | Link to GCC 64-bit archive or repository | `https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/aarch64/aarch64-linux-android-4.9/+archive/refs/heads/master.tar.gz` |
| GCC_64_BRANCH | <div align="center">✅</div> | Branch name of GCC 64-bit repository | <div align="center">`main`</div> |
| USE_GCC_32 | <div align="center">✅</div> | Enable GCC 32-bit | <div align="center">`true`</div> |
| GCC_32_SOURCE | <div align="center">❌</div> | Link to GCC 32-bit archive or repository | `https://android.googlesource.com/platform/prebuilts/gcc/linux-x86/arm/arm-linux-androideabi-4.9/+archive/refs/heads/master.tar.gz` |
| GCC_32_BRANCH | <div align="center">✅</div> | Branch name of GCC 32-bit repository | <div align="center">`main`</div> |
> [!IMPORTANT]
> You can use only Clang or GCC, but not both at the same time.

<br>

| Anykernel3 section options | Optional | Description | Example value |
|----------------------------|----------|-------------|---------------|
| USE_ANYKERNEL3 | <div align="center">✅</div> | Enable creating flashable AnyKernel3 zip and accounting for options written below | <div align="center">`true`</div> |
| ANYKERNEL3_SOURCE | <div align="center">❌</div> | Link to AnyKernel3 source | `https://github.com/user25-dev/AnyKernel3.git` |
| ANYKERNEL3_BRANCH | <div align="center">✅</div> | Branch name of AnyKernel3 repository | <div align="center">`main`</div> |

<br>

| Build section options | Optional | Description | Example value |
|-----------------------|----------|-------------|---------------|
| EXTRA_CMDS | <div align="center">✅</div> | Additional compiler options | `LLVM=1 LLVM_IAS=1 LD=ld.lld AS=llvm-as AR=llvm-ar NM=llvm-nm OBJCOPY=llvm-objcopy OBJDUMP=llvm-objdump READELF=llvm-readelf STRIP=llvm-strip CROSS_COMPILE=aarch64-linux-gnu- CROSS_COMPILE_ARM32=arm-linux-gnueabi- CROSS_COMPILE_COMPAT=arm-linux-gnueabi- CONFIG_NO_ERROR_ON_MISMATCH=y TARGET_BUILD_VARIANT=user` |
| DISABLE_LTO | <div align="center">✅</div> | [LTO](https://llvm.org/docs/LinkTimeOptimization.html) is used to optimize the kernel but sometimes causes errors | <div align="center">`false`</div> |
| DISABLE_CC_WERROR | <div align="center">✅</div> | Disable CONFIG_CC_WERROR | <div align="center">`false`</div> |
| ENABLE_PYTHON2 | <div align="center">✅</div> | Many old kernels require python2 to build them | <div align="center">`false`</div> |
| ENABLE_CCACHE | <div align="center">✅</div> | Enable [ccache](https://ccache.dev) | <div align="center">`false`</div> |
| REMOVE_UNUSED_PACKAGES| <div align="center">✅</div> | Remove unnecessary packages and free up more disk space for builder | <div align="center">`false`</div> |
| NEED_DTBO | <div align="center">✅</div> | Upload DTBO | <div align="center">`false`</div> |
| BUILD_BOOT_IMG | <div align="center">✅</div> | Repack boot.img by replacing the kernel in it with the compiled kernel | <div align="center">`false`</div> |
| SOURCE_BOOT_IMAGE | <div align="center">✅</div> | Link to the original boot.img for repackage it | `https://mirrorbits.lineageos.org/full/earth/20260215/boot.img` |

<br>