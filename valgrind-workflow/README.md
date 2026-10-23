# QNX Valgrind Configuration

This example provides Visual Studio Code configurations for running Valgrind as part of a QNX development workflow using the QNX Toolkit for Visual Studio Code.

The provided `tasks.json` and `launch.json` configurations help automate the supporting workflow for running an application under Valgrind on a remote QNX target. This includes transferring the required Valgrind files and application binary to the target, running Valgrind, and downloading the generated results to the development host for analysis.

The configurations support both **AArch64** and **x86_64** QNX targets.

## What's Included

- `.vscode/tasks.json` – Tasks for building the application and uploading the Valgrind files required on the QNX target.
- `.vscode/launch.json` – Launch configurations for running an application with Valgrind and downloading the generated Valgrind output.

## Workflow

1. Build the QNX application.
2. Upload the required Valgrind files to the QNX target.
3. Upload the application binary.
4. Run the application under Valgrind on the target.
5. Generate a Valgrind results file.
6. Download the results to the development host for analysis.

## Usage

1. Add the provided `.vscode` configurations to your QNX application project.
2. Open the project in Visual Studio Code and connect to the QNX target.
3. Build the application using:

   `QNX: build debug`

4. Upload the Valgrind files for the target architecture:

   - `QNX: Upload Valgrind Files (aarch64)`
   - `QNX: Upload Valgrind Files (x86_64)`

5. Run the corresponding Valgrind launch configuration:

   - `QNX: run with valgrind (aarch64)`
   - `QNX: run with valgrind (x86_64)`

6. After execution, the Valgrind output is downloaded to the workspace as:

   `valgrind_<timestamp>.valgrind`
