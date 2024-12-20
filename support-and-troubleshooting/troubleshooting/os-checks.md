# OS checks

## Check Internet and DNS Connectivity

To get started with the AI Manager, ensure you have internet access and a functioning DNS. To troubleshoot and verify internet connectivity and DNS functionality on a Linux system, follow these steps:

#### 1.. Test Internet Connectivity

To test if you have internet connectivity, you can try pinging an external server like Google's DNS server.

*   **Ping an external server:** Run the following command:

    ```bash
    ping -c 4 8.8.8.8
    ```

    This command sends four ICMP echo requests to Google's DNS server. If you receive replies, your internet connection is working.

#### 2. Verify DNS Functionality

If your network connection is active but you suspect DNS issues, you should verify that DNS resolution functions correctly.

*   **Ping a domain name:** To check if DNS is working, try pinging a domain name:

    ```bash
    ping -c 4 google.com
    ```

    If the domain name resolves to an IP address and you receive replies, your DNS works. If not, you might see an error like "unknown host," indicating a DNS resolution issue.

## **Failed to create SHM:: Function not implemented**

The issue is that the image on the device has not been compiled with the SHM flag. We work with shared memory. (By default, Ubuntu, and Debian, have SHM enabled.) In other words, `CONFIG_SYSVIPC=y` needs to be enabled.

Explanation and Clarification:

1.  **The Issue**:

    The problem arises because the software image (likely an operating system or kernel) on a particular device was not compiled with the SHM (Shared Memory) flag enabled. This flag is necessary for certain features related to shared memory to work properly.
2.  **Shared Memory**:

    Shared memory is a method of inter-process communication (IPC) that allows multiple processes to access the same segment of memory. This is essential for certain applications that need to exchange data quickly without going through the slower process of sending data through sockets or files.
3.  **Ubuntu Default**:

    Ubuntu (which is likely the base operating system being used) has shared memory support enabled by default. This means that the necessary settings for shared memory are turned on in the standard Ubuntu configuration.
4.  **CONFIG\_SYSVIPC=y**:

    This is a configuration option in the Linux kernel. `CONFIG_SYSVIPC` controls whether System V IPC (which includes shared memory, semaphores, and message queues) is enabled in the kernel. The `y` indicates that this option should be enabled. Without this setting, shared memory and other IPC mechanisms would not be available.

Summary: The current device's software image doesn't support shared memory because the SHM flag wasn't enabled during compilation. To fix this, the `CONFIG_SYSVIPC=y` option needs to be enabled in the kernel configuration.

## Make sure _libgomp_ is installed

As is mentioned in 1. Install Network Optix, you need to have `libgomp` (the GNU Offloading and Multi Processing Runtime Library)  installed. You can do so with:

```
sudo apt update
sudo apt upgrade -y
sudo apt-get install -y libgomp1 gdebi wget
```

It should not be necessary after you have installed it. But to double check whether `libgomp` is indeed installed on your system, you can use one of the following methods depending on your operating system:

#### 1. **On Linux (Debian/Ubuntu)**

You can use the `dpkg` command:

```bash
dpkg -l | grep libgomp
```

If `libgomp` is installed, you will see an output listing the package details. If it is not installed, there will be no output.

Alternatively, you can use the `apt` command to search for the package:

```bash
apt list --installed | grep libgomp
```

#### 2. **On Linux (RedHat/CentOS/Fedora)**

You can use the `rpm` command to check if `libgomp` is installed:

```bash
rpm -qa | grep libgomp
```

If `libgomp` is installed, this will display the package name and version.

#### 3. **Using the `ldconfig` Command**

You can also check if the shared library is available using `ldconfig`:

```bash
ldconfig -p | grep libgomp
```

This command will list the path to `libgomp.so` if it is installed.
