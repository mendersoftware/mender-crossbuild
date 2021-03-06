[![Build Status](https://travis-ci.org/mendersoftware/mender-crossbuild.svg?branch=master)](https://travis-ci.org/mendersoftware/mender-crossbuild)
[![codecov](https://codecov.io/gh/mendersoftware/mender-crossbuild/branch/master/graph/badge.svg)](https://codecov.io/gh/mendersoftware/mender-crossbuild)

Mender: over-the-air updater for embedded Linux devices
==============================================

Mender is an open source over-the-air (OTA) software updater for embedded Linux
devices. Mender comprises a client running at the embedded device, as well as
a server that manages deployments across many devices.

Embedded product teams often end up creating homegrown updaters at the last
minute due to the need to fix bugs in field-deployed devices. However, the most
important requirement for an embedded update process is *robustness*, for example
loss of power at any time should not brick a device. This creates a challenge
given the time constraints to develop and maintain a homegrown updater.

Mender aims to address this challenge with a *robust* and *easy to use* updater
for embedded Linux devices, which is open source and available to anyone.

Robustness is ensured with *atomic* image-based deployments using a dual A/B
rootfs partition layout. This makes it always possible to roll back to a working state, even
when losing power at any time during the update process.

Ease of use is addressed with an intuitive UI, [comprehensive documentation](https://docs.mender.io/), a
[meta layer for the Yocto Project](https://github.com/mendersoftware/meta-mender) for *easy integration into existing environments*,
and high quality software (see the test coverage badge).

This repository contains the Mender client updater, which can be run in standalone mode
(manually triggered through its command line interface) or managed mode (connected to the Mender server).

Mender not only provides the client-side updater, but also the backend and UI
for managing deployments as open source. The Mender server is
designed as a microservices architecture and comprises several repositories.


## Cross-compiling the Mender client

The Mender client binary can be cross-compiled for a given device architecture. Note that in this case you will also need to do bootloader integration and partition setup to integrate it to a device. See [the device integration documentation](https://docs.mender.io/devices?target=_blank) for more information.

Pre-compiled tool-chain (e.g. linaro, bootlin) can be used for building Mender client binary as well as self-compiled customized tool-chain built with **crosstool-ng**.

Use *client-cross-compilation-tool --help* command to find out supported CPUs and available options.

**crosstool-ng** dependencies:
* gperf, texinfo, bison, flex, help2man, ncurses-dev

Default target directory for *crosstool-ng* based toolchain is *~/x-tools*.

To work with *go-executable-build* script first specifiy the location of your workspace with the GOPATH environment variable. Copy script to *$GOPATH/src* directory. Use *go get github.com/mendersoftware/mender* to download the Mender client code.

Having tool-chain ready (either pre-compiled or customized) one can compile Mender client binary. Use *go-executable-build* script to perform that job. Building binaries for more that one architecture at once is supported. To distinguish binaries their names follow the scheme: mender-_OS_-_ARCH_.


## Contributing

We welcome and ask for your contribution. If you would like to contribute to Mender, please read our guide on how to best get started [contributing code or documentation](https://github.com/mendersoftware/mender/blob/master/CONTRIBUTING.md).

## License

Mender is licensed under the Apache License, Version 2.0. See [LICENSE](https://github.com/mendersoftware/mender-crossbuild/blob/master/LICENSE) for the full license text.

## Security disclosure

We take security very seriously. If you come across any issue regarding
security, please disclose the information by sending an email to
[security@mender.io](security@mender.io). Please do not create a new public
issue. We thank you in advance for your cooperation.

## Connect with us

* Join the [Mender Hub discussion forum](https://hub.mender.io)
* Follow us on [Twitter](https://twitter.com/mender_io). Please
  feel free to tweet us questions.
* Fork us on [Github](https://github.com/mendersoftware)
* Create an issue in the [bugtracker](https://tracker.mender.io/projects/MEN)
* Email us at [contact@mender.io](mailto:contact@mender.io)
* Connect to the [#mender IRC channel on Freenode](http://webchat.freenode.net/?channels=mender)
