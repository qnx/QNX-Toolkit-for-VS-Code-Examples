# QNX Code Coverage Workflow

This example provides Visual Studio Code configurations for collecting and viewing code coverage results for a QNX application using the QNX Toolkit for Visual Studio Code, GCOV, and LCOV.

The provided `tasks.json` and `launch.json` configurations help automate the code coverage workflow. The application is built with GCC coverage instrumentation, launched on a remote QNX target with the required GCOV environment settings, and the generated coverage data is downloaded to the development host. LCOV is then used to capture the coverage data, and `genhtml` generates an HTML report for viewing the coverage results.

## Requirements

- A **Linux development host**. The workflow uses LCOV and Linux command-line utilities for coverage processing and report generation.
- An **AArch64 QNX target**. The current configuration uses the AArch64 GCOV executable and AArch64 build/output paths.
- LCOV and `genhtml` available on the Linux development host.
- Firefox is used by the provided `Show HTML Report` task to open the generated report.

## What's Included

- `.vscode/tasks.json` – Build and coverage-processing tasks, including coverage instrumentation, GCOV setup, coverage data download, LCOV capture, HTML report generation, and report display.
- `.vscode/launch.json` – QNX GDB launch configurations for normal execution, debugging, and execution with GCOV enabled.

## Workflow

The overall workflow demonstrated by these configurations is:

1. Build the QNX application with coverage instrumentation enabled using `-fprofile-arcs` and `-ftest-coverage`.
2. Launch the application on the QNX target using the GCOV launch configuration.
3. Use `GCOV_PREFIX` and `GCOV_PREFIX_STRIP` to direct generated coverage data to `/tmp` on the target.
4. Download the generated `.gcda` coverage data from the QNX target to the corresponding local build directory.
5. Use LCOV to capture the coverage information.
6. Use `genhtml` to generate an HTML coverage report in the workspace.
7. Open the generated report in Firefox.

## Usage

1. Add the provided `.vscode` configurations to your QNX application project.

2. Open the project in Visual Studio Code on a Linux development host and connect to the QNX target.

3. Build the application with code coverage instrumentation using:

   `QNX: build debug`

4. Run the application using the code coverage launch configuration:

   `QNX: Code_coverage_workflow with GCOV`

5. After the application has finished running, execute:

   `Show HTML Report`

   This task runs the dependent coverage tasks in sequence to clear previous coverage output, download the generated `.gcda` file, capture the coverage results with LCOV, generate the HTML report, and open the report in Firefox.

6. The generated HTML coverage report is available at:

   `coverage/index.html`
