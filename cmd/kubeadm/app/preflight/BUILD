package(default_visibility = ["//visibility:public"])

load(
    "@io_bazel_rules_go//go:def.bzl",
    "go_library",
    "go_test",
)

go_library(
    name = "go_default_library",
    srcs = [
        "checks.go",
        "checks_unix.go",
        "utils.go",
    ] + select({
        "@io_bazel_rules_go//go/platform:windows_amd64": [
            "checks_windows.go",
        ],
        "//conditions:default": [],
    }),
    importpath = "k8s.io/kubernetes/cmd/kubeadm/app/preflight",
    deps = [
        "//cmd/kube-apiserver/app/options:go_default_library",
        "//cmd/kube-controller-manager/app/options:go_default_library",
        "//cmd/kubeadm/app/apis/kubeadm:go_default_library",
        "//cmd/kubeadm/app/constants:go_default_library",
        "//pkg/apis/core/validation:go_default_library",
        "//pkg/kubeapiserver/authorizer/modes:go_default_library",
        "//pkg/registry/core/service/ipallocator:go_default_library",
        "//pkg/util/initsystem:go_default_library",
        "//pkg/util/version:go_default_library",
        "//pkg/version:go_default_library",
        "//plugin/cmd/kube-scheduler/app:go_default_library",
        "//test/e2e_node/system:go_default_library",
        "//vendor/github.com/PuerkitoBio/purell:go_default_library",
        "//vendor/github.com/blang/semver:go_default_library",
        "//vendor/github.com/spf13/pflag:go_default_library",
        "//vendor/k8s.io/apimachinery/pkg/util/net:go_default_library",
        "//vendor/k8s.io/apimachinery/pkg/util/sets:go_default_library",
        "//vendor/k8s.io/utils/exec:go_default_library",
    ],
)

go_test(
    name = "go_default_test",
    srcs = [
        "checks_test.go",
        "utils_test.go",
    ],
    importpath = "k8s.io/kubernetes/cmd/kubeadm/app/preflight",
    library = ":go_default_library",
    deps = [
        "//cmd/kubeadm/app/apis/kubeadm:go_default_library",
        "//vendor/github.com/renstrom/dedent:go_default_library",
        "//vendor/k8s.io/apimachinery/pkg/util/sets:go_default_library",
        "//vendor/k8s.io/utils/exec:go_default_library",
    ],
)

filegroup(
    name = "package-srcs",
    srcs = glob(["**"]),
    tags = ["automanaged"],
    visibility = ["//visibility:private"],
)

filegroup(
    name = "all-srcs",
    srcs = [":package-srcs"],
    tags = ["automanaged"],
)
