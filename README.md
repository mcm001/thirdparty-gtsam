# Bulid steps

For rio:

```
curl -SL https://github.com/wpilibsuite/opensdk/releases/download/v2024-1/cortexa9_vfpv3-roborio-academic-2024-x86_64-linux-gnu-Toolchain-12.1.0.tgz | tar xzf - --strip-components=2
cmake -G Ninja -B build -S . --toolchain toolchain-config.cmake
cmake --build build
```
