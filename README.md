# Nuand bladeRF specific directions #

Please ensure you have a recent version (any equal to or greater than 0.14) of libbladeRF installed. Instructions on installing libbladeRF can be found here: https://github.com/Nuand/bladeRF/wiki/Getting-Started%3A-Linux

Also please ensure you have the [latest FX3 firwmare](http://hoopycat.com/bladerf_builds/latest/artifacts/firmware.img) flashed to the bladeRF,  .

## OpenBTS Quick Start ##
You can follow the installation instructions found at https://github.com/RangeNetworks/dev/wiki. The only difference is that after the ./clone.sh is run, the confflags environmental variable should be set to --with-bladeRF by running `export confflags=--with-bladeRF'.

1. git clone https://github.com/Nuand/dev
2. cd dev
3. ./clone.sh
4. export confflags=--with-bladeRF
5. ./build.sh
6. sudo dpkg -i BUILD-timestamp/*.deb


### Starting OpenBTS ###

To start OpenBTS two things have to be done.
First, the FPGA has to be loaded by running either:
    bladeRF-cli -l openbts/TransceiverRAD1/hostedx115bts.rbf
    bladeRF-cli -l openbts/TransceiverRAD1/hostedx40bts.rbf

Second, OpenBTS has to be started as a service or as a stand-alone application. Following the instructions given by RangeNetworks should be pretty straight forward https://github.com/RangeNetworks/dev/wiki#running . Alternatively, it is possible to run OpenBTS directly from the Github checkout directory if all dependencies are installed. You can do this by running the following commands:

1. cd openbts/apps
2. ln -sf ../TransceiverRAD1/transceiver transceiver
3. sudo ./OpenBTS

Once OpenBTS starts LED1 and LED3 should remain solid, and LED2 should start blinking at roughly 4Hz.

The remainig README content is taken directly from the https://github.com/RangeNetworks/dev repository.

Development Environment
=========

A collection of tools to make working with the numerous software components as painless as possible.

If there's a task that annoys you when working with the code, open an issue to suggest an improvement. Or, better, send a pull request to get your automation included in the project.

### &#10143; [Get Started Here](https://github.com/RangeNetworks/dev/wiki)

#### Weather Report

| Component     | master status |
|---------------|:-------------:|
| asterisk | [![Build Status](https://travis-ci.org/RangeNetworks/asterisk.svg?branch=master)](https://travis-ci.org/RangeNetworks/asterisk) |
| asterisk-config | [![Build Status](https://travis-ci.org/RangeNetworks/asterisk-config.svg?branch=master)](https://travis-ci.org/RangeNetworks/asterisk-config) |
| liba53 | [![Build Status](https://travis-ci.org/RangeNetworks/liba53.svg?branch=master)](https://travis-ci.org/RangeNetworks/liba53) |
| libcoredumper | [![Build Status](https://travis-ci.org/RangeNetworks/libcoredumper.svg?branch=master)](https://travis-ci.org/RangeNetworks/libcoredumper) |
| libsqliteodbc | [![Build Status](https://travis-ci.org/RangeNetworks/libsqliteodbc.svg?branch=master)](https://travis-ci.org/RangeNetworks/libsqliteodbc) |
| libzmq | [![Build Status](https://travis-ci.org/RangeNetworks/libzmq.svg?branch=master)](https://travis-ci.org/RangeNetworks/libzmq) |
| openbts | [![Build Status](https://travis-ci.org/RangeNetworks/openbts.svg?branch=master)](https://travis-ci.org/RangeNetworks/openbts) |
| smqueue | [![Build Status](https://travis-ci.org/RangeNetworks/smqueue.svg?branch=master)](https://travis-ci.org/RangeNetworks/smqueue) |
| subscriberRegistry | [![Build Status](https://travis-ci.org/RangeNetworks/subscriberRegistry.svg?branch=master)](https://travis-ci.org/RangeNetworks/subscriberRegistry) |
| system-config | [![Build Status](https://travis-ci.org/RangeNetworks/system-config.svg?branch=master)](https://travis-ci.org/RangeNetworks/system-config) |

#### Misc. Notes

- relink submodule branch tracking

```
$ vi .gitmodules
(change submodule to track different branch X)
$ git submodule update --init --remote
$ cd theSubmoduleDir
$ git checkout X
```
