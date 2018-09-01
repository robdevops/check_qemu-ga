# check_qemu-ga
check_qemu-ga plugin for Nagios / Icinga. Checks if the specified guest agents are responding.

## Dependencies
* bash
* libvirt-client (virsh)
* coreutils

## Usage
```
check_qemu-ga-mod <VM list>
```

### Example output
```
sudo /usr/local/sbin/check_qemu-ga helo stark snuffleupagus
WARNING: 3 specified VM not in running state: helo stark snuffleupagus.

echo $?
1
```
```
sudo /usr/local/sbin/check_qemu-ga sdfsdf
WARNING: 1 VM do not exist on this server: sdfsdf.

echo $?
1
```
```
sudo /usr/local/sbin/check_qemu-ga helo stark snuffleupagus
WARNING: 3 VM not responding: helo stark snuffleupagus.

echo $?
1
```
```
sudo /usr/local/sbin/check_qemu-ga helo stark snuffleupagus
OK: 3 of 3 VM responding: helo stark snuffleupagus.

echo $?
0
```
