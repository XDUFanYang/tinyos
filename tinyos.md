**bash build.sh的log：显示找不到librustcore.a：**

```
yangfan@yangfan:~/tinyos/TencentOS-tiny/examples/tos_meets_rust$ sudo bash build.sh 
[sudo] yangfan 的密码： 
-- Tencent OS source root: /home/yangfan/tinyos/TencentOS-tiny.
-- The C compiler identification is GNU 6.3.1
-- The CXX compiler identification is GNU 6.3.1
-- The ASM compiler identification is GNU
-- Found assembler: /usr/bin/arm-none-eabi-g++
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - failed
-- Detecting C compile features
-- Detecting C compile features - failed
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - failed
-- Detecting CXX compile features
-- Detecting CXX compile features - failed
Device: STM32G070xx
Processor: STM32G070XX
-- Configuring done
-- Generating done
-- Build files have been written to: /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build
Scanning dependencies of target rustcore
[  1%] Building C object CMakeFiles/rustcore.dir/libs/rustcore/stub.c.obj
/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/libs/rustcore/stub.c: In function 'rust_libcore_stub':
/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/libs/rustcore/stub.c:2:5: warning: implicit declaration of function 'printf' [-Wimplicit-function-declaration]
     printf("Stub in rust libcore library!\r\n");
     ^~~~~~
[  2%] Linking C static library librustcore.a
Error running link command: No such file or directory
CMakeFiles/rustcore.dir/build.make:94: recipe for target 'librustcore.a' failed
make[2]: *** [librustcore.a] Error 2
CMakeFiles/Makefile2:99: recipe for target 'CMakeFiles/rustcore.dir/all' failed
make[1]: *** [CMakeFiles/rustcore.dir/all] Error 2
Makefile:83: recipe for target 'all' failed
make: *** [all] Error 2
```

**重装cmake后再按照build.sh的说明在 /build目录下cmake .. 以下是log:**

```
yangfan@yangfan:~/tinyos/TencentOS-tiny/examples/tos_meets_rust/build$ sudo cmake ..
-- Tencent OS source root: /home/yangfan/tinyos/TencentOS-tiny.
Device: STM32G070xx
Processor: STM32G070XX
COMPILER_PREFIX =
CMAKE_SOURCE_DIR =/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust
CMAKE_C_COMPILER =/usr/bin/arm-none-eabi-gcc
CMAKE_C_FLAGS =-std=gnu99 -Wextra -Wall -Wno-unused-parameter -mcpu=cortex-m0plus -mthumb -fno-builtin -ffunction-sections -fdata-sections -fomit-frame-pointer -mfpu=fpv4-sp-d16 -mfloat-abi=soft   --specs=nano.specs -MMD -MP
CMAKE_C_LINK_EXECUTABLE =<CMAKE_C_COMPILER> <FLAGS> <CMAKE_C_LINK_FLAGS> <LINK_FLAGS> <OBJECTS>  -o <TARGET> <LINK_LIBRARIES>
CMAKE_EXE_LINKER_FLAGS =-Wextra -Wall -Wno-unused-parameter -mcpu=cortex-m0plus -mthumb -fno-builtin -ffunction-sections -fdata-sections -fomit-frame-pointer -mfpu=fpv4-sp-d16 -mfloat-abi=soft  -u _printf_float -Xlinker -T/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/BSP/STM32G070RBTx_FLASH.ld -Wl,-Map=/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build/mqtt_iot_explorer_tc_ch20_oled.map -Wl,--gc-sections -Wl,-v 
CMAKE_AR =
Definitions: 
-- -DSTM32G070xx
-- -DUSE_HAL_DRIVER
Includes: 
-- /home/yangfan/tinyos/TencentOS-tiny/kernel/core/include
-- /home/yangfan/tinyos/TencentOS-tiny/kernel/pm/include
-- /home/yangfan/tinyos/TencentOS-tiny/kernel/hal/include
-- /home/yangfan/tinyos/TencentOS-tiny/arch/arm/arm-v7m/common/include
-- /home/yangfan/tinyos/TencentOS-tiny/arch/arm/arm-v7m/cortex-m0+/gcc
-- /home/yangfan/tinyos/TencentOS-tiny/osal/cmsis_os
-- /home/yangfan/tinyos/TencentOS-tiny/platform/vendor_bsp/st/STM32G0xx_HAL_Driver/Inc
-- /home/yangfan/tinyos/TencentOS-tiny/platform/vendor_bsp/st/STM32G0xx_HAL_Driver/Inc/Legacy
-- /home/yangfan/tinyos/TencentOS-tiny/platform/vendor_bsp/st/CMSIS/Device/ST/STM32G0xx/Include
-- /home/yangfan/tinyos/TencentOS-tiny/platform/vendor_bsp/st/CMSIS/Include
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/inc
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/BSP/Inc
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/TOS_CONFIG
-- /home/yangfan/tinyos/TencentOS-tiny/net/at/include
-- /home/yangfan/tinyos/TencentOS-tiny/devices/esp8266_tencent_firmware
-- /home/yangfan/tinyos/TencentOS-tiny/net/tencent_firmware_module_wrapper
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/BSP/Hardware/CH20
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/BSP/Hardware/OLED
-- /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/BSP/Hardware/PM2D5
Libraries:
-- -lgcc
-- -lc
-- -lnosys
-- -lgcc
-- -lc
-- -lnosys
-- c
-- nosys
-- rustcore
-- rustapp
-- Configuring done
-- Generating done
-- Build files have been written to: /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build
```

