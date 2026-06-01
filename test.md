# test

The Nx AI Manager integrates several runtimes that allow you to benefit from hardware acceleration when running deployed models.

## Fully supported

The following AI accelerators are available out of the box in the current release:

| AI Accelerator     | Support Level | CPU Architecture | Operating System    | API/driver version                   |
| ------------------ | ------------- | ---------------- | ------------------- | ------------------------------------ |
| CPU (OpenVINO)     | Supported     | x86\_64          | Windows, Linux      | OpenVINO runtime (see OpenVINO page) |
| CPU                | Supported     | aarch64          | Linux               | -                                    |
| Nvidia CUDA        | Supported     | x86\_64          | Windows             | CUDA 11, CUDA 12                     |
| Nvidia Jetson Orin | Supported     | aarch64          | Linux (Jetson Orin) | JetPack (Orin supported versions)    |

## Advanced configuration

These accelerators are supported through advanced configuration and additional validation. Contact Nx if you plan to use them in production.

| AI Accelerator            | Support Level          | CPU Architecture | Operating System | API/driver version               |
| ------------------------- | ---------------------- | ---------------- | ---------------- | -------------------------------- |
| Hailo (Hailo 8, Hailo 8L) | Advanced configuration | x86\_64, aarch64 | Linux            | HailoRT (see Hailo Support page) |
| DeepX                     | Advanced configuration | x86\_64, aarch64 | Linux            | DeepX SDK (vendor specific)      |

## Requested and planned integrations

The following vendors have requested and committed to an integration with Nx AI Manager. These accelerators are not yet available in the current release.

| AI Accelerator | Support Level       | CPU Architecture | Operating System | API/driver version |
| -------------- | ------------------- | ---------------- | ---------------- | ------------------ |
| EdgeCortix     | Planned integration | TBD              | TBD              | TBD                |
| Axelera        | Planned integration | TBD              | TBD              | TBD                |
| SiMa.ai        | Planned integration | TBD              | TBD              | TBD                |
| MemryX         | Planned integration | TBD              | TBD              | TBD                |
