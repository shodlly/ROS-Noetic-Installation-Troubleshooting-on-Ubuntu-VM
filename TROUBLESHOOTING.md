# Resolving "Temporary Failure Resolving" Errors in Ubuntu VM on VirtualBox

## Introduction

This document provides a comprehensive account of the troubleshooting process undertaken to resolve "Temporary Failure Resolving" errors encountered when running `sudo apt update` on Ubuntu Desktop 20.04.1 installed within a VirtualBox VM. The issue involved errors related to failing to resolve URLs for package updates and persisted despite numerous troubleshooting efforts.

## Issue Description

Upon executing the `sudo apt update` command, the following errors were observed:

```
Err:1 http://security.ubuntu.com/ubuntu focal-security InRelease
  Temporary failure resolving 'security.ubuntu.com'

Err:2 http://sa.archive.ubuntu.com/ubuntu focal InRelease
  Temporary failure resolving 'sa.archive.ubuntu.com'

Err:3 http://sa.archive.ubuntu.com/ubuntu focal-updates InRelease
  Temporary failure resolving 'sa.archive.ubuntu.com'

Err:4 http://sa.archive.ubuntu.com/ubuntu focal-backports InRelease
  Temporary failure resolving 'sa.archive.ubuntu.com'

Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/focal/InRelease  Temporary failure resolving 'sa.archive.ubuntu.com'
W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease  Temporary failure resolving 'sa.archive.ubuntu.com'
W: Failed to fetch http://sa.archive.ubuntu.com/ubuntu/dists/focal-backports/InRelease  Temporary failure resolving 'sa.archive.ubuntu.com'
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/focal-security/InRelease  Temporary failure resolving 'security.ubuntu.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.
```

## Troubleshooting Steps

### 1. Initial Troubleshooting
- **Restarted Network Services**: Attempted to restart network services to resolve connectivity issues.
- **Verified Network Adapter Settings**: Ensured that the network adapter settings in VirtualBox were correctly configured.
- **DNS Configuration**: Edited `/etc/resolv.conf` to include Google's DNS servers (8.8.8.8 and 8.8.4.4). This adjustment did not resolve the issue.

### 2. Additional Challenges
- **Persistence of Errors**: Despite applying these initial troubleshooting steps, the errors persisted for over two weeks.
- **Previous Installations**: Encountered similar issues with unmet dependencies and DNS errors during past installations of ROS Noetic and ROS 2 Foxy.
- **Underlying Issues**: Faced errors from the very first command, indicating a deeper issue requiring resolution.

### 3. Expert Recommendations
- **Verify System Time**: Ensure that the time settings on both the host system (Windows) and the VM are accurate.
- **Check Internet Connectivity**: Confirm that the VM has a stable internet connection.
- **Disable Firewall/Proxy**: Temporarily disable any firewall or proxy settings that might interfere with network connectivity.
- **Create a New VM**: If issues persist, consider creating a new VM to rule out configuration problems.
- **Consider Dual Boot**: For long-term stability and performance, consider installing Ubuntu as a dual-boot alongside Windows.

## Resolution

The issue was resolved through the following actions:

1. **Corrected System Time**: Verified and corrected the time settings on both the host system and the VM to ensure synchronization.
2. **Confirmed Internet Connectivity**: Ensured that the VM was properly connected to the internet.
3. **Disabled Interfering Settings**: Checked for and disabled any firewall or proxy settings that might have been causing issues.
4. **Successful Update Command**: With these adjustments, running `sudo apt update` completed successfully without errors.

## Conclusion

The resolution involved correcting system time discrepancies and ensuring proper internet connectivity. While DNS configuration changes did not resolve the issue, addressing network settings and disabling interfering firewalls or proxies proved effective. For persistent problems, creating a new VM or opting for a dual-boot configuration is recommended for better performance and fewer issues.
