
### update existing list of packages

> ❯❯❯ sudo apt update
 ```python
 [sudo] password for vivek:
 Hit:1 https://repos.insights.digitalocean.com/apt/do-agent main InRelease
 Get:2 http://mirrors.digitalocean.com/ubuntu kinetic InRelease [267 kB]
 Hit:3 https://repos-droplet.digitalocean.com/apt/droplet-agent main InRelease
 Get:4 http://mirrors.digitalocean.com/ubuntu kinetic-updates InRelease [109 kB]
 Get:5 http://security.ubuntu.com/ubuntu kinetic-security InRelease [109 kB]
 Get:6 http://mirrors.digitalocean.com/ubuntu kinetic-backports InRelease [99.9 kB]
 Get:7 http://mirrors.digitalocean.com/ubuntu kinetic-updates/main amd64 Packages [126 kB]
 Get:8 http://mirrors.digitalocean.com/ubuntu kinetic-updates/restricted amd64 Packages [133 kB]
 Get:9 http://mirrors.digitalocean.com/ubuntu kinetic-updates/restricted Translation-en [20.3 kB]
 Get:10 http://mirrors.digitalocean.com/ubuntu kinetic-updates/universe amd64 Packages [60.0 kB]
 Hit:11 https://ppa.launchpadcontent.net/fish-shell/release-3/ubuntu kinetic InRelease
 Get:12 http://mirrors.digitalocean.com/ubuntu kinetic-updates/multiverse amd64 Packages [4948 B]
 Get:13 http://security.ubuntu.com/ubuntu kinetic-security/restricted amd64 Packages [133 kB]
 Hit:14 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu kinetic InRelease
 Get:15 http://security.ubuntu.com/ubuntu kinetic-security/restricted Translation-en [20.3 kB]
 Get:16 http://security.ubuntu.com/ubuntu kinetic-security/restricted amd64 c-n-f Metadata [508 B]
 Get:17 http://security.ubuntu.com/ubuntu kinetic-security/multiverse amd64 Packages [4924 B]
 Get:18 http://security.ubuntu.com/ubuntu kinetic-security/multiverse Translation-en [996 B]
 Get:19 http://security.ubuntu.com/ubuntu kinetic-security/multiverse amd64 c-n-f Metadata [232 B]
 Fetched 1087 kB in 9s (122 kB/s)
 Reading package lists... Done
 Building dependency tree... Done
 Reading state information... Done
 3 packages can be upgraded. Run 'apt list --upgradable' to see them.
 ```

### install prerequestite packages so let `apt` use packages over HTTPS
> ❯❯❯ sudo apt install apt-transport-https ca-certificates curl software-properties-common
 ```python
 Reading package lists... Done
 Building dependency tree... Done
 Reading state information... Done
 apt-transport-https is already the newest version (2.5.3).
 ca-certificates is already the newest version (20211016).
 curl is already the newest version (7.85.0-1ubuntu0.1).
 software-properties-common is already the newest version (0.99.27).
 software-properties-common set to manually installed.
 0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
 ```

### add GPG key for the offical docker repo to your system
> ❯❯❯ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```python
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
OK
```

### add docker repository to APT sources
> ❯❯❯ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
 ```python
 Repository: 'deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable'
 Description:
 Archive for codename: focal components: stable
 More info: https://download.docker.com/linux/ubuntu
 Adding repository.
 Press [ENTER] to continue or Ctrl-c to cancel.
 Adding deb entry to /etc/apt/sources.list.d/archive_uri-https_download_docker_com_linux_ubuntu-kinetic.list
 Adding disabled deb-src entry to /etc/apt/sources.list.d/archive_uri-https_download_docker_com_linux_ubuntu-kinetic.list
 Get:1 https://download.docker.com/linux/ubuntu focal InRelease [57.7 kB]
 Get:2 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages [20.9 kB]
 Hit:3 https://repos.insights.digitalocean.com/apt/do-agent main InRelease
 Get:4 http://mirrors.digitalocean.com/ubuntu kinetic InRelease [267 kB]
 Hit:5 http://security.ubuntu.com/ubuntu kinetic-security InRelease
 Hit:6 http://mirrors.digitalocean.com/ubuntu kinetic-updates InRelease
 Hit:7 http://mirrors.digitalocean.com/ubuntu kinetic-backports InRelease
 Hit:8 https://repos-droplet.digitalocean.com/apt/droplet-agent main InRelease
 Hit:9 https://ppa.launchpadcontent.net/fish-shell/release-3/ubuntu kinetic InRelease
 Hit:10 https://ppa.launchpadcontent.net/git-core/ppa/ubuntu kinetic InRelease
 Fetched 346 kB in 3s (109 kB/s)
 Reading package lists... Done
 W: https://download.docker.com/linux/ubuntu/dists/focal/InRelease: Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
 ```

### make sure you are about to install from docker repo insteead of the default ubuntu repo. Note `docker-ce` is not installed but candidate for install is from docker repo
> ❯❯❯ apt-cache policy docker-ce
```python
docker-ce:
  Installed: (none)
  Candidate: 5:20.10.21~3-0~ubuntu-focal
  Version table:
     5:20.10.21~3-0~ubuntu-focal 500
        500 https://download.docker.com/linux/ubuntu focal/stable amd64 Packages
        <snip>
```

### install docker
> ❯❯❯ sudo apt install docker-ce
 ```python
 Reading package lists... Done
 Building dependency tree... Done
 Reading state information... Done
 The following additional packages will be installed:
   containerd.io docker-ce-cli docker-ce-rootless-extras docker-scan-plugin libltdl7 libslirp0 pigz slirp4netns
 Suggested packages:
   aufs-tools cgroupfs-mount | cgroup-lite
 The following NEW packages will be installed:
   containerd.io docker-ce docker-ce-cli docker-ce-rootless-extras docker-scan-plugin libltdl7 libslirp0 pigz slirp4netns
 0 upgraded, 9 newly installed, 0 to remove and 3 not upgraded.
 Need to get 102 MB of archives.
 After this operation, 384 MB of additional disk space will be used.
 Do you want to continue? [Y/n] y
 Get:1 https://download.docker.com/linux/ubuntu focal/stable amd64 containerd.io amd64 1.6.10-1 [27.7 MB]
 Get:2 http://mirrors.digitalocean.com/ubuntu kinetic/universe amd64 pigz amd64 2.6-1 [63.6 kB]
 Get:3 http://mirrors.digitalocean.com/ubuntu kinetic/main amd64 libltdl7 amd64 2.4.7-4 [40.3 kB]
 Get:4 http://mirrors.digitalocean.com/ubuntu kinetic/main amd64 libslirp0 amd64 4.7.0-1 [62.7 kB]
 Get:5 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce-cli amd64 5:20.10.21~3-0~ubuntu-focal [41.5 MB]
 Get:6 http://mirrors.digitalocean.com/ubuntu kinetic/universe amd64 slirp4netns amd64 1.2.0-1 [33.5 kB]
 Get:7 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce amd64 5:20.10.21~3-0~ubuntu-focal [20.5 MB]
 Get:8 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-ce-rootless-extras amd64 5:20.10.21~3-0~ubuntu-focal [8394 kB]
 Get:9 https://download.docker.com/linux/ubuntu focal/stable amd64 docker-scan-plugin amd64 0.21.0~ubuntu-focal [3622 kB]
 Fetched 102 MB in 3s (38.2 MB/s)
 Selecting previously unselected package pigz.
 (Reading database ... 132478 files and directories currently installed.)
 Preparing to unpack .../0-pigz_2.6-1_amd64.deb ...
 Unpacking pigz (2.6-1) ...
 Selecting previously unselected package containerd.io.
 Preparing to unpack .../1-containerd.io_1.6.10-1_amd64.deb ...
 Unpacking containerd.io (1.6.10-1) ...
 Selecting previously unselected package docker-ce-cli.
 Preparing to unpack .../2-docker-ce-cli_5%3a20.10.21~3-0~ubuntu-focal_amd64.deb ...
 Unpacking docker-ce-cli (5:20.10.21~3-0~ubuntu-focal) ...
 Selecting previously unselected package docker-ce.
 Preparing to unpack .../3-docker-ce_5%3a20.10.21~3-0~ubuntu-focal_amd64.deb ...
 Unpacking docker-ce (5:20.10.21~3-0~ubuntu-focal) ...
 Selecting previously unselected package docker-ce-rootless-extras.
 Preparing to unpack .../4-docker-ce-rootless-extras_5%3a20.10.21~3-0~ubuntu-focal_amd64.deb ...
 Unpacking docker-ce-rootless-extras (5:20.10.21~3-0~ubuntu-focal) ...
 Selecting previously unselected package docker-scan-plugin.
 Preparing to unpack .../5-docker-scan-plugin_0.21.0~ubuntu-focal_amd64.deb ...
 Unpacking docker-scan-plugin (0.21.0~ubuntu-focal) ...
 Selecting previously unselected package libltdl7:amd64.
 Preparing to unpack .../6-libltdl7_2.4.7-4_amd64.deb ...
 Unpacking libltdl7:amd64 (2.4.7-4) ...
 Selecting previously unselected package libslirp0:amd64.
 Preparing to unpack .../7-libslirp0_4.7.0-1_amd64.deb ...
 Unpacking libslirp0:amd64 (4.7.0-1) ...
 Selecting previously unselected package slirp4netns.
 Preparing to unpack .../8-slirp4netns_1.2.0-1_amd64.deb ...
 Unpacking slirp4netns (1.2.0-1) ...
 Setting up docker-scan-plugin (0.21.0~ubuntu-focal) ...
 Setting up containerd.io (1.6.10-1) ...
 Created symlink /etc/systemd/system/multi-user.target.wants/containerd.service → /lib/systemd/system/containerd.service.
 Setting up libltdl7:amd64 (2.4.7-4) ...
 Setting up docker-ce-cli (5:20.10.21~3-0~ubuntu-focal) ...
 Setting up libslirp0:amd64 (4.7.0-1) ...
 Setting up pigz (2.6-1) ...
 Setting up docker-ce-rootless-extras (5:20.10.21~3-0~ubuntu-focal) ...
 Setting up slirp4netns (1.2.0-1) ...
 Setting up docker-ce (5:20.10.21~3-0~ubuntu-focal) ...
 Created symlink /etc/systemd/system/multi-user.target.wants/docker.service → /lib/systemd/system/docker.service.
 Created symlink /etc/systemd/system/sockets.target.wants/docker.socket → /lib/systemd/system/docker.socket.
 Processing triggers for man-db (2.10.2-2) ...
 Processing triggers for libc-bin (2.36-0ubuntu4) ...
 Scanning processes...
 Scanning processor microcode...
 Scanning linux images...
 
 Running kernel seems to be up-to-date.
 
 Failed to check for processor microcode upgrades.
 
 No services need to be restarted.
 
 No containers need to be restarted.
 
 No user sessions are running outdated binaries.
 
 No VM guests are running outdated hypervisor (qemu) binaries on this host.
```

### check docker status 
> ❯❯❯ sudo systemctl status docker
```python
 ● docker.service - Docker Application Container Engine
      Loaded: loaded (/lib/systemd/system/docker.service; enabled; preset: enabled)
      Active: active (running) since Sat 2022-12-03 20:49:20 AEDT; 11s ago
 TriggeredBy: ● docker.socket
        Docs: https://docs.docker.com
    Main PID: 12198 (dockerd)
       Tasks: 7
      Memory: 30.8M
         CPU: 229ms
      CGroup: /system.slice/docker.service
              └─12198 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
```
 
### avoid using `sudo` for running docker command
> ❯❯❯ sudo usermod -aG docker vivek

### apply the new group membership
> ❯❯❯ su - vivek

### check groups
> ❯❯❯ groups
 ```python
 vivek sudo docker
 ```

### check if you can access and download images from Docker Hub
> ❯❯❯ docker run hello-world

```python
Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
 ```
