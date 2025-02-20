# Copyright (c) Facebook, Inc. and its affiliates.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
add_executable(
  velox_type_test StringViewTest.cpp TypeTest.cpp FilterTest.cpp
                  SubfieldTest.cpp TimestampConversionTest.cpp VariantTest.cpp)

add_test(velox_type_test velox_type_test)

target_link_libraries(
  velox_type_test
  velox_type
  velox_serialization
  velox_external_date
  ${FOLLY}
  ${DOUBLE_CONVERSION}
  ${GTEST_BOTH_LIBRARIES}
  ${gflags_LIBRARIES}
  glog::glog)

add_executable(velox_filter_benchmark FilterBenchmark.cpp)

target_link_libraries(
  velox_filter_benchmark
  velox_type
  velox_serialization
  ${FOLLY}
  ${FOLLY_BENCHMARK}
  ${DOUBLE_CONVERSION}
  ${GTEST_BOTH_LIBRARIES}
  ${gflags_LIBRARIES}
  glog::glog)
