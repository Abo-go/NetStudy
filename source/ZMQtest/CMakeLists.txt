cmake_minimum_required(VERSION 2.6)

set(target        "ZMQtest")  #对应文件AliceOperationAgent-config.cmake
#// cmake寻找cuda，并且CUDA_ADD_EXECUTABLE等cuda前缀的命令是由cuda提供的，cmake本身不支持
find_package(ZMQ REQUIRED)
find_package(CZMQ REQUIRED)


set(include_path "${CMAKE_CURRENT_SOURCE_DIR}/include")
set(source_path "${CMAKE_CURRENT_SOURCE_DIR}/source")
    
file(GLOB headers
    ${include_path}/*.h
    )
    
file(GLOB sources
    ${source_path}/*.cpp
    )

 add_executable(${target}  WIN32 ${sources} ${headers} ${UIS_HDRS} ${MOCAP_QRC} ${MOCAP_RC} ${LangSrcs} ${LangenSrcs})

target_include_directories(${target}
    PRIVATE
        ${CMAKE_CURRENT_SOURCE_DIR}/include
        ${ZMQ_INCLUDE_DIR}
        ${CZMQ_INCLUDE_DIR}
		${PROJECT_SOURCE_DIR}/thirdparty/pugixml
        )
        
target_link_libraries(${target}
    PRIVATE
        ${ZMQ_LIBRARY}
        ${CZMQ_LIBRARY}
        )
		
