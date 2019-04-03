# packer_vagrant_builder

## Description
Using this repo will give you the opportunity to create vagrant box with packer based on box from [vagrant cloud](https://app.vagrantup.com/boxes/search)

## Files
- `test.json` - packer json template. Based on that template will be creted your vagrant box

## Requirements
- installed [vagrant](https://www.vagrantup.com/docs/installation/)
- installed [packer](https://www.packer.io/intro/getting-started/install.html)

## Instructions
- Download this repo: `git clone https://github.com/berchev/packer_vagrant_builder.git`
- Change to **packer_vagrant_builder** directory: `cd packer_vagrant_builder`
- Open **test.json** file with your favourite editor and edit **variables** section:
  ```
  "variables": {
    "box_from_vagrant_cloud": "hashicorp/precise64"
  }
  ```
- Instead of **hashicorp/precise64**, type box by your choice from [vagrant cloud](https://app.vagrantup.com/boxes/search)
- Run following command: `packer build test.json`
- Once execution finish, you will find a new directory `output-vagrant`. Inside will find files `package.box` and `Vagrantfile`
- `package.box` is the result box. You can use this box locally or you can upload it to Vagrant cloud


## Important notes
- If you try to build box based on your locally added box with vagrant, you will hit an error:
  ```
  Build 'vagrant' errored: Vagrant error: The box you're attempting to add already exists. Remove it before
  adding it again or add it with the `--force` flag.

  Name: hashicorp/precise64
  Provider: virtualbox
  Version: 1.1.0
  ```
- In this case you need to make sure the box exist among you locally added boxes: `vagrant box list`
- If yes, you can use [skip_add](https://packer.io/docs/builders/vagrant.html#skip_add) 
- Then run `packer build test.json` again.

## TODO
