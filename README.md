# Arias Research Group - Battery Testing Board

### Seiya Ono Sp'19

## Overview

The board was designed such that the Photon could both drive and discharge the battery cell attached. The battery load resistor was chosen to be 0805 SMD so it could potentially be upgraded to handle higher discharges. Other than that, there are redundant connectors coming off so the user can access needed pins in different ways. The board also features two exposed test pads to probe the resistance of the load resistor precisely, given the user measures it before soldering on the Photon.

The pins below the Photon as well as the battery connection pins are meant for test points. The slide switch can disconnect the battery from the circuit as to not discharge when unnecessary. There are 5 indicator LEDs on the side that can be programmed by the user.

The BOM can be found as `bom.csv` and includes the parts used to populate the board.

### Resistor Selection

The [10 Ohm Resistor](https://www.digikey.com/product-detail/en/stackpole-electronics-inc/RNCF0805AKT10R0/RNCF0805AKT10R0CT-ND/4250701) was chosen by searching through Digikey with [these filters](https://www.digikey.com/products/en/resistors/chip-resistor-surface-mount/52?k=&pkeyword=&sv=0&pv7=2&pv1989=0&pv3=651&pv3=667&pv3=696&pv16=39329&pv1127=i2&sf=1&FV=-8%7C52&quantity=&ColumnSort=0&page=1&stock=1&nstock=1&photo=1&pageSize=50) enabled.

If that link somehow is broken, the filters are as follows:

`Product Index > Resistors > Chip Resistor > Surface Mount`

Part Status: Active

Package / Case: 0805

Packaging: Cut Tape

Tolerance: 0.01%, 0.02%, 0.05%

Number of Terminations: 2

In stock: Checked

Normally Stocking: Checked

Photo: Checked

## Tips

When soldering, start with the smallest components, as they are the hardest to solder. Then move to the test points and slide switch, then the Photon. When soldering the Photon, make sure it is aligned well so that all the pads have enough room to contact the castelated board.

## Specifications

From Dr. Evans:

Idea is to carry out multi-cycle testing of a Panasonic coin cell (about 3 million cycles). With the present arrangement (a Photon mounted on a breadboard) we have reached ~ 2 million cycles and still going. The design connects the DAC output of the Photon (nominally 0 – 3.3V DC) to the positive terminal of the cell holder via a 10 Ohm resistor. The negative terminal of the cell holder is connected to GND on the Photon. Wires run from either side of the resistor to the analog input connections on the Photon so that the current can be determined from the voltage drop across the resistor (A3 to A5) and the cell voltage determined by one of the connections (A3). We have software that brings the DAC output to greater than the cell voltage during charge and lowers it to below cell voltage during discharge. A cycle takes approximately 400 ms and the data are relayed via Webhook to ThingSpeak (Math Works’ version of the cloud) for plotting/analysis.

![spec](img/spec.png)

### Task

1. Build present design but with soldered connections. Two Photons without header pins should be here by next week. We have cell holders and cells.
1. Set up the Photons and load code (I will supply).
1. Run a couple of cells to 3 million cycles or failure, collecting data.
1. See what we can do next.

Useful Links:

[Photon](https://store.particle.io/products/photon)

## Possibilities

* External power - through maybe a barrel jack to provide external power to the entire board, so that the photon's uUSB isn't stressed
* Push buttons for Photon configuration - allows external user to set up and start different testing procedures
* Accurate ammeter for measuring current.
* Instead of having a soldered on resistor, can use [SIP Sockets](https://www.digikey.com/product-detail/en/mill-max-manufacturing-corp/346-43-102-41-013000/ED6464-02-ND/1212288) to make impermanent connections with precision through hole resistors. This way, they can be swapped in and out for future proofing.
