# header & description

## 首先，需要明确支持当前所有功能的最小cmake版本，基于Modern CMake，至少3.0.0， 而且还要至少发行时间要在支持的c++标准发布后。
cmake minimum_required(VERSION 3.14.1)

## 用法如下
# project(<PROJECT-NAME> [<language-name>...])
# project(<PROJECT-NAME>
#        [VERSION <major>[.<minor>[.<patch>[.<tweak>]]]]
#        [DESCRIPTION <project-description-string>]
#        [HOMEPAGE_URL <url-string>]
#        [LANGUAGES <language-name>...])

project(project_model 
  VERSION 1.0.0
  LANGUAGES C CXX)


## language feature set like c++11， 自版本3.8+后有效。

target_compile_features(myTarget PUBLIC cxx_std_11)
set_target_properties(myTarget PROPERTIES CXX_EXTENSIONS OFF)

## 或者可以使用下面这种模式,自cmake3.1+生效。
# 第一行指定c++标准，第二行告诉cmake需要使用这个，第三行 区分 -std=c++11 和 -std=g++11
# 但尽量不要手工设置flags，毕竟你不想把cmake做好的工作重做一遍，别让cmake退化。

# set_target_properties(myTarget PROPERTIES
#    CXX_STANDARD 11
#    CXX_STANDARD_REQUIRED YES
#    CXX_EXTENSIONS NO
#)
