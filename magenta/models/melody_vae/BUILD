# Copyright 2016 Google Inc. All Rights Reserved.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#    http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

# Description: An VAE model for generating melodies.

licenses(["notice"])  # Apache 2.0

py_library(
    name = "melody_vae",
    srcs = ["__init__.py"],
    visibility = ["//magenta/tools/pip:__subpackages__"],
    deps = [
        ":melody_vae_model",
    ],
)

py_library(
    name = "melody_vae_config_flags",
    srcs = ["melody_vae_config_flags.py"],
    srcs_version = "PY2AND3",
    visibility = [
        # internal model:melody_vae
    ],
    deps = [
        ":melody_vae_model",
        "//magenta",
        # tensorflow dep
    ],
)

py_library(
    name = "melody_vae_model",
    srcs = ["melody_vae_model.py"],
    srcs_version = "PY2AND3",
    deps = [
        "//magenta",
        "//magenta/models/melody_vae:events_vae_model",
    ],
)

py_library(
    name = "melody_vae_sequence_generator",
    srcs = ["melody_vae_sequence_generator.py"],
    srcs_version = "PY2AND3",
    visibility = ["//magenta/interfaces:generator_interfaces"],
    deps = [
        ":melody_vae_model",
        "//magenta",
    ],
)

py_binary(
    name = "melody_vae_create_dataset",
    srcs = ["melody_vae_create_dataset.py"],
    srcs_version = "PY2AND3",
    visibility = [
        # internal model:melody_vae
        "//magenta/tools/pip:__subpackages__",
    ],
    deps = [
        ":melody_vae_config_flags",
        "//magenta",
        # tensorflow dep
    ],
)

py_test(
    name = "melody_vae_create_dataset_test",
    srcs = ["melody_vae_create_dataset_test.py"],
    deps = [
        ":melody_vae_create_dataset",
        ":melody_vae_model",
        "//magenta",
        # tensorflow dep
    ],
)

py_binary(
    name = "melody_vae_train",
    srcs = ["melody_vae_train.py"],
    srcs_version = "PY2AND3",
    visibility = [
        "//magenta/tools/pip:__subpackages__",
    ],
    deps = [
        ":melody_vae_config_flags",
        "//magenta/models/melody_vae:events_vae_graph",
        "//magenta/models/melody_vae:events_vae_train",
        # tensorflow dep
    ],
)

py_binary(
    name = "melody_vae_generate",
    srcs = ["melody_vae_generate.py"],
    srcs_version = "PY2AND3",
    visibility = [
        "//magenta/tools/pip:__subpackages__",
    ],
    deps = [
        ":melody_vae_config_flags",
        ":melody_vae_model",
        ":melody_vae_sequence_generator",
        "//magenta",
        # tensorflow dep
    ],
)

py_library(
    name = "events_vae_graph",
    srcs = ["events_vae_graph.py"],
    srcs_version = "PY2AND3",
    deps = [
        "//magenta",
        # tensorflow dep
    ],
)

py_test(
    name = "events_vae_graph_test",
    srcs = ["events_vae_graph_test.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":events_vae_graph",
        ":events_vae_model",
        "//magenta",
        # tensorflow dep
    ],
)

py_library(
    name = "events_vae_model",
    srcs = ["events_vae_model.py"],
    srcs_version = "PY2AND3",
    deps = [
        ":events_vae_graph",
        "//magenta",
        # tensorflow dep
    ],
)

py_library(
    name = "events_vae_train",
    srcs = ["events_vae_train.py"],
    srcs_version = "PY2AND3",
    deps = [
        # tensorflow dep
    ],
)
