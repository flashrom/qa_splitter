# Introduction

<To be written>

# Repository contents

 * `docs/`  
   Documentation including specifications, theses etc.
 * `hw/`  
   Hardware CAD files, e.g. schematic, gerber files etc.
 * `sw/`  
   All kinds of software related to the project including test scripts, USB clients etc.

# Requirements

 * The device must be able to easily connect at least 5 of programmers to various SPI flash chips as specified below.
 * The flash chips shall be placed in sockets or be easily replaceable by other means (e.g., adapter boards with a standardized connector to the device).
   The physical interface hereinafter will simply be denoted socket.
 * Every flash chip's VCC must be decoupled by a suitable capacitor close to the socket with a capacitor of at approximately 0.1 uF (up to 1 uF).
 * It must be possible to route any of the programmers to any of the flash chips at runtime via a USB interface.
 * The upper bound on concurrent programmer <-> flash connections might be 1 (i.e. it is not necessary although advantageous to support multiple concurrent connections).
 * The connectors for the programmers shall be 2x4 2.54 mm pin headers and match the pin layout of JEDEC 25 family flash chips so that programmers also using this layout via pin headers or ZIF sockets can be connected via 8-wire ribbon cables.
 * At least one programmer connector must match the Dediprog SF100 layout with 2x7 2.54 mm pins.
 * **JEDEC 25 flash chips**
   * The device must support (at least) three flash chips of the JEDEC 25 family without any hardware/manual reconfiguration.
     It might support this change by receiving commands via USB.
   * All respective sockets must support the 8-pin and 16-pin versions of these flash chips.
   * At least two sockets must support multi-I/O modes (e.g., dual output, quad SPI).
   * At least one socket must support multi-I/O modes requiring four pins (e.g. quad SPI).
 * The device must support (at least) one flash chip of the AT45 family (e.g. AT45DB041D).
 * The device must support using the I/O voltages supplied by the attached programmers.
   This might be implemented by simply routing any I/O signals directly from the programmer to the flash chip or by sensing the I/O voltage and refraining from applying any voltage conversion.
 * The device should support converting between the I/O voltage of all attached programmers to 3.3 V I/O voltages on the flash chips.
 * The device should support converting between the I/O voltage of all attached programmers to 1.8 V I/O voltages on the flash chips.
 * The device must support a maximum frequency of the data signals between the programmers and the flash chip of at least 5 MHz.
 * The supply voltage of the flash chips has to match the respective configured I/O voltage.
   The Vcc pin of the respective programmer might be used to supply the connected flash chip if its voltage level matches.
 * For every routed connection the state of the write protection pin (/WP, if available) shall be configurable via USB to be pulled low, high, or be directly connected from the programmer to the flash chip.
 * Every flash chip must be resettable via USB.
 * Logic input pins of the flash chips not mentioned elsewhere in these requirements have to be pulled up by the device.
 * The device shall be powered via a single standardized USB connector.
   The same connector should be used to transport control commands to the device.
 * The device must have suitable mounting holes to fixate it within an enclosure.
