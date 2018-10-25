Install fmtlib with Conan according to the official getting started guide: https://docs.conan.io/en/latest/getting_started.html#a-timer-using-poco-libraries

1. Create projects directory
```
mkdir project && cd project
```

2. Create your projects cpp files
```
touch main.cpp
```

3. Create conanfile.txt
```
[requires]
fmt/5.2.0@bincrafters/stable

[generators]
cmake
```

4. Create your CMakeLists.txt
```
project(ConanTest)
cmake_minimum_required(VERSION 3.12.0)
add_definitions("-std=c++11")

include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
conan_basic_setup()

add_executable(main main.cpp)
target_link_libraries(main ${CONAN_LIBS})
```

5. Setup build directory
```
mkdir build && cd build
```

6. Install Conan dependencies
```
conan install ..
```

7. Build missing depenencies
If depencies are not available in the official repository, they need to be build.
```
conan install --build missing ..
```

8. Building the project
```
ccmake ..
cmake --build .
```

9. Run the executable
