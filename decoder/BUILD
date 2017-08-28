
cc_library(
    name = "ctc_decoder_with_kenlm",
    srcs = ["beam_search.cc",
            "alphabet.h",
            "trie_node.h"] +
           glob(["kenlm/lm/*.cc", "kenlm/util/*.cc", "kenlm/util/double-conversion/*.cc",
                 "kenlm/lm/*.hh", "kenlm/util/*.hh", "kenlm/util/double-conversion/*.h"],
                exclude = ["kenlm/*/*test.cc", "kenlm/*/*main.cc"]),
    includes = ["kenlm"],
    defines = ["KENLM_MAX_ORDER=6"],
    deps = ["//tensorflow/core:core",
            "//tensorflow/core/util/ctc",
            "//third_party/eigen3",
    ],
)

cc_binary(
    name = "generate_trie",
    srcs = [
        "generate_trie.cpp",
        "trie_node.h",
        "alphabet.h",
    ] + glob(["kenlm/lm/*.cc", "kenlm/util/*.cc", "kenlm/util/double-conversion/*.cc",
                 "kenlm/lm/*.hh", "kenlm/util/*.hh", "kenlm/util/double-conversion/*.h"],
                exclude = ["kenlm/*/*test.cc", "kenlm/*/*main.cc"]),
    includes = ["kenlm"],
    copts = ['-std=c++11'],
    linkopts = ['-lm'],
    defines = ["KENLM_MAX_ORDER=6"],
)
