# Ohmpilot communication

Extracts from Modbus communication between a Fronius GEN25 inverter and a Fronius Ohmpilot water storage heater controller.
The output of the Ohmpilot is controlled to make maximum use of excess power from the solar array to heat up water.

The Ohmpilot uses address 40 (28 in Hexadecimal on Modbus 0 of the GEN24 inverter. Using the Ohmpilot the user gets full information of
the power delivered to the storage tank and the temperature of the water as a function of time using Fronius Solarweb portal.

The Modbus_logfiles directory holds two sessions one of which is a full startup of the Ohmpilot when the GEN24 is running. Here I have added some comments in the logfile. Both files are plain textfiles, show can be browsed easily. The second file logs a period in which the Ohmpilot is at work by heating the water to 55 degC (set Max. temperature). And it can be seen that power and temperature are varying.

Brief Register list:
(Note: listed are the decimal base holding register address + 1. So for register 40800 one will find x9F5F in the log files):
40004   Holding registers with Ohmpilot information (Manufacturer, DeviceName, Serialno. etc)
40452   Holding registers with string data (FRO:xxxxxxxx) - xxxxxxxx is pairing number
40600   Holding registers that GEN24 writes to (4 bytes), to control power to water
40800   Holding registers read by GEN24 with data (power to water heater, water temperature, etc)
41200

