licenses(["notice"])  # Apache 2

load(
    "@envoy//bazel:envoy_build_system.bzl",
    "envoy_cc_binary",
    "envoy_cc_library",
    "envoy_cc_test",
    "envoy_package",
)

envoy_package()

load("@envoy_api//bazel:api_build_system.bzl", "api_proto_library")

envoy_cc_library(
    name = "consul_connect",
    srcs = ["consul_connect.cc"],
    hdrs = ["consul_connect.h"],
    repository = "@envoy",
    deps = [
        "//:authorize_proto_cc",
        "//api/envoy/config/filter/network/consul_connect/v2:consul_connect_proto_cc",
        "@envoy//include/envoy/network:filter_interface",
        "@envoy//include/envoy/upstream:cluster_manager_interface",
        "@envoy//source/common/common:assert_lib",
        "@envoy//source/common/common:enum_to_int",
        "@envoy//source/common/common:logger_lib",
        "@envoy//source/common/http:message_lib",
        "@envoy//source/common/http:utility_lib",
        "@solo_envoy_common//source/common/buffer:buffer_utility_lib",
    ],
)

envoy_cc_library(
    name = "config",
    srcs = ["config.cc"],
    hdrs = ["config.h"],
    repository = "@envoy",
    deps = [
        ":consul_connect",
        "//source/extensions/filters/network:consul_connect_well_known_names",
        "@envoy//include/envoy/network:filter_interface",
        "@envoy//include/envoy/registry",
        "@envoy//include/envoy/server:filter_config_interface",
        "@envoy//source/extensions/filters/network/common:factory_base_lib",
    ],
)
