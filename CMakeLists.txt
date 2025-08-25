cmake_minimum_required(VERSION 3.10)
project(toyip C)

# 设置C语言标准
set(CMAKE_C_STANDARD 99)

# 生成编译数据库文件
set(CMAKE_EXPORT_COMPILE_COMMANDS ON)

# 编译器标志
set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -Wall -g -Wno-address-of-packed-member")

# 头文件目录
include_directories(include)

# 收集各目录下的源文件
file(GLOB SHELL_SOURCES "shell/*.c")
file(GLOB NET_SOURCES "net/*.c")
file(GLOB LIB_SOURCES "lib/*.c")
file(GLOB ARP_SOURCES "arp/*.c")
file(GLOB IP_SOURCES "ip/*.c")
file(GLOB SOCKET_SOURCES "socket/*.c")
file(GLOB UDP_SOURCES "udp/*.c")
file(GLOB TCP_SOURCES "tcp/*.c")
file(GLOB APP_SOURCES "app/*.c")

# 合并所有源文件
set(ALL_SOURCES
    ${SHELL_SOURCES}
    ${NET_SOURCES}
    ${LIB_SOURCES}
    ${ARP_SOURCES}
    ${IP_SOURCES}
    ${SOCKET_SOURCES}
    ${UDP_SOURCES}
    ${TCP_SOURCES}
    ${APP_SOURCES}
)

# 创建可执行文件
add_executable(toyip ${ALL_SOURCES})

# 链接pthread库
target_link_libraries(toyip pthread)