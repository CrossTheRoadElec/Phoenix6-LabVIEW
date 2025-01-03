# Phoenix 6 for LabVIEW Beta

This is the repository that contains the beta VIs for Phoenix 6 in LabVIEW.

## Installation
To install the required VIs onto your development computer, perform the following steps:
 1. Download this repository (either by cloning or downloading as a zip via the green Code button in the upper right).
 2. Move this repository to the LabVIEW "ThirdParty/Phoenix6" folder (typically at `C:\Program Files (x86)\National Instruments\LabVIEW 2023\vi.lib\Rock Robotics\WPI\ThirdParty\Phoenix6`)
 3. Move the `dir.mnu` file from "Menu Files/Top Level" into LabVIEW's "ThirdParty/TopLevel/Phoenix6" folder (Typically at `C:\Program Files (x86)\National Instruments\LabVIEW 2023\vi.lib\Rock Robotics\WPI\ThirdParty\TopLevel\Phoenix6`)
 4. Restart LabVIEW and there should now be a Phoenix6 palette under WPILib->Thirdparty with all the VIs for use.

### Phoenix Install on roboRIO
In addition to locally installing the VIs onto your development computer, you will also need to install the Phoenix Libraries to the roboRIO.
This can be accomplished by following the steps in our [Installing Phoenix 6 (FRC) documentation](https://v6.docs.ctr-electronics.com/en/stable/docs/installation/installation-frc.html).

## Usage
This library is primarily accessed by a few common VIs across all devices.

### Device Open
This VI is named "device"_open.vi. It contains 2 input parameters, a device ID and a CAN bus, and outputs a cluster.
The Device ID must match the CAN ID that was set in Tuner, and the CAN bus must match the CANivore name, or rio/blank if on the RIO bus.
The cluster output is a device reference to be used in the subsequent VIs.

### Device Getters
This VI is named "device"Getters.vi.
It is a polymorphic VI that allows the user to select which signal to get.
It accepts the device reference and outputs a cluster that contains value, units, and timestamp.

### Device Setters
This VI is named "device"Setters.vi.
Currently only TalonFX supports this VI.
It is a polymorphic VI that allows the user to select which control parameters to set with.
It accepts a device reference and all the variables that pertain to the control mode selected.

### Phoenix6_Device_RefNumRegistryGet.vi and Phoenix6_Device_RefNumRegistrySet.vi
These VIs are the refnum gets and sets so users can open their devices in begin and use them in other locations.

## Limitations
Phoenix 6 for LabVIEW is currently in beta, and as such has some limitations.
 - Configs: Configs are currently not supported. Users will have to use Tuner to set and get configs for the time being.
 - Waiting on Signals: The Java/C++ API for WaitForAll and WaitForUpdate is not implemented in LabVIEW. Currently the signal getters are equivalent to the refresh API.
 - Set Update Frequency: Currently the signals cannot change update frequency, so signals will update at their default frequency.
 
