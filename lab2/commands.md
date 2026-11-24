## **1. Підготовка середовища**
1. $ docker --version
Docker version 29.9.3, build 5457199

2. $ docker info
Client:
 Version:    29.9.3
 Context:    desktop-linux
 Debug Mode: false
 Plugins:
  agent: Docker AI Agent Runner (Docker Inc.)
    Version:  v1.153.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-agent.exe
  ai: Docker AI Agent - Ask Gordon (Docker Inc.)
    Version:  v1.33.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-ai.exe
  buildx: Docker Buildx (Docker Inc.)
    Version:  v0.38.1
    Path:     C:\Users\galal\.docker\cli-plugins\docker-buildx.exe
  compose: Docker Compose (Docker Inc.)
    Version:  v5.7.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-compose.exe
  debug: Get a shell into any image or container (Docker Inc.)
    Version:  0.49.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-debug.exe
  desktop: Docker Desktop commands (Docker Inc.)
    Version:  4.99.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-desktop.exe
  dhi: CLI for managing Docker Hardened Images (Docker Inc.)
    Version:  v0.0.10
    Path:     C:\Users\galal\.docker\cli-plugins\docker-dhi.exe
  extension: Manages Docker extensions (Docker Inc.)
    Version:  v0.2.32
    Path:     C:\Users\galal\.docker\cli-plugins\docker-extension.exe
  init: Creates Docker-related starter files for your project (Docker Inc.)
    Version:  v1.4.1
    Path:     C:\Users\galal\.docker\cli-plugins\docker-init.exe
  mcp: Docker MCP Plugin (Docker Inc.)
    Version:  v0.44.3
    Path:     C:\Users\galal\.docker\cli-plugins\docker-mcp.exe
  model: Docker Model Runner (Docker Inc.)
    Version:  v1.2.9
    Path:     C:\Users\galal\.docker\cli-plugins\docker-model.exe
  offload: Docker Offload (Docker Inc.)
    Version:  v0.7.36
    Path:     C:\Users\galal\.docker\cli-plugins\docker-offload.exe
  pass: Docker Pass Secrets Manager Plugin (beta) (Docker Inc.)
    Version:  v0.3.2
    Path:     C:\Users\galal\.docker\cli-plugins\docker-pass.exe
  sandbox: "docker sandbox" is deprecated, use Docker Sandboxes instead (Docker
Inc.)
    Version:  v0.13.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-sandbox.exe
  scout: Docker Scout (Docker Inc.)
    Version:  v1.28.0
    Path:     C:\Users\galal\.docker\cli-plugins\docker-scout.exe

Server:
 Containers: 0
  Running: 0
  Paused: 0
  Stopped: 0
 Images: 0
 Server Version: 29.9.3
 Storage Driver: overlayfs
  driver-type: io.containerd.snapshotter.v1
 Logging Driver: local
 Cgroup Driver: cgroupfs
 Cgroup Version: 2
 Plugins:
  Volume: local
  Network: bridge host ipvlan macvlan null overlay
  Log: awslogs fluentd gcplogs gelf journald json-file local splunk syslog
 CDI spec directories:
  /etc/cdi
  /var/run/cdi
 Discovered Devices:
  cdi: docker.com/gpu=webgpu
 Swarm: inactive
 Runtimes: io.containerd.runc.v2 nvidia runc
 Default Runtime: runc
 Init Binary: docker-init
 containerd version: b7a25261e029d68978bbf290df0a62fc819b3c51
 runc version: v1.5.2-0-g29dd3dc2
 init version: de40ad0
 Security Options:
  seccomp
   Profile: builtin
  cgroupns
 Kernel Version: 6.18.58.1-microsoft-standard-WSL2
 Operating System: Docker Desktop
 OSType: linux
 Architecture: x86_64
 CPUs: 8
 Total Memory: 7.713GiB
 Name: docker-desktop
 ID: 03a22083-41f7-42f1-83ed-147390781fdb
 Docker Root Dir: /var/lib/docker
 Debug Mode: false
 HTTP Proxy: http.docker.internal:3128
 HTTPS Proxy: http.docker.internal:3128
 No Proxy: hubproxy.docker.internal
 Labels:
  com.docker.desktop.address=npipe://\\.\pipe\docker_cli
 Experimental: false
 Insecure Registries:
  hubproxy.docker.internal:5555
  127.0.0.0/8
  ::1/128
 Live Restore Enabled: false
 Firewall Backend: iptables

