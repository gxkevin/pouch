## pouch run

Create a new container and start it

### Synopsis

Create a container object in Pouchd, and start the container. This is useful when you just want to use one command to start a container. 

```
pouch run [OPTIONS] IMAGE [ARG...]
```

### Examples

```
$ pouch run --name test registry.hub.docker.com/library/busybox:latest echo "hi"
hi
$ pouch ps
Name   ID       Status    Image                                            Runtime   Created
test   23f852   stopped   registry.hub.docker.com/library/busybox:latest   runc      4 seconds ago
$ pouch run -d --name test registry.hub.docker.com/library/busybox:latest
90719b5f9a455b3314a49e72e3ecb9962f215e0f90153aa8911882acf2ba2c84
$ pouch ps
Name   ID       Status    Image                                            Runtime   Created
test   90719b   stopped   registry.hub.docker.com/library/busybox:latest   runc      5 seconds ago
$ pouch run --device /dev/zero:/dev/testDev:rwm --name test registry.hub.docker.com/library/busybox:latest ls -l /dev/testDev
crw-rw-rw-    1 root     root        1,   3 Jan  8 09:40 /dev/testnull
	
```

### Options

```
  -a, --attach                       Attach container's STDOUT and STDERR
      --blkio-weight uint16          Block IO (relative weight), between 10 and 1000, or 0 to disable
      --blkio-weight-device value    Block IO weight (relative device weight) (default [])
      --cap-add strings              Add Linux capabilities
      --cap-drop strings             Drop Linux capabilities
      --cgroup-parent string         Optional parent cgroup for the container (default "default")
      --cpu-share int                CPU shares (relative weight)
      --cpuset-cpus string           CPUs in which to allow execution (0-3, 0,1)
      --cpuset-mems string           MEMs in which to allow execution (0-3, 0,1)
  -d, --detach                       Run container in background and print container ID
      --detach-keys string           Override the key sequence for detaching a container
      --device strings               Add a host device to the container
      --device-read-bps value        Limit read rate (bytes per second) from a device (default [])
      --device-read-iops value       Limit read rate (IO per second) from a device (default [])
      --device-write-bps value       Limit write rate (bytes per second) from a device (default [])
      --device-write-iops value      Limit write rate (IO per second) from a device (default [])
      --enableLxcfs                  Enable lxcfs for the container, only effective when enable-lxcfs switched on in Pouchd
      --entrypoint string            Overwrite the default ENTRYPOINT of the image
  -e, --env strings                  Set environment variables for container
  -h, --help                         help for run
      --hostname string              Set container's hostname
      --initscript string            Initial script executed in container
      --intel-rdt-l3-cbm string      Limit container resource for Intel RDT/CAT which introduced in Linux 4.10 kernel
  -i, --interactive                  Attach container's STDIN
      --ipc string                   IPC namespace to use
  -l, --label strings                Set labels for a container
  -m, --memory string                Memory limit
      --memory-extra int             Represent container's memory high water mark percentage, range in [0, 100]
      --memory-force-empty-ctl int   Whether to reclaim page cache when deleting the cgroup of container
      --memory-swap string           Swap limit equal to memory + swap, '-1' to enable unlimited swap
      --memory-swappiness int        Container memory swappiness [0, 100] (default -1)
      --memory-wmark-ratio int       Represent this container's memory low water mark percentage, range in [0, 100]. The value of memory low water mark is memory.limit_in_bytes * MemoryWmarkRatio
      --name string                  Specify name of container
      --net strings                  Set networks to container
      --pid string                   PID namespace to use
      --privileged                   Give extended privileges to the container
      --restart string               Restart policy to apply when container exits
      --rich                         Start container in rich container mode. (default false)
      --rich-mode string             Choose one rich container mode. dumb-init(default), systemd, sbin-init
      --runtime string               OCI runtime to use for this container
      --sche-lat-switch int          Whether to enable scheduler latency count in cpuacct
      --security-opt strings         Security Options
      --sysctl strings               Sysctl options
  -t, --tty                          Allocate a pseudo-TTY
  -u, --user string                  UID
      --uts string                   UTS namespace to use
  -v, --volume strings               Bind mount volumes to container
  -w, --workdir string               Set the working directory in a container
```

### Options inherited from parent commands

```
  -H, --host string        Specify connecting address of Pouch CLI (default "unix:///var/run/pouchd.sock")
      --tlscacert string   Specify CA file of TLS
      --tlscert string     Specify cert file of TLS
      --tlskey string      Specify key file of TLS
      --tlsverify          Use TLS and verify remote
```

### SEE ALSO

* [pouch](pouch.md)	 - An efficient container engine

