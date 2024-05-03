# Container Security
The objective of this repo is to capture knowledge learnt and level up the understanding of building and running a container with quality and cyber considerations. In general the repo covers:
- Cyber concerns of running a rootful container.
- Type of security scans and tools available. 
- How to build a rootless container.
- How to convert a rootful container to rootless.
- When to use docker vs podman.

## Cyber concerns on running rootful container.
To be added.
     
## Type of security scans and tools available
In this table, tools for quality checks are also included. 
   
| Category          |  Type of Scans               | Paid Tools                   | Free Tools                  |
| ----------------- | ---------------------------- | ---------------------------- | --------------------------- |
| Security          | Container Malware Detection  | Prisma Cloud, SEP            |                             |
| Security          | Container CVE Detection      | Openshift ACS                |                             |
| Security          | Container Virus Detection    | SEP                          |                             |
| Quality           | Cyclomatic Complexity        | Parasoft                     |                             |
| Quality           | Static Code Analysis         | Parasoft                     | ESlint , Pylint             |
| Quality           | Code Coverage                | McCabe                       |                             |
| Quality           | SCA                          | Prisma Cloud                 |                             |
| Security          | SAST (whitebox)              | Parasoft, Fortify            | CodeQL (For Github)         |
| Security          | DAST (blackbox)              | WebInspect                   |                             |

- SCA is usually more concern for vendor selling products, to avoid licensing issue
- Scantist is similar to Prisma Cloud. It can bring down application upon detection of malware, etc.

## How to build a rootless container
![image](https://github.com/okyspace/container-security/assets/55354225/d21bf8cb-a227-4fed-bc9c-9c37102f46c9)

## How to convert a rootful container to rootless.
![image](https://github.com/okyspace/container-security/assets/55354225/1160bd4b-fce3-43c9-993a-44b6ec07f911)

## When to use docker vs podman
- In general, there are some cases where you do not have control over the container and you may need to run with port < 1024, e.g vendor product. You may want to run it with docker instead of podman, since there is no good way to run podman with root.
- Although you can set sudo sysctl net.ipv4_xxxxx_port_start=0 to allow running of ports < 1024 with non-root, but this is pending assessment if there will be cyber concerns.

## Selinux
1. Security-Enhanced Linux (SELinux) is a security architecture for Linux® systems that allows administrators to have more control over who can access the system.
2. Selinux setting is found in /etc/sysconfig/selinux or /etc/selinux/config.
3. Default setting is "enforcing" and "targetting".

![image](https://github.com/okyspace/container-security/assets/55354225/eed802eb-b3b0-4533-b4fb-953e2b478fa9)


![image](https://github.com/okyspace/container-security/assets/55354225/eb02f460-73d2-4ff4-8187-99a5c73bf9e6)


### Example
```
# files created at /home
-rw-r--r--. 1 root root unconfined_u:object_r:admin_home_t:s0    14 May  4 01:06 test1.html
-rw-r--r--. 1 root root unconfined_u:object_r:admin_home_t:s0    14 May  4 01:07 test2.html
```

```
# cp file change type context but not move.. 
-rw-r--r--. 1 root root unconfined_u:object_r:httpd_sys_content_t:s0 29 May  3 22:01 index.html
-rw-r--r--. 1 root root unconfined_u:object_r:httpd_sys_content_t:s0 14 May  4 01:07 test1.html
-rw-r--r--. 1 root root unconfined_u:object_r:admin_home_t:s0        14 May  4 01:07 test2.html
```

## Proper use of Linux Folders
| folder     |                                                             |
| -          | -                                                           |
| /etc       | configurations and settings for the system (e.g. .conf)     |
| /usr       | is used for "user programs". Usually your package manager installs all the binaries, shared files etc. from all programs here (except config files, which go to /etc). You can check /usr/bin for binaries, /usr/share for shared files (media, etc), /usr/share/doc for documentation,...     |
| /opt       | there are "other" programs usually put (mostly binary programs, or programs installed from other sources (not the default package manager). Some programs like that (usually compiled) also go to "/usr/local"    |
| /var       | is usually used for log files, 'temporary' files (like mail spool, printer spool, etc), databases, and all other data not tied to a specific user. Logs are usually in "/var/log", databases in "/var/lib" (mysql - "/var/lib/mysql"), etc.    |


## References
1. Does running container with GID 0 cause security issue?
https://access.redhat.com/solutions/6970217
2. Why do containerized processes run with a GID of 0 by default on OpenShift ?
https://access.redhat.com/solutions/6966929
3. Linux File Permission. https://www.redhat.com/sysadmin/linux-file-permissions-explained
4. Linux Selinux with examples. https://www.computernetworkingnotes.com/linux-tutorials/selinux-explained-with-examples-in-easy-language.html
