

# Linux Networking Investigation | Beginner Cybersecurity Portfolio

**Author:** Wajeeha  
**GitHub:** https://github.com/wajeeha-cyber  
**Date:** 14 October 2026  
**Project Level:** Beginner  
**Status:** Completed

## 1. Project Overview

This project documents my practical learning of Linux networking fundamentals using my own Linux virtual machine.

The purpose was to understand network interfaces, routing, hostname resolution, listening sockets, and HTTP responses through basic command-line investigation.

This is an educational networking project, not a penetration test or vulnerability assessment.

## 2. Lab Environment

- Operating System: Linux virtual machine (exact distribution and version to be confirmed)
- Virtualization Software: Oracle VirtualBox
- Working Directory: cyber-lab
- Tools: Linux Terminal, ip, ping, getent, ss, curl
- Scope: My own virtual machine and permitted requests to example.com

## 3. Network Interface Investigation

**Command:** `ip -br addr`

**Purpose:** Identify network interfaces and view their status and IP address information.

**Observation:** I identified the eth0 network interface on my Linux virtual machine. Its status was UP.

**What I Learned:** The ip utility displays network configuration information. The -br option provides brief output, while addr displays address information. An UP interface status does not, by itself, guarantee internet connectivity.

## 4. Default Gateway Investigation

**Command:** `ip route show`

**Purpose:** Examine the Linux routing table and identify the default route.

**Observation:** I identified a default route configured through the eth0 network interface.

**What I Learned:** The default route is used when no more specific route matches a destination. The routing table helps the operating system decide where network traffic should be forwarded.

## 5. Hostname Resolution Investigation

**Command:** `getent ahostsv4 example.com`

**Purpose:** Test IPv4 hostname resolution using the system's configured name-resolution services.

**Observation:** My Linux virtual machine successfully resolved example.com to an IPv4 address.

**What I Learned:** The getent command retrieves information from configured system databases. The ahostsv4 database provides IPv4 address information. DNS may be one of the services used during hostname resolution.

## 6. Listening Ports Investigation

**Command:** `ss -tuln`

**Purpose:** Examine TCP and UDP listening sockets on my Linux virtual machine.

**Observation:** The output showed TCP sockets in the LISTEN state and UDP sockets in the UNCONN state.

**What I Learned:**
- `ss` displays socket information.
- `-t` selects TCP sockets.
- `-u` selects UDP sockets.
- `-l` selects listening sockets.
- `-n` displays numeric addresses and port numbers.

A listening socket does not automatically indicate a security vulnerability or external accessibility.

## 7. HTTP Response Investigation

**Command:** `curl -I https://example.com`

**Purpose:** Inspect HTTP response headers using an HTTP HEAD request.

**Observation:** The server returned HTTP status code 200, indicating a successful request.

**What I Learned:** The curl tool can communicate with web servers using HTTP and HTTPS. The `-I` option requests response headers using the HEAD method. HTTP status code 200 indicates that the request succeeded.

## 8. Additional Commands Practiced

### whoami
Displays the username associated with the current effective user.

### pwd
Prints the current working directory.

### ping
Tests network reachability using ICMP Echo Requests and replies. A successful ping does not prove a system is secure.

### curl -v
Displays verbose connection diagnostics and HTTP request/response information. Sensitive headers should be redacted before sharing.

## 9. Security and Ethical Scope

- All local investigations were performed on my own virtual machine.
- Public HTTP requests were limited to example.com.
- No unauthorized scanning, exploitation, or vulnerability testing was performed.
- No passwords, authentication tokens, or sensitive network details are included in this report.
- A listening port or successful HTTP response does not establish whether a system is secure.

## 10. Project Conclusion

Through this beginner project, I practiced inspecting Linux network interfaces, identifying a default route, resolving a hostname, examining TCP/UDP sockets, and reading HTTP response headers.

I also learned how to explain technical commands and document observations clearly.

This project helped strengthen my networking fundamentals for further cybersecurity studies.

## 11. Next Learning Goals

1. Learn Linux file permissions, users, and processes.
2. Study HTTP methods, headers, cookies, and browser Developer Tools.
3. Practice manual website quality assurance on an authorized demo application.
4. Learn web security fundamentals and responsible vulnerability reporting.
5. Continue building my cybersecurity portfolio with documented practical projects.

Prepared by Wajeeha
GitHub: https://github.com/wajeeha-cyber
Project Type: Beginner Linux Networking Investigation
