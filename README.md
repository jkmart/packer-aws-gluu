# Gluu Server AMI

AMI that should be used to create virtual machines with Gluu Server installed.

## Synopsis

This script will create an AMI with Gluu Server installed and with all of the
required initialization scripts.

The AMI resulting from this script should be the one used to instantiate a
[Gluu Server](https://gluu.org/docs/ce/installation-guide/install/)

## Getting Started

There are a couple of things needed for the script to work.

### Prerequisites

Packer and AWS Command Line Interface tools need to be installed on your local
computer.
To build a base image this uses a AMI filter to get the latest Ubuntu 16.04 Xenial HVM EBS image.

#### Packer

Packer installation instructions can be found
[here](https://www.packer.io/docs/installation.html).

#### AWS Command Line Interface

AWS Command Line Interface installation instructions can be found [here](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

#### Ubuntu AMI's

This AMI will be based on an official Ubuntu AMI. The latest version of that
AMI will be used.

A list of Ubuntu AMI id's can be found at the Ubuntu official page:
[Ubuntu Amazon EC2 Images](https://cloud-images.ubuntu.com/locator/ec2/)

### Usage

In order to create the AMI using this packer template you need to provide a
few options.

```
Usage:
  packer build \
    -var 'aws_access_key=AWS_ACCESS_KEY' \
    -var 'aws_secret_key=<AWS_SECRET_KEY>' \
    -var 'aws_region=<AWS_REGION>' \
    [-var 'option=value'] \
    gluu.json
```

#### Build Options

- `aws_access_key` - *[required]* The AWS access key.
- `aws_ami_name` - The AMI name (default value: "spark").
- `aws_ami_name_prefix` - Prefix for the AMI name (default value: "").
- `aws_instance_type` - The instance type to use for the build (default value: "m3.medium").
- `aws_region` - *[required]* The regions were the build will be performed.
- `aws_secret_key` - *[required]* The AWS secret key.
- `gluu_version` - *[required]* Gluu version (default value: 3.1.1)


#### Configuring the server

[Following the install guide](https://gluu.org/docs/ce/installation-guide/install/) once the server is installed, start
the server and login to the Gluu container
`service gluu-server-3.1.1 start`
`service gluu-server-3.1.1 login`
`cd /install/community-edition-setup`
`./setup.py`
Then answer questions about the deployment.
Note: The server IP or hostname cannot be localhost

## Contributing

1. Fork it!
2. Create your feature branch: `git checkout -b my-new-feature`
3. Commit your changes: `git commit -am 'Add some feature'`
4. Push to the branch: `git push origin my-new-feature`
5. Submit a pull request

## Versioning

This project uses [SemVer](http://semver.org/) for versioning. For the versions
available, see the [tags on this repository](https://github.com/fscm/packer-aws-spark/tags).

## Authors

* **J. Kerry Martin** - [jkmart](https://github.com/jkmart)

* Special thanks to **Frederico Martins** - [fscm](https://github.com/fscm) whose contributions are the basis for this repo

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE)
file for details