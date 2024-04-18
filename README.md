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

## References
1. Does running container with GID 0 cause security issue?
https://access.redhat.com/solutions/6970217
2. ??
