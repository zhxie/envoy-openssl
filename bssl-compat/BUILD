load("//bazel:envoy_build_system.bzl", "envoy_cmake", "envoy_package")
load("//bazel:envoy_internal.bzl", "envoy_external_dep_path")

filegroup(
    name = "srcs",
    srcs = glob(["**"]),
)

licenses(["notice"])  # Apache 2

envoy_package()

envoy_cmake(
    name = "bssl-compat",
    cache_entries = {
        "OPENSSL_ROOT_DIR": "$EXT_BUILD_DEPS/openssl",
    },
    lib_source = ":srcs",
    out_static_libs = ["libbssl-compat.a"],
    deps = [envoy_external_dep_path("openssl")],
)

alias(
    name = "crypto",
    actual = ":bssl-compat",
    visibility = ["//visibility:public"],
)

alias(
    name = "ssl",
    actual = ":bssl-compat",
    visibility = ["//visibility:public"],
)