## **2. Запуск вебсервера**
3. $ docker run -d -p 8080:80 --name alex-webserver nginx:1.30
Unable to find image 'nginx:1.30' locally
1.30: Pulling from library/nginx
aa560e7d269a: Pull complete
37fb86c2a767: Pull complete
d573f8ac02d6: Pull complete
8aac28a8701c: Pull complete
3a0b39cdd8e2: Pull complete
77dc24f83d75: Pull complete
59f811ed280c: Pull complete
92dcba877e73: Download complete
b4486ea52d8a: Download complete
Digest: sha256:7fad6c0dff97965adbddf28027d934b111fc0221a554315dc274712f3fba24d3
Status: Downloaded newer image for nginx:1.30
5e295ddf86832f40da14a05fae768927d355d7dc44cf102224b2bd0bbc26e512

4. $ docker ps
CONTAINER ID   IMAGE        COMMAND                  CREATED          STATUS          PORTS                                     NAMES
5e295ddf8683   nginx:1.30   "/docker-entrypoint.…"   54 seconds ago   Up 54 seconds   0.0.0.0:8080->80/tcp, [::]:8080->80/tcp   alex-webserver

5. $ curl -i http://localhost:8080
HTTP/1.1 200 OK
Server: nginx/1.30.7
Date: Mon, 23 Nov 2026 12:12:53 GMT
Content-Type: text/html
Content-Length: 896
Last-Modified: Wed, 11 Nov 2026 18:08:26 GMT
Connection: keep-alive
ETag: "6af4af1a-380"
Accept-Ranges: bytes

<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, nginx is successfully installed and working.
Further configuration is required for the web server, reverse proxy,
API gateway, load balancer, content cache, or other features.</p>

<p>For online documentation and support please refer to
<a href="https://nginx.org/">nginx.org</a>.<br/>
To engage with the community please visit
<a href="https://community.nginx.org/">community.nginx.org</a>.<br/>
For enterprise grade support, professional services, additional
security features and capabilities please refer to
<a href="https://f5.com/nginx">f5.com/nginx</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
## **3. Запуск СКБД**
6. $ docker run -d --name alex-database -e MYSQL_ROOT_PASSWORD=lab2pass mysql:8.4
Unable to find image 'mysql:8.4' locally
8.4: Pulling from library/mysql
0b3d5697e820: Pull complete
5a7ab34260fd: Pull complete
abda743cff12: Pull complete
16ff0dc0f366: Pull complete
a8a79f346bc1: Pull complete
084e06fe4d96: Pull complete
b14917cf1885: Pull complete
c3e99775cc39: Pull complete
335c0ba6129f: Pull complete
332288060cf8: Pull complete
6f4c84f51b8c: Download complete
2047ca069dcd: Download complete
Digest: sha256:a81d043930e51745522bd5c430961cf8286f0a23f0a9a2a6e0108f7ea71b0902
Status: Downloaded newer image for mysql:8.4
693fd2bcefacdf6a5d3b224a5afee0fa6f3cd2a408218a3f05e6bf39dcb2b8eb

7. $ docker ps
CONTAINER ID   IMAGE       COMMAND                  CREATED              STATUS              PORTS                 NAMES
693fd2bcefac   mysql:8.4   "docker-entrypoint.s…"   About a minute ago   Up About a minute   3306/tcp, 33060/tcp   alex-database

