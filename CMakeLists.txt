cmake_minimum_required(VERSION 3.13)

project(canopen VERSION 0.1 DESCRIPTION "CANopen implementation for raspi")

include_directories(. stack stack/socketCAN example)
set(HEADERS
        stack/socketCAN/CO_driver.h
        stack/socketCAN/CO_Linux_tasks.h
        stack/socketCAN/CO_OD_storage.h
        stack/crc16-ccitt.h
        stack/CO_SDO.h
        stack/CO_Emergency.h
        stack/CO_NMT_Heartbeat.h
        stack/CO_SYNC.h
        stack/CO_PDO.h
        stack/CO_HBconsumer.h
        stack/CO_SDOmaster.h
        stack/CO_LSSmaster.h
        stack/CO_LSSslave.h
        stack/CO_trace.h
        CANopen.h
        example/CO_OD.h)
set(SOURCES
        stack/socketCAN/CO_driver.c
        stack/socketCAN/CO_Linux_tasks.c
        stack/socketCAN/CO_OD_storage.c
        stack/crc16-ccitt.c
        stack/CO_SDO.c
        stack/CO_Emergency.c
        stack/CO_NMT_Heartbeat.c
        stack/CO_SYNC.c
        stack/CO_PDO.c
        stack/CO_HBconsumer.c
        stack/CO_SDOmaster.c
        stack/CO_LSSmaster.c
        stack/CO_LSSslave.c
        stack/CO_trace.c
        CANopen.c
        example/CO_OD.c)

add_library(canopen
        ${SOURCES})

set_target_properties(canopen PROPERTIES
        PUBLIC_HEADER "${HEADERS}")

target_include_directories(canopen PUBLIC . stack stack/socketCAN example)


install(TARGETS canopen LIBRARY DESTINATION canopenlib PUBLIC_HEADER DESTINATION include/caaan)

