set(TARGET_NAME open_dashboard_idl)

find_package(Protobuf REQUIRED)

protobuf_generate_cpp(PROTO_SRCS PROTO_HDRS open_dashboard.proto)

add_library(${TARGET_NAME}
	${PROTO_SRCS}
	${PROTO_HDRS}
)

target_include_directories(${TARGET_NAME}
	PUBLIC ${Protobuf_INCLUDE_DIRS}
	PUBLIC ${CMAKE_CURRENT_BINARY_DIR}
)

target_link_libraries(${TARGET_NAME}
	${Protobuf_LIBRARIES}
)