8. $ docker logs alex-database
2026-11-23 17:14:20+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 8.4.13-1.el9 started.
2026-11-23 17:14:21+00:00 [Note] [Entrypoint]: Switching to dedicated user 'mysql'
2026-11-23 17:14:21+00:00 [Note] [Entrypoint]: Entrypoint script for MySQL Server 8.4.13-1.el9 started.
2026-11-23 17:14:21+00:00 [Note] [Entrypoint]: Initializing database files
2026-11-23T17:14:21.620080Z 0 [System] [MY-015017] [Server] MySQL Server Initialization - start.
2026-11-23T17:14:21.622095Z 0 [System] [MY-013169] [Server] /usr/sbin/mysqld (mysqld 8.4.13) initializing of server in progress as process 80
2026-11-23T17:14:21.622098Z 0 [System] [MY-015150] [Server] Server version with update: '8.4.13.0'
2026-11-23T17:14:21.631495Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2026-11-23T17:14:22.127640Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2026-11-23T17:14:23.882578Z 6 [Warning] [MY-010453] [Server] root@localhost is created with an empty password ! Please consider switching off the --initialize-insecure option.
2026-11-23T17:14:27.061135Z 0 [System] [MY-015018] [Server] MySQL Server Initialization - end.
2026-11-23 17:14:27+00:00 [Note] [Entrypoint]: Database files initialized
2026-11-23 17:14:27+00:00 [Note] [Entrypoint]: Starting temporary server
2026-11-23T17:14:27.173253Z 0 [System] [MY-015015] [Server] MySQL Server - start.
2026-11-23T17:14:27.501577Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.4.13) starting as process 121
2026-11-23T17:14:27.501582Z 0 [System] [MY-015150] [Server] Server version with update: '8.4.13.0'
2026-11-23T17:14:27.518806Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2026-11-23T17:14:27.946552Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2026-11-23T17:14:28.476033Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2026-11-23T17:14:28.476097Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
2026-11-23T17:14:28.480993Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consid
er choosing a different directory.
2026-11-23T17:14:28.513646Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Socket: /var/run/mysqld/mysqlx.sock
2026-11-23T17:14:28.513846Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.4.13'  socket: '/var/run/mysqld/mysqld.sock'  port: 0  MySQL Co
mmunity Server - GPL.
2026-11-23 17:14:28+00:00 [Note] [Entrypoint]: Temporary server started.
'/var/lib/mysql/mysql.sock' -> '/var/run/mysqld/mysqld.sock'

2026-11-23 17:14:31+00:00 [Note] [Entrypoint]: Stopping temporary server
2026-11-23T17:14:32.011833Z 10 [System] [MY-013172] [Server] Received SHUTDOWN from user root. Shutting down mysqld (Version: 8.4.13).
2026-11-23T17:14:32.698753Z 0 [System] [MY-010910] [Server] /usr/sbin/mysqld: Shutdown complete (mysqld 8.4.13)  MySQL Community Server - GPL.
2026-11-23T17:14:32.698811Z 0 [System] [MY-015016] [Server] MySQL Server - end.
2026-11-23 17:14:33+00:00 [Note] [Entrypoint]: Temporary server stopped

2026-11-23 17:14:33+00:00 [Note] [Entrypoint]: MySQL init process done. Ready for start up.

2026-11-23T17:14:33.037444Z 0 [System] [MY-015015] [Server] MySQL Server - start.
2026-11-23T17:14:33.347475Z 0 [System] [MY-010116] [Server] /usr/sbin/mysqld (mysqld 8.4.13) starting as process 1
2026-11-23T17:14:33.347482Z 0 [System] [MY-015150] [Server] Server version with update: '8.4.13.0'
2026-11-23T17:14:33.357362Z 1 [System] [MY-013576] [InnoDB] InnoDB initialization has started.
2026-11-23T17:14:33.717585Z 1 [System] [MY-013577] [InnoDB] InnoDB initialization has ended.
2026-11-23T17:14:34.089033Z 0 [Warning] [MY-010068] [Server] CA certificate ca.pem is self signed.
2026-11-23T17:14:34.089107Z 0 [System] [MY-013602] [Server] Channel mysql_main configured to support TLS. Encrypted connections are now supported for this channel.
2026-11-23T17:14:34.094670Z 0 [Warning] [MY-011810] [Server] Insecure configuration for --pid-file: Location '/var/run/mysqld' in the path is accessible to all OS users. Consid
er choosing a different directory.
2026-11-23T17:14:34.127610Z 0 [System] [MY-011323] [Server] X Plugin ready for connections. Bind-address: '::' port: 33060, socket: /var/run/mysqld/mysqlx.sock
2026-11-23T17:14:34.127806Z 0 [System] [MY-010931] [Server] /usr/sbin/mysqld: ready for connections. Version: '8.4.13'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  MySQL
 Community Server - GPL.


