# knife plugin for opennebula

## Description

This plugin gives knife the ability to create, bootstrap, and manage OpenNebula Virtual Machines

## Development

To contribute bug patches or new features, you can use the github Pull Request model. It is assumed that code and documentation are contributed under the Apache License 2.0. 

More info:
* [How to Contribute](http://opennebula.org/software:add-ons#how_to_contribute_to_an_existing_add-on)
* Support: [OpenNebula user mailing list](http://opennebula.org/community:mailinglists)
* Development: [OpenNebula developers mailing list](http://opennebula.org/community:mailinglists)
* Issues Tracking: Github issues (https://github.com/OpenNebula/addon-iscsi/issues)

## Authors

* Leader: Thomas Alrin (alrin@megam.co.in)
* Kishore Kumar (nkishore@megam.co.in)

## Compatibility

This add-on is compatible with OpenNebula 4.4, 4.6.
Tested extensively with 4.6 (EC2)

## Requirements

### Chef

Hosted Chef 11.0.x (or) On Premises Chef (http://www.getchef.com/chef/choose-your-version/) configured with a client.

[For more information about Chef](https://learnchef.opscode.com/get-started/)

## Installation

To install the plugin you need to do the following in your workstation:

* `gem install chef`
* `gem install opennebula`
* `gem install knife-opennebula`


## Configuration

Configuration can be done either of any three ways.

### 1. Configuring the ENV variables

* `export OPENNEBULA_USERNAME="MY_OPENNEBULA_USERNAME"`

* `export OPENNEBULA_PASSWORD="MY_OPENNEBULA_PASSWORD"`

* `export OPENNEBULA_ENDPOINT="MY_OPENNEBULA_ENDPOINT"`


### 2. Configuring knife.rb
* `knife[:opennebula_username] = "MY_OPENNEBULA_USERNAME"`

* `knife[:opennebula_password] = "MY_OPENNEBULA_PASSWORD"`

* `knife[:opennebula_endpoint] = "MY_OPENNEBULA_ENDPOINT"`

### 3. Configure while running commands by passing options
* `-A` or `--username` -> `OPENNEBULA_USERNAME`
* `-K` or `--password` -> `OPENNEBULA_PASSWORD`
* `-e` or `--endpoint` -> `OPENNEBULA_ENDPOINT`

Specific command options can be found by invoking the subcommand with a `--help` flag

## Usage

This plugin provides the following Knife subcommands. Specific command options can be found by invoking the subcommand with a `--help` flag


#### To list the virtual resource templates

`knife opennebula template list`


#### To list the virual machines

`knife opennebula server list`


#### To create a virtual machine by instantiating a template

`knife opennebula server create`


#### To undeploy and delete a virtual machine

`knife opennebula server delete SERVER_NAME`

eg:

    knife opennebula template list -A OPENNEBULA_USERNAME -K OPENNEBULA_USER_PASSWORD -e http://my-opennebula.com:2633/RPC2
    
    knife opennebula server create -A OPENNEBULA_USERNAME -K OPENNEBULA_USER_PASSWORD -e http://my-opennebula.com:2633/RPC2 -t MY_TEMPLATE_NAME -i IDENTITY_FILE -x USER -r 'role[test]' -N TEST1 -n TEST1
    
    knife opennebula server list -A OPENNEBULA_USERNAME -K OPENNEBULA_USER_PASSWORD -e http://my-opennebula.com:2633/RPC2
    
    knife opennebula server delete SERVER_NAME -A OPENNEBULA_USERNAME -K OPENNEBULA_USER_PASSWORD -e http://my-opennebula.com:2633/RPC2 -P -N NODE_NAME

