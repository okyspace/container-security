# Container Security
The objective of this repo is to share and level up the understanding of running a container with cyber considerations.

## Scope
1. Concerns of running a container with root user and how to build a rootless container.
   - Cyber concerns of running a rootful container.
   - Example of containerfile to build rootless container.
   - Some examples of why rootless container do not work.
   - When to use docker vs podman.
     
2. Useful Tools and Type of Scans
   
| Category          |  Type of Scans               | Paid Tools                   | Free Tools                  |
| ----------------- | ---------------------------- | ---------------------------- | --------------------------- |
| Security          | Container Malware Detection  | Prisma Cloud, SEP            |                             |
| Security          | Container CVE Detection      | Openshift ACS                |                             |
| Security          | Container Virus Detection    | SEP                          |                             |
| Quality           | Static Code Analysis         | Parasoft                     | ESlint                      |
| Quality           | Code Coverage                | ??                           |                             |
| Quality           | SCA                          | Prisma Cloud                 |                             |
| Security          | SAST (whitebox)              | Parasoft, Fortify            | CodeQL                      |
| Security          | DAST (blackbox)              | WebInspect                   |                             |

- SCA is usually more concern for vendor selling products, to avoid licensing issue
- Scantist is similar to Prisma Cloud. It can bring down application upon detection of malware, etc.

## Building and Running a rootless container
![image](https://github.com/okyspace/container-security/assets/55354225/d21bf8cb-a227-4fed-bc9c-9c37102f46c9)

## Converting an existing rootful to rootless container
![image](https://github.com/okyspace/container-security/assets/55354225/131ed2d9-d944-452a-85ed-7507cdc8e0fb)


## References
1. Does running container with GID 0 cause security issue?
https://access.redhat.com/solutions/6970217
2. ??
