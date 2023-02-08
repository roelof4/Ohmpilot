# Fronius Ohmpilot communication

Extracts from Modbus communication between a Fronius GEN24 inverter and a Fronius Ohmpilot water storage heater controller.
The output of the Ohmpilot is controlled to make maximum use of excess power from the solar array to heat up water. Almost impossible to buy these days but with access to the communications it is possible to create a similar device.

The Ohmpilot uses decimal address 40 (28 in Hexadecimal on Modbus 0 of the GEN24 inverter). Through this communication the GEN24 has full information of
the power delivered to the storage tank and the temperature of the water as a function of time and this data is visible on the Fronius Solarweb portal.  

Interestingly the Ohmpilot works also in the Export Limit mode of the GEN24 (for those who get nothing supplying to the grid). It does so by varying the power whilst observing feedback from the GEN24 data which stems from the power meter that is hooked up to the other Modbus port of the GEN24.

The Modbus_logfiles directory holds two sessions one of which is a full startup of the Ohmpilot when the GEN24 is running. Here I have added some comments in the logfile. Both files are plain textfiles, and can thus be browsed easily. Note that occasionally a x00 byte appears after a valid CRC double byte.  
The second file logs a period in which the Ohmpilot is at work by heating the water to 55 degC (set Max. temperature). And it can be seen that power and temperature are varying.

Brief Register list:
(Note: listed are the decimal base holding register address + 1. So for register 40800 one will find as x9F x5F in the log files):

40004   Holding registers with Ohmpilot information (Manufacturer, DeviceName, Serialno. etc)  
40452   Holding registers with string data (FRO:xxxxxxxx) - xxxxxxxx is pairing number  
40600   Holding registers that GEN24 writes to (4 bytes), to control power to water  
40800   Holding registers read by GEN24 with data (power to water heater, water temperature, etc)  
41200  