**没有提示报错，然后make后提示找不到librustcore.a:**

```
yangfan@yangfan:~/tinyos/TencentOS-tiny/examples/tos_meets_rust/build$ sudo make 
/usr/bin/cmake -H/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust -B/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build --check-build-system CMakeFiles/Makefile.cmake 0
/usr/bin/cmake -E cmake_progress_start /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build/CMakeFiles /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build/CMakeFiles/progress.marks
make -f CMakeFiles/Makefile2 all
make[1]: 进入目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
make -f CMakeFiles/rustcore.dir/build.make CMakeFiles/rustcore.dir/depend
make[2]: 进入目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
cd /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build && /usr/bin/cmake -E cmake_depends "Unix Makefiles" /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build /home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build/CMakeFiles/rustcore.dir/DependInfo.cmake --color=
make[2]: 离开目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
make -f CMakeFiles/rustcore.dir/build.make CMakeFiles/rustcore.dir/build
make[2]: 进入目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
[  1%] Linking C static library librustcore.a
/usr/bin/cmake -P CMakeFiles/rustcore.dir/cmake_clean_target.cmake
/usr/bin/cmake -E cmake_link_script CMakeFiles/rustcore.dir/link.txt --verbose=1
"" qc librustcore.a  CMakeFiles/rustcore.dir/libs/rustcore/stub.c.obj
Error running link command: No such file or directory
CMakeFiles/rustcore.dir/build.make:97: recipe for target 'librustcore.a' failed
make[2]: *** [librustcore.a] Error 2
make[2]: 离开目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
CMakeFiles/Makefile2:102: recipe for target 'CMakeFiles/rustcore.dir/all' failed
make[1]: *** [CMakeFiles/rustcore.dir/all] Error 2
make[1]: 离开目录“/home/yangfan/tinyos/TencentOS-tiny/examples/tos_meets_rust/build”
Makefile:86: recipe for target 'all' failed
make: *** [all] Error 2
```

## 7.20

吐了，这个tinyos好像只能在20.04下面使用，不能在18.04。要不然找不到librustcore.a。那现在就是今晚把笔记本带回去 板子放家里 刷上固件使用，今天把无线的东西刷上去。等待回家...
