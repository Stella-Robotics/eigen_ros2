# eigen_ros2
Automatically download latest eigen library in order to use in ros2 workspace. (Todo)

Currently, CMake Commands has problem in downloading, so manualy installed now.

## Eigen Version : 3.4.0
------------------------
### Usage Example

package.xml
``` xml
<depend>eigen_ros2</depend>
```

CMakeLists.txt
``` CMake
find_package(eigen_ros2 REQUIRED)
target_link_libraries(${your_target} PUBLIC eigen_ros2::eigen_ros2)
```

Source.cpp
``` cpp
#include <Eigen/Core>
```