# SPDX-FileCopyrightText: 2006-2025 Knut Reinert & Freie Universität Berlin
# SPDX-FileCopyrightText: 2016-2025 Knut Reinert & MPI für molekulare Genetik
# SPDX-License-Identifier: CC0-1.0

cmake_minimum_required (VERSION 3.25)

# This includes `cmake/test/config.cmake` which takes care of setting up the test infrastructure. It also provides
# the `add_app_test` macro, which is used to add tests to the CMake test suite.
include (test/config)

# This includes `test/data/datasources.cmake`, which makes test data available to the tests.
include (data/datasources.cmake)

add_app_test (build/api_build_test.cpp)
add_app_test (build/cli_build_test.cpp)
add_app_test (search/api_search_test.cpp)
add_app_test (search/cli_provided_data_test.cpp)
add_app_test (search/cli_search_test.cpp)

# `make syncmer_example` will build the syncmer example.
add_executable (syncmer_example EXCLUDE_FROM_ALL syncmer_example.cpp)
target_link_libraries (syncmer_example HIBF-hashing_lib)

message (STATUS "You can run `make check` to build and run tests.")
