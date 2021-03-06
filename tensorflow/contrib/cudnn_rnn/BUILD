# Description:
#   A Cudnn RNN wrapper.
#   APIs are meant to change over time.

load("//tensorflow:tensorflow.bzl", "cuda_py_test")
load("//tensorflow:tensorflow.bzl", "tf_custom_op_py_library")

package(
    default_visibility = ["//visibility:private"],
    licenses = ["notice"],  # Apache 2.0
)

exports_files(["LICENSE"])

tf_custom_op_py_library(
    name = "cudnn_rnn_py",
    srcs = [
        "__init__.py",
        "python/layers/__init__.py",
        "python/layers/cudnn_rnn.py",
        "python/ops/cudnn_rnn_ops.py",
    ],
    srcs_version = "PY2AND3",
    visibility = ["//visibility:public"],
    deps = [
        "//tensorflow/contrib/checkpoint/python:split_dependency",
        "//tensorflow/contrib/util:util_py",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:cudnn_rnn_ops_gen",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:layers_base",
        "//tensorflow/python:platform",
        "//tensorflow/python:state_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:util",
        "//tensorflow/python:variable_scope",
    ],
)

cuda_py_test(
    name = "cudnn_rnn_ops_test",
    size = "medium",
    srcs = ["python/kernel_tests/cudnn_rnn_ops_test.py"],
    additional_deps = [
        ":cudnn_rnn_py",
        "@absl_py//absl/testing:parameterized",
        "//tensorflow/core:protos_all_py",
        "//tensorflow/contrib/rnn:rnn_py",
        "//tensorflow/python/ops/losses:losses",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:platform_test",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:state_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:variables",
    ],
    shard_count = 2,
    tags = [
        "noasan",  # http://b/62067814
        "requires-gpu-sm35",
    ],
)

cuda_py_test(
    name = "cudnn_rnn_test",
    size = "enormous",
    srcs = ["python/kernel_tests/cudnn_rnn_test.py"],
    additional_deps = [
        ":cudnn_rnn_py",
        "//tensorflow/core:protos_all_py",
        "//tensorflow/contrib/rnn:rnn_py",
        "//tensorflow/python/ops/losses:losses",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:framework",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:math_ops",
        "//tensorflow/python:platform_test",
        "//tensorflow/python:random_ops",
        "//tensorflow/python:state_ops",
        "//tensorflow/python:training",
        "//tensorflow/python:variables",
    ],
    shard_count = 12,
    tags = [
        "noasan",  # http://b/62067814
    ],
)

cuda_py_test(
    name = "cudnn_rnn_ops_benchmark",
    size = "small",
    srcs = ["python/kernel_tests/cudnn_rnn_ops_benchmark.py"],
    additional_deps = [
        ":cudnn_rnn_py",
        "//tensorflow/contrib/rnn:rnn_py",
        "//tensorflow/python:array_ops",
        "//tensorflow/python:client",
        "//tensorflow/python:client_testlib",
        "//tensorflow/python:control_flow_ops",
        "//tensorflow/python:framework_for_generated_wrappers",
        "//tensorflow/python:framework_test_lib",
        "//tensorflow/python:gradients",
        "//tensorflow/python:init_ops",
        "//tensorflow/python:platform",
        "//tensorflow/python:platform_test",
        "//tensorflow/python:variables",
    ],
    tags = [
        "noasan",  # http://b/62067814
        "nomsan",
        "notsan",
    ],
)
