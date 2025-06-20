<!-- (C) Copyright 2025, SECO Mind Srl

SPDX-License-Identifier: Apache-2.0 -->

# Astarte device SDK C++ - Qt example

This example demonstrates how to use the **Astarte device SDK for C++** in a **Qt** application.


## 📁 Example location

```
astarte-device-sdk-cpp/samples/qt
```


## 🛠️ Requirements

- **Qt**

  ⚠️ *Minimum required version: 5.15*

- **CMake**

    ⚠️ *Minimum required version: 3.19*

- **C++ compiler**

    ⚠️ *Requires support for at least C++17*

- **gRPC**

  ⚠️ *Minimum required gRPC version: 1.69.0*

- **Astarte device SDK C++**

## ⚙️ Building the example using Qt Creator UI

1. Open the `astarte-device-sdk-cpp/samples/qt` folder using **Qt Creator** (*Open Project*).
2. Qt Creator will detect `CMakeLists.txt` and prompt you to configure the project.
3. Click the **hammer icon** (🔨) in the lower-left corner of Qt Creator to build the project.
4. The build output will appear in a directory like:

```
samples/qt/build/Desktop_Qt_6_8_1-Debug/
```

> **Note:** The exact folder name may differ depending on your selected Qt kit.

To run the example from root:

```bash
./samples/qt/build/Desktop_Qt_6_8_1-Debug/qt
```

## 🧰 Building from terminal with script

Instead of using **Qt Creator**, you can build the project directly from the terminal using the
provided script:

```bash
./build_sample.sh qt [OPTIONS]
```

After building, the executable can be found in `build` folder.

To run the example from root:

```bash
./samples/qt/build/qt
```

## ⚠️ Notes

If you encounter the following error:

```
'main.moc' file not found
```

Please verify:

- Any class that inherits from `QObject` includes the `Q_OBJECT` macro.
- `main.cpp` is part of the CMake project and recognized by Qt Creator.
- `CMAKE_AUTOMOC` is enabled in your `CMakeLists.txt` (as shown above).

The `main.moc` file is generated automatically during the build if the project is properly
configured.

### 📄 About the CMakeList.txt

Make sure your `CMakeLists.txt` file includes the following content:

```cmake
target_link_libraries(qt
    PRIVATE astarte_device_sdk
)

# Add the root SDK directory as subdirectory
add_subdirectory(${CMAKE_CURRENT_SOURCE_DIR}/../.. ${CMAKE_CURRENT_BINARY_DIR}/lib_build)

set(CMAKE_AUTOMOC ON)
```

This configuration ensures that the **Astarte device SDK** is fetched from GitHub and properly
linked with the Qt project. The `CMAKE_AUTOMOC` setting is essential for Qt’s meta-object compiler
to generate required `.moc` files automatically.
