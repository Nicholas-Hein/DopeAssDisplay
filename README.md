# DopeAssDisplay

A size-adaptable RGB-LED array for displaying images and animations.

## Segment Managers

Segment managers are the base layer of the display structure.  They directly
interface with the RGB-LEDs via a series of shift registers.  They have constant
dimensions, but they can be placed parallel to eachother to expand the overall
display dimensions.  They are controlled via the TWI protocol (each having
a unique address) by the imaging manager.


## Imaging Manager

The Imaging Manager is the volatile image data layer of the display structure.
It directly interfaces with the Segment Managers via TWI to produce specific
patterns.  It is controlled via USART by the Display Controller, and is
indirectly interfaced with other high-speed, high-capacity storage devices.
It unloads and controls the rendering of all media from the storage devices by
controlling the Segment Managers individually.


## Display Controller

The Display Controller is the application layer of the display structure.  It
is indirectly interfaced with the high-speed, high-capacity storage devices and
directly interfaced with the Imaging Manager.  The Display Controller is
responsible for loading all media to the storage devices, and it controls the
way that data is interpreted by the imaging manager via the USART interface
with the Imaging Manager.  It also directly controls the Communications Manager
via the SPI protocol in order to get information from the master computer.


## Communications Manager

The Communications Manager is the module responsible for direct communication
with the master computer.  It loads command data to the display controller and
relays status data back to the master computer.
