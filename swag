# Swag Function

The `swag` function is designed to perform sliding window aggregation efficiently. It is useful for solving problems that require frequent and efficient computation over a sliding window of elements.

## Table of Contents

1. [Introduction](#introduction)
2. [Function Definition](#function-definition)
3. [Usage](#usage)
4. [Example](#example)
5. [Complexity](#complexity)
6. [Contributing](#contributing)
7. [License](#license)

## Introduction

The sliding window aggregation (SWAG) technique is particularly useful for maintaining a running summary of data as it flows in, especially when working with large datasets. The `swag` function provides a way to compute aggregates like sum, minimum, maximum, or any other associative operation over a sliding window.

## Function Definition

Here's a typical definition of the `swag` function in C++:

```cpp
#include <deque>
#include <functional>
#include <vector>

template<typename T, typename F>
class Swag {
public:
    Swag(F func) : func(func) {}

    void push(const T& value) {
        T aggregated_value = buffer.empty() ? value : func(buffer.back().second, value);
        buffer.emplace_back(value, aggregated_value);
    }

    void pop() {
        if (!buffer.empty()) {
            buffer.pop_front();
        }
    }

    T query() const {
        if (buffer.empty()) {
            throw std::runtime_error("Query on empty buffer");
        }
        return buffer.front().second;
    }

    bool empty() const {
        return buffer.empty();
    }

private:
    F func;
    std::deque<std::pair<T, T>> buffer;
};
