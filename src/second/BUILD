load("//:gen.bzl", "second_generate_srcjar", "second_generate_file")

package(default_visibility = ["//visibility:public"])

filegroup(
    name = "srcs",
    srcs = ["Main.java"],
)

second_generate_file(
    name = "gen_file",
    package = "second",
    expected = "not to be visible",
)

second_generate_srcjar(
    name = "gen_srcjar",
    package = "second",
    expected = "to be visible",
)

java_library(
    name = "second_file_lib",
    srcs = [":gen_file"],
)

java_library(
    name = "second_srcjar_lib",
    srcs = [":gen_srcjar"],
)

java_library(
    name = "main",
    srcs = [
        ":srcs"
    ],
    deps = [
        ":second_srcjar_lib",
        ":second_file_lib",
    ],
)
