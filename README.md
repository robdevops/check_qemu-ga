# check_qemu-ga
check_qemu-ga plugin for Nagios / Icinga. Checks if the specified guest agents are responding.

## Dependencies
* bash 4.2
* libvirt-client (virsh)
* coreutils

## Installation
1. Copy the script to /usr/local/sbin/check_qemu-ga
1. Use chown and chmod to ensure the test user can execute it.
1. Give the test user sudo access:
```
visudo 
```
```
icinga ALL=(root) NOPASSWD: /usr/local/sbin/check_qemu-ga
``` 

## Usage
```
Usage: check_qemu-ga [-i '<IGNORED VMs>']
Ignored VMs should be semicolon separated.
```

### Example output
All guests responding:
```
sudo /usr/local/sbin/check_qemu-ga
OK: 3 guests responding: helo stark snuffleupagus.

echo $?
0
```
Some guests not responding:
```
sudo /usr/local/sbin/check_qemu-ga
WARNING: 2 guests not responding: helo stark.

echo $?
1
```
Ignoring guests:
```
sudo /usr/local/sbin/check_qemu-ga -i 'helo;stark'
OK: 1 guests responding: snuffleupagus.

echo $?
0
```
