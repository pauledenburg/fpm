With this VM you can create packages in RPM and/or DEB format 
using [FPM](https://github.com/jordansissel/fpm).



# Start the machine

## Prerequirements
To be able to use this Vagrant box,  you need to have Vagrant and Virtual Box installed:

- Vagrant: [http://www.vagrantup.com/]
- VirtualBox: [https://www.virtualbox.org/]

## Fire up the box

1. Get the source `git clone https://github.com:pauledenburg/fpm; cd fpm`
2. Start the box `vagrant up`

# Create packages
## Debian package with PEAR as its source
`fpm -s pear -a all -n "PHPUnit" --pear-channel pear.phpunit.de --pear-channel-update PHPUnit`

## RPM package based on directory
`fpm -s dir -t rpm -n "slashbin" -v 1.0 /bin /sbin`
