# Sandbox Implementation on AWS EC2

## Project Overview

This project demonstrates the implementation of a security mechanism known as a **sandbox** using an **AWS EC2 instance**. A sandbox is a controlled environment that allows untested or potentially harmful code to run without affecting the host system. The aim of this project is to protect systems from the adverse effects of unverified or untrusted software by isolating the execution environment.

### Objective

- Set up a sandbox environment on an AWS EC2 instance to isolate potentially harmful code.
- Implement the necessary steps to protect the system from security risks using best practices for cloud-based sandboxing.
- Configure and set up a development environment for C programming (make, man, gcc, gdb, valgrind).

---

## Table of Contents

1. [Introduction](#introduction)
2. [Implementation Steps](#implementation-steps)
    - [AWS EC2 Setup Procedure](#aws-ec2-setup-procedure)
    - [Connecting to EC2 Instance](#connecting-to-your-ec2-instance-via-ssh)
    - [Set Up Development Environment for C](#set-the-developing-environment-for-c-language)
3. [Observation](#observation)
4. [Testing](#testing)
5. [Clean Up](#clean-up)
6. [Contributions](#contributions)
7. [License](#license)

---

## Introduction

A **sandbox** is a security measure designed to isolate potentially harmful programs or code from the underlying system. This implementation sets up a sandboxed environment using **AWS EC2** to safely run and test untrusted software without compromising the host system's integrity.

The sandbox environment limits access to critical resources such as:
- **Storage**
- **Memory**
- **Network access**
- **Hardware devices**

In this project, an EC2 instance is set up, configured, and prepared to execute programs in a controlled environment. Additionally, the development environment for C programming is set up to compile, debug, and test programs in the sandbox.

---

## Implementation Steps

### AWS EC2 Setup Procedure

1. **Sign up for an AWS Free Tier Account**: Create a new AWS account if you don’t have one.
2. **Launch an EC2 Instance**: In the AWS Management Console, select EC2 under "Compute" and launch a new instance.
3. **Choose an Amazon Machine Image (AMI)**: Select Ubuntu 20.04 LTS for the operating system.
4. **Select Instance Type**: Choose the Free Tier eligible "t2.micro" instance.
5. **Configure Instance Settings**: Leave default settings or modify based on specific requirements.
6. **Configure Security Group**: Set up a security group to allow inbound SSH access (port 22).
7. **Review and Launch**: Review instance details and create a new key pair for SSH access.
8. **Wait for Instance to Launch**: Once launched, note down the Public IP or DNS of the instance.

### Connecting to Your EC2 Instance (via SSH)

1. **Get the Public IP/DNS**: From the EC2 Dashboard, locate the Public IP or Public DNS.
2. **Set Permissions for the PEM Key**: On Linux or macOS, run `chmod 400 /path/to/your-key.pem` to set the appropriate permissions.
3. **SSH into the EC2 Instance**: Use the SSH command with the PEM file to connect:
   - From Windows (Command Prompt/PowerShell):
     ```bash
     ssh -i "C:\path\to\your-key.pem" ubuntu@ec2-<public-ip>.compute.amazonaws.com
     ```
   - From Linux/macOS:
     ```bash
     ssh -i /path/to/your-key.pem ubuntu@ec2-<public-ip>.compute.amazonaws.com
     ```

---

### Set the Developing Environment for C Language

Once connected to the EC2 instance, follow these steps to install the development tools:

1. **Update System**:
    ```bash
    sudo apt-get update
    sudo apt-get upgrade
    ```

2. **Install Development Tools**:
    ```bash
    sudo apt-get install -y make man gcc gdb valgrind git-all
    ```

3. **Test Installed Tools**:
    - **Make**: 
      ```bash
      make --version
      ```
    - **GCC (Compiler)**: 
      ```bash
      gcc --version
      ```
    - **GDB (Debugger)**:
      ```bash
      gdb --version
      ```
    - **Valgrind**: 
      ```bash
      valgrind --version
      ```
    - **Git**:
      ```bash
      git --version
      ```

4. **Create and Test a Sample C Program**:
    Create a simple C program to test the development environment:
    ```c
    #include <stdio.h>
    int main() {
        printf("Hello, C Programming!\n");
        return 0;
    }
    ```
    Compile and run the program:
    ```bash
    gcc test.c -o test
    ./test
    ```

5. **Test Debugging with GDB**: Run the program inside GDB to check debugging functionality:
    ```bash
    gdb ./test
    ```

---

## Observation

- **AWS EC2 Instance Setup**: The EC2 instance was successfully launched, and the key pair was correctly configured to allow SSH access.
- **Instance Accessibility**: The instance was accessible via SSH after configuring the security group and obtaining the public IP.
- **Successful SSH Connection**: The SSH connection was established without issues, and the command prompt was successfully accessed.
- **Development Environment**: The tools (make, man, gcc, gdb, valgrind, and git) were installed successfully and tested.

---

## Testing

- **Make**: Confirmed that `make` can be used for compiling projects.
- **GCC**: Compiled a test program to ensure the C compiler is working.
- **GDB**: Debugged the C program to verify GDB functionality.
- **Valgrind**: Ran the program with Valgrind to check for memory leaks.
- **Git**: Verified that Git is installed and working correctly.

---

## Clean Up

After testing, remove any unnecessary files such as the test program:
```bash
rm test.c test
```

---
