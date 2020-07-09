## system

Contains `System` related information and operations.

### system uptime

System uptime (hh:mm:ss).

```bash
#!/usr/bin/env bash

sys_uptime=`uptime | cut -d ' ' -f2`
echo "$sys_uptime" # 03:26:47
```

### system memory info

System memory information in kilobytes (KB). Available memory information:

- MemTotal
- MemFree
- MemAvailable
- Cached
- Buffers
- Active
- Inactive
- SwapTotal
- SwapFree
- SwapCached

```bash
#!/usr/bin/env bash

sysMemoryMemTotal=`cat /proc/meminfo | grep 'MemTotal' | awk '{print $2}' | head -n 1`
echo "$sysMemoryMemTotal" # total system memory in KB
```

### system distro name

Operating System ID (i.e. Ubuntu).

```bash
#!/usr/bin/env bash

distroName=`lsb_release -i | awk '{print $3}'`
echo "$distroName"
```

### system distro version

Operating System release version (i.e. 16.04).

```bash
#!/usr/bin/env bash

distroName=`lsb_release -r | awk '{print $2}'`
echo "$distroName"
```

### system distro codename

Operating System codename (i.e. xenial).

```bash
#!/usr/bin/env bash

distroName=`lsb_release -c | awk '{print $2}'`
echo "$distroName"
```

### system kernel name

Operating System kernel name (i.e. Linux).

```bash
#!/usr/bin/env bash

kernelName=`uname -s`
echo "$kernelName" # Linux
```

### system kernel release

Operating System kernel release (i.e. 4.4.0-140-generic).

```bash
#!/usr/bin/env bash

kernelRelease=`uname -r`
echo "$kernelRelease" # 4.4.0-140-generic
```

### system processor type

Operating System processor type (i.e. x86_64).

```bash
#!/usr/bin/env bash

processorType=`uname -p`
echo "$processorType" # x86_64
```

### system processor count

Number of processors (cores).

```bash
#!/usr/bin/env bash

processorCount=`lscpu | grep 'CPU(s)' |awk '{print $2}' | head -n 1`
echo "$processorCount" # 4
```

### system processor architecture

Processor architecture (i.e. x86_64).

```bash
#!/usr/bin/env bash

processorArchitecture=`lscpu | grep 'Architecture' |awk '{print $2}' | head -n 1`
echo "$processorArchitecture" # x86_64
```

### system processor model

Processor model name (i.e. Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz).

```bash
#!/usr/bin/env bash

processorModel=`lscpu | grep 'Model name' |cut -d ' ' -f 3- | sed -e 's/^[[:space:]]*//'`
echo "$processorModel" # Intel(R) Core(TM) i5-5200U CPU @ 2.20GHz
```

### system service manage

Manage service (daemon) operations.

- enable
- disable
- start
- stop
- reload
- restart
- status

```bash
sudo systemctl status network-manager
```
