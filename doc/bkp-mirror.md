# "bkp-mirror"

This script copies backups to mirror directories, optionally using ssh to pull from remote ("target") servers.

Default config:

`/opt/etc/bkp-mirror`

Default source backups:

`/opt/var/bkp`

Default mirror directories:

`/opt/var/bkp-mirror*` (multiple copies)

Default log:

`/opt/var/log/bkp-mirror.log`

## Setting up remote mirroring

1. Setup target server:
```
adduser bkp
chown .bkp /opt/var/bkp
```

2. Setup mirroring server:
```
adduser bkp
su bkp
ssh-keygen -t rsa -b 4096
ssh-copy-id <target_server> -p <target_port>
```

Register target server to "known_hosts" as sudo user or root:
```
sudo ssh <target_server> -p <target_port>
```

Add target server to "/opt/etc/bkp-mirror" config:
```
pull bkp@<target_server:target_port>
```

Test with:
```
/opt/bin/bkp-mirror
```
