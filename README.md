# SPI flasher cape for Beaglebone family

![Cape rendering, top side]
(/pcb_3d_render/beagleflash-top-render.png)
![Cape rendering, bottom side]
(/pcb_3d_render/beagleflash-bottom-render.png)

## Introduction

The SPI flasher cape is a cape for the BeagleBone family of boards which
allows the BeagleBone to interface with a SPI NOR flash chip in order to allow
programming or reading the chip's contents.

### Features

#### Low BOM cost

The total bill-of-materials (COM) cost is under $10 US, including the PCB.

#### Independent voltage regulator

The independent voltage regulator (VR) supplies the power for the operation of
the SPI chip, and is independent of te BeagleBone's internal voltage rails.
This protects the BeagleBone from brown-outs inc case of an external
short-circuits. Since it is a switching regulator, the VR dissipates very
little power when compared to more common linear regulators.

#### SPI buffer IC

The SPI buffer IC protects the internal pins of the BeagleBone from ESD and
short-circuits. The buffer IC is powered from the independent VR, and prevents
excessive currents from being sourced by the BeagleBone's processor in case of
short-circuits.

The buffer IC is driven by the CS signal of the SPI interface, which means that
the outputs are high-impedance when no SPI communication is taking place. As a
result, the SPI chip does not have to be disconnected when the target system is
powered on. Also, since the buffer is enabled by the CS signal, there is no
extra software configuration that needs to be done before enabling the signal
path to the SPI chip, as there is on other solutions (e.g. Gogole servo board).
It's all automatic!

#### Integrated Cape EEPROM

The integrated EEPROM informs the BeagleBone what pins are used by the cape, so
the cape is automatically detected, and the interfaces pins are automatically
configured.

#### Industry-standard headers for 8-pin and 16-pin SPI devices

The external pin headers match the pinout of 8-pin and 16-pin SPI flash parts
so that programming clips (e.g. Pomona SOIC-8) may be directly connected to the
cape.

#### Integrated pull-up resistors for HOLD and WP lines

The integrated pull-up resistors ensure that the HOLD and WP lines of the SPI
chip are driven appropriately. This allows "naked" chips to be programmed. For
mounted SPI chips, the pull-ups prevent short-circuits if another component on
the target system drives these signals low.

## Layout of the repository

### kicad/

This folder contains the KiCad schematic and board files

* beagleflash-cache.lib:
	project-specific chematic symbol library
* beagleflash.kicad_pcb:
	KiCad (pcbnew) PCB design file
* beagleflash.net:
	Netlist file with footprint associactions
* beagleflash.pro:
	KiCad project file
* beagleflash.sch:
	KiCad (eeschema) schematic

### gerbers/

* beagleflash-B.Cu.gbl:
	Bottom copper layer
* beagleflash-B.Mask.gbs:
	Bottom soldermask layer
* beagleflash-B.SilkS.gbo:
	Bottom silkscreen layer
* beagleflash-Edge.Cuts.gm1:
	Board outline
* beagleflash-F.Cu.gtl:
	Top copper layer
* beagleflash-F.Mask.gts:
	Top soldermask layer
* beagleflash-F.SilkS.gto:
	Top silkscreen layer
* beagleflash.txt:
	Drill file

### pcb_3d_render/

3D renderings of the PCB.
