load(
    "//tensorflow/lite/micro/testing:micro_test.bzl",
    "tflite_micro_cc_test",
)
load(
    "//tensorflow/lite/micro:build_def.bzl",
    "cc_library",
    "micro_copts",
)

package(
    default_visibility = ["//visibility:public"],
    licenses = ["notice"],  # Apache 2.0
)

cc_library(
    name = "memory_planner",
    hdrs = [
        "memory_planner.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        "//tensorflow/lite/c:common",
        "//tensorflow/lite/core/api",
    ],
)

cc_library(
    name = "linear_memory_planner",
    srcs = [
        "linear_memory_planner.cc",
    ],
    hdrs = [
        "linear_memory_planner.h",
    ],
    copts = micro_copts(),
    deps = [
        ":memory_planner",
        "//tensorflow/lite/c:common",
        "//tensorflow/lite/micro:micro_compatibility",
    ],
)

cc_library(
    name = "greedy_memory_planner",
    srcs = [
        "greedy_memory_planner.cc",
    ],
    hdrs = [
        "greedy_memory_planner.h",
    ],
    build_for_embedded = True,
    copts = micro_copts(),
    deps = [
        ":memory_planner",
        "//tensorflow/lite/c:common",
        "//tensorflow/lite/micro:micro_compatibility",
    ],
)

tflite_micro_cc_test(
    name = "linear_memory_planner_test",
    srcs = [
        "linear_memory_planner_test.cc",
    ],
    deps = [
        ":linear_memory_planner",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)

tflite_micro_cc_test(
    name = "greedy_memory_planner_test",
    srcs = [
        "greedy_memory_planner_test.cc",
    ],
    deps = [
        ":greedy_memory_planner",
        "//tensorflow/lite/micro/testing:micro_test",
    ],
)
