# Copyright (c) 2024 General Motors GTO LLC
#
# Licensed to the Apache Software Foundation (ASF) under one
# or more contributor license agreements.  See the NOTICE file
# distributed with this work for additional information
# regarding copyright ownership.  The ASF licenses this file
# to you under the Apache License, Version 2.0 (the
# "License"); you may not use this file except in compliance
# with the License.  You may obtain a copy of the License at
#
#   http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing,
# software distributed under the License is distributed on an
# "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
# KIND, either express or implied.  See the License for the
# specific language governing permissions and limitations
# under the License.
# SPDX-FileType: SOURCE
# SPDX-FileCopyrightText: 2024 General Motors GTO LLC
# SPDX-License-Identifier: Apache-2.0

cmake_minimum_required(VERSION 3.20)
project(pubsub VERSION 0.1.0 LANGUAGES CXX)

find_package(spdlog REQUIRED)
find_package(up-cpp REQUIRED)

add_definitions(-DSPDLOG_FMT_EXTERNAL)

# sub
add_executable(sub src/main_sub.cpp src/UTransportDomainSockets.cpp)
target_link_libraries(sub
    PUBLIC
        spdlog::spdlog
        up-cpp::up-cpp
        up-core-api::up-core-api)
target_include_directories(sub
	PRIVATE
	include)

# pub
add_executable(pub src/main_pub.cpp src/UTransportDomainSockets.cpp)
target_link_libraries(pub
    PUBLIC
        spdlog::spdlog
        up-cpp::up-cpp
        up-core-api::up-core-api)
target_include_directories(pub
	PRIVATE
	include)
