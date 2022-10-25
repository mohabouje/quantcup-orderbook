cmake_minimum_required(VERSION 3.23)
project(ORDERBOOK VERSION 0.0.1 LANGUAGES CXX)

find_package(Boost COMPONENTS REQUIRED)
include_directories( ${Boost_INCLUDE_DIR} )

set(TEST_SRCS order_book.cpp engine.cpp test.cpp)
set(SCORE_SRCS order_book.cpp engine.cpp score.cpp)

add_library(quantcup_orderbook STATIC order_book.cpp engine.cpp)
target_include_directories(quantcup_orderbook PUBLIC ${CMAKE_CURRENT_LIST_DIR})

add_executable(quantcup_test test.cpp)
target_link_libraries(quantcup_test PRIVATE quantcup_orderbook)

add_executable(quantcup_score score.cpp)
target_link_libraries(quantcup_score PRIVATE quantcup_orderbook)