## **4. Інтерактивний контейнер операційної системи**
9. $ docker run -it --name alex-os alpine:3.24 /bin/sh
Unable to find image 'alpine:3.24' locally
3.24: Pulling from library/alpine
881fc932939e: Pull complete
86ff264fe568: Download complete
c35a7d82b8fa: Download complete
Digest: sha256:f59abe656b692d901e184be3445e084786602108599d2a51d229c0f5a48c71bf
Status: Downloaded newer image for alpine:3.24
docker: Error response from daemon: failed to create task for container: failed to create shim task: OCI runtime create failed: runc create failed: unable to start container
process: error during container init: exec: "D:/Program Files/Git/usr/bin/sh": stat D:/Program Files/Git/usr/bin/sh: no such file or directory

10. $/ # ls /
bin    dev    etc    home   lib    media  mnt    opt    proc   root   run    sbin   srv    sys    tmp    usr    var

11. / # cat /etc/os-release
NAME="Alpine Linux"
ID=alpine
VERSION_ID=3.24.4
PRETTY_NAME="Alpine Linux v3.24"
HOME_URL="https://alpinelinux.org/"
BUG_REPORT_URL="https://gitlab.alpinelinux.org/alpine/aports/-/issues"

12. / # exit

## **5. Фоновий контейнер і docker exec**
13. docker run -d --name alex-os-d alpine:3.24 sleep infinity
064691830c6ba058856520f565164d2dcb4d668618f7e4ef308b8170ebb0ea0f

14. / # ls /
bin    etc    lib    mnt    proc   run    srv    tmp    var dev    home   media  opt    root   sbin   sys    usr

15. / # exit
What's next:
    Try Docker Debug for seamless, persistent debugging tools in any container or image → docker debug alex-os-d
    Learn more at https://docs.docker.com/go/debug-cli/

16. docker ps
CONTAINER ID   IMAGE         COMMAND            CREATED         STATUS         PORTS     NAMES
064691830c6b   alpine:3.24   "sleep infinity"   6 minutes ago   Up 6 minutes             alex-os-d

17. docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED             STATUS                      PORTS     NAMES
064691830c6b   alpine:3.24   "sleep infinity"         6 minutes ago       Up 6 minutes                          alex-os-d
0fe597e4e620   alpine:3.24   "//bin/sh"               39 minutes ago      Exited (0) 9 minutes ago              alex-os
693fd2bcefac   mysql:8.4     "docker-entrypoint.s…"   About an hour ago   Exited (0) 58 minutes ago             alex-database
5e295ddf8683   nginx:1.30    "/docker-entrypoint.…"   7 hours ago         Exited (0) 6 hours ago                alex-webserver

