<!---

This file is used to generate your project datasheet. Please fill in the information below and delete any unused
sections.

You can also include images in this folder and reference them in the markdown. Each image must be less than
512 kb in size, and the combined size of all images must be less than 1 MB.
-->

## How it works

When the system boots up, it will start accessing the SPI bus to set up a connected SPI Flash memory in XIP mode and start executing instructions from there. The GPIO can be used to output data, e.g. as a bitbanged UART


## How to test

The testbench contains a model of an SPI Flash. A program in Verilog Hex format can be preloaded into the Flash model.

Underserved can easiest be run locally using FuseSoC.

```Install FuseSoC

pip install fusesoc
```
```Create and enter a new workspace

mkdir workspace && cd workspace
```
```Register underserved as a library in the workspace

fusesoc library add underserved /path/to/prince
```
...if repo is available locally or... ...to get the upstream repo
```
fusesoc library add underserved https://github.com/olofk/underserved
```
```Show available cores in workspace (probally just underserved for now if you haven't added other libraries)

fusesoc core list
```
```Show info about underserved


fusesoc core show underserved
```
```Run linting (static code checks) using Verilator

fusesoc run --target=lint underserved
```
```Run underserved testbench

fusesoc run --target=sim underserved
```
```Run with modelsim instead of default tool (icarus)

fusesoc run --target=sim underserved --tool=modelsim
```
## External hardware

Expects a compatible SPI Flash. The XIP controller was stolen from PicoSoC which also contains some info about compatible SPI Flash components.
