# ATSrepo
#include "spdlog/spdlog.h"
#include "spdlog/sinks/stdout_color_sinks.h"
void stdout_example()
{
    // create a color multi-threaded logger
    auto console = spdlog::stdout_color_mt("console");    
    auto err_logger = spdlog::stderr_color_mt("stderr");    
    spdlog::get("console")->info("loggers can be retrieved from a global registry using the spdlog::get(logger_name)");
}

#pragma once

#include <iomanip>
#include <locale>
#include <sstream>

namespace utils {

template <typename T>
inline std::string format(const T &value) {
    static std::locale loc("");
    std::stringstream ss;
    ss.imbue(loc);
    ss << value;
    return ss.str();
}

template <>
inline std::string format(const double &value) {
    static std::locale loc("");
    std::stringstream ss;
    ss.imbue(loc);
    ss << std::fixed << std::setprecision(1) << value;
    return ss.str();
}

}  // namespace utils