## **6. Дослідження контейнера**
18. docker inspect alex-webserver
[
    {
        "Id": "5e295ddf86832f40da14a05fae768927d355d7dc44cf102224b2bd0bbc26e512",
        "Created": "2026-11-23T12:08:31.3126202Z",
        "Path": "/docker-entrypoint.sh",
        "Args": [
            "nginx",
            "-g",
            "daemon off;"
        ],
        "State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2026-11-23T12:08:31.7952124Z",
            "FinishedAt": "2026-11-23T12:32:43.961213364Z"
        },
        "Image": "sha256:7fad6c0dff97965adbddf28027d934b111fc0221a554315dc274712f3fba24d3",
        "ResolvConfPath": "/var/lib/docker/containers/5e295ddf86832f40da14a05fae768927d355d7dc44cf102224b2bd0bbc26e512/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/5e295ddf86832f40da14a05fae768927d355d7dc44cf102224b2bd0bbc26e512/hostname",
        "HostsPath": "/var/lib/docker/containers/5e295ddf86832f40da14a05fae768927d355d7dc44cf102224b2bd0bbc26e512/hosts",
        "LogPath": "",
        "Name": "/alex-webserver",
        "RestartCount": 0,
        "Driver": "overlayfs",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "local",
                "Config": {}
            },
            "NetworkMode": "bridge",
            "PortBindings": {
                "80/tcp": [
                    {
                        "HostIp": "",
                        "HostPort": "8080"
                    }
                ]
            },
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                31,
                95
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "private",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": null,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/acpi",
                "/proc/asound",
                "/proc/interrupts",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/sys/devices/virtual/powercap",
                "/sys/firmware"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "Storage": {
            "RootFS": {
                "Snapshot": {
                    "Name": "overlayfs"
                }
            }
        },
        "Mounts": [],
        "Config": {
            "Hostname": "5e295ddf8683",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": false,
            "OpenStdin": false,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "NGINX_VERSION=1.30.7",
                "NJS_VERSION=1.0.2",
                "NJS_RELEASE=1~trixie",
                "ACME_VERSION=0.4.2",
                "PKG_RELEASE=1~trixie",
                "DYNPKG_RELEASE=1~trixie"
            ],
            "Cmd": [
                "nginx",
                "-g",
                "daemon off;"
            ],
            "Image": "nginx:1.30",
            "Volumes": null,
            "WorkingDir": "",
            "Entrypoint": [
                "/docker-entrypoint.sh"
            ],
            "Labels": {
                "maintainer": "NGINX Docker Maintainers \u003cdocker-maint@nginx.com\u003e"
            },
            "StopSignal": "SIGQUIT"
        },
        "NetworkSettings": {
            "SandboxID": "",
            "SandboxKey": "",
            "Ports": {},
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "DriverOpts": null,
                    "GwPriority": 0,
                    "NetworkID": "368b4bb599f1b552cc31dd6b2f8c4a808957d60b12ac98f09158967fe437fbbc",
                    "EndpointID": "",
                    "Gateway": "",
                    "IPAddress": "",
                    "MacAddress": "",
                    "IPPrefixLen": 0,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "DNSNames": null
                }
            }
        },
        "ImageManifestDescriptor": {
            "mediaType": "application/vnd.oci.image.manifest.v1+json",
            "digest": "sha256:af61f605a001c7794200cae30093d8ee0da5183318df15fdfff3597ef37a7486",
            "size": 2288,
            "annotations": {
                "com.docker.official-images.bashbrew.arch": "amd64",
                "org.opencontainers.image.base.digest": "sha256:7378260c0a098d27ac206225db5e7d92b8c7c84ea7afccc86eeb513756bbd392",
                "org.opencontainers.image.base.name": "debian:trixie-slim",
                "org.opencontainers.image.created": "2026-11-18T16:34:20Z",
                "org.opencontainers.image.revision": "a2a986d19aac4a79a330e6e0b5171aae4e521926",
                "org.opencontainers.image.source": "https://github.com/nginx/docker-nginx.git#a2a986d19aac4a79a330e6e0b5171aae4e521926:stable/debian",
                "org.opencontainers.image.url": "https://hub.docker.com/_/nginx",
                "org.opencontainers.image.version": "1.30.7"
            },
            "platform": {
                "architecture": "amd64",
                "os": "linux"
            }
        }
    }
]


19. docker inspect --format "{{.State.Status}} {{.Config.Image}}" alex-webserver
exited nginx:1.30

20. docker images
i Info →   U  In Use
IMAGE         ID             DISK USAGE   CONTENT SIZE   EXTRA
alpine:3.24   f59abe656b69         13MB         3.94MB    U
mysql:8.4     a81d043930e5       1.12GB          254MB    U
nginx:1.30    7fad6c0dff97        242MB         66.5MB    U

## **7. Завершення роботи з ресурсами**
21. docker stop alex-webserver
alex-webserver

22. docker rm alex-webserver
alex-webserver

23. docker stop alex-database
alex-database

24. docker stop alex-database alex-os-d
alex-database
alex-os-d

25. docker rm alex-database alex-os alex-os-d
alex-database
alex-os
alex-os-d

26. docker ps -a
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

27. docker rmi nginx:1.30 mysql:8.4 alpine:3.24
Untagged: nginx:1.30
Deleted: sha256:7fad6c0dff97965adbddf28027d934b111fc0221a554315dc274712f3fba24d3
Untagged: mysql:8.4
Deleted: sha256:a81d043930e51745522bd5c430961cf8286f0a23f0a9a2a6e0108f7ea71b0902
Untagged: alpine:3.24
Deleted: sha256:f59abe656b692d901e184be3445e084786602108599d2a51d229c0f5a48c71bf

28. docker images
i Info →   U  In Use
IMAGE   ID             DISK USAGE   CONTENT SIZE   EXTRA