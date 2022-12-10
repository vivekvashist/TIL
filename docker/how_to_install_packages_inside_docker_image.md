
#### Error message
```python
# apt install man
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: Unable to locate package man
```

#### run `apt-get update`
```python
# apt-get update
Get:1 http://deb.debian.org/debian bullseye InRelease [116 kB]
Get:2 http://deb.debian.org/debian-security bullseye-security InRelease [48.4 kB]
Get:3 http://deb.debian.org/debian bullseye-updates InRelease [44.1 kB]
Get:4 http://deb.debian.org/debian bullseye/main amd64 Packages [8184 kB]
Get:5 http://deb.debian.org/debian-security bullseye-security/main amd64 Packages [209 kB]
Get:6 http://deb.debian.org/debian bullseye-updates/main amd64 Packages [14.6 kB]
Fetched 8616 kB in 1s (6109 kB/s)
Reading package lists... Done
```

#### install packatges
```python
# apt install man
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Note, selecting 'man-db' instead of 'man'
The following additional packages will be installed:
  bsdextrautils groff-base libpipeline1 libuchardet0
Suggested packages:
  groff apparmor less www-browser
The following NEW packages will be installed:
  bsdextrautils groff-base libpipeline1 libuchardet0 man-db
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 2538 kB of archives.
After this operation, 7390 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://deb.debian.org/debian bullseye/main amd64 bsdextrautils amd64 2.36.1-8+deb11u1 [145 kB]
Get:2 http://deb.debian.org/debian bullseye/main amd64 libuchardet0 amd64 0.0.7-1 [67.8 kB]
Get:3 http://deb.debian.org/debian bullseye/main amd64 groff-base amd64 1.22.4-6 [936 kB]
Get:4 http://deb.debian.org/debian bullseye/main amd64 libpipeline1 amd64 1.5.3-1 [34.3 kB]
Get:5 http://deb.debian.org/debian bullseye/main amd64 man-db amd64 2.9.4-2 [1354 kB]
Fetched 2538 kB in 0s (46.3 MB/s)
debconf: delaying package configuration, since apt-utils is not installed
Selecting previously unselected package bsdextrautils.
(Reading database ... 23422 files and directories currently installed.)
Preparing to unpack .../bsdextrautils_2.36.1-8+deb11u1_amd64.deb ...
Unpacking bsdextrautils (2.36.1-8+deb11u1) ...
Selecting previously unselected package libuchardet0:amd64.
Preparing to unpack .../libuchardet0_0.0.7-1_amd64.deb ...
Unpacking libuchardet0:amd64 (0.0.7-1) ...
Selecting previously unselected package groff-base.
Preparing to unpack .../groff-base_1.22.4-6_amd64.deb ...
Unpacking groff-base (1.22.4-6) ...
Selecting previously unselected package libpipeline1:amd64.
Preparing to unpack .../libpipeline1_1.5.3-1_amd64.deb ...
Unpacking libpipeline1:amd64 (1.5.3-1) ...
Selecting previously unselected package man-db.
Preparing to unpack .../man-db_2.9.4-2_amd64.deb ...
Unpacking man-db (2.9.4-2) ...
Setting up libpipeline1:amd64 (1.5.3-1) ...
Setting up bsdextrautils (2.36.1-8+deb11u1) ...
update-alternatives: using /usr/bin/write.ul to provide /usr/bin/write (write) in auto mode
Setting up libuchardet0:amd64 (0.0.7-1) ...
Setting up groff-base (1.22.4-6) ...
Setting up man-db (2.9.4-2) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 78.)
debconf: falling back to frontend: Readline
Building database of manual pages ...
Processing triggers for libc-bin (2.31-13+deb11u5) ...
```
