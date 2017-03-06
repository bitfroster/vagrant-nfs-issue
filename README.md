# vagrant-nfs-issue
## Requirements
- Vagrant (version >= 1.8.5)
- Ansible

## Installation
Clone the repository:
```git clone https://github.com/bitfroster/vagrant-nfs-issue.git```

Change your current folder to vagrant-nfs-issue:
```cd vagrant-nfs-issue```

Run ```vagrant up```

Then connect to the machine, go to nfs folder and run ```composer install```:

```vagrant ssh```

```cd nfs```

```composer install```

## Note
Composer works properly with disabled nfs_udp setting:

```config.vm.synced_folder "../nfs", "/home/vagrant/nfs", mount_options: ['rw', 'vers=3', 'fsc' ,'actimeo=2', 'async'], nfs: true, nfs_udp: false```