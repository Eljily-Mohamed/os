# Introduction

This document provides a step-by-step guide to understanding and verifying each main component in the progressive construction of our operating system. The project is designed so that the source file `main.c` is divided into multiple sections, each encapsulated within `#ifdef ... #endif` macros. Each section includes example code that tests a specific functionality of the OS currently under development.

To test a particular functionality, we define the relevant label with `#define` at the top of `main.c`. This label corresponds to the desired test and will determine which code segment is included during compilation. This approach allows developers to focus on one functionality at a time, enabling modular testing and debugging throughout the OS development.

Below is an overview of the different labels available in `main.c`, each representing a different test case:

- **`MAIN_TEST`**: Tests the mechanics of a system call.
- **`MAIN_EX1`**: Tests the setup of the first task and task switching.
- **`MAIN_EX2`**: Similar to `MAIN_EX1`, but with all tasks executing the same code.
- **`MAIN_EX3`**: Tests semaphore functionality.
- **`MAIN_EX4`**: Demonstrates using a semaphore as a mutex.
- **`MAIN_EX5`**: Tests the timing (temporization) feature.
- **`MAIN_EX6`**: Similar to `MAIN_EX5`, but with two timed tasks.
- **`MAIN_EX7`**: Tests the termination of a task.
- **`MAIN_EX8`**: Tests the virtual file interface.
- **`MAIN_EX9`**: Tests using the RGB LED as a device.
- **`MAIN_EX10`**: Tests using the USR button as a device with interrupt handling for button presses.

Each of these labels allows us to verify a specific aspect of the operating system’s functionality, ensuring robust testing and progressive development. This documentation serves as a guide to understanding each test, its setup, purpose, and expected outcomes as we build the OS component by component.