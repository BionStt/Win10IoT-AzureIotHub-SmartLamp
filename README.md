# Win10IoT-AzureIotHub-SmartLamp
In this project, I put together a proof of concept project that shows how we can create an IoT device based on *Raspberry Pi 2*, 
with *Windows 10 IoT Core* OS. It's basically a smart lamp, that's controllable (switched on/off) remotely and able to send wattage telemetry. 
It's written in *Node.js*, and leverages *Azure IoT Hub* for collecting telemetry data and control the device.

Components:
* Raspberry Pi 2 with Windows 10 IoT Core
* Solid state AC switch circuit (will detail it later)
* AC current sensor ACS712
* ADC Chip MCP3008


##Azure IoT Hub
You need to have Azure IoT Hub account in order to try control device remotely and sending wattage. After you setup an Azure IoT Hub container, you should change `[IOT HUB CONNECTION STRING]` in `server.js` file with appropriate connection string. Refer to Azure IoT Hub documentation on how to get that connection string.


## Bonus
For reading wattage used by the lamp, I need to read the used current. For that I use current sensor (ACS712). 
However, as we know, Raspberry can't read analog data from current sensor. For that, I use ADC chip called MCP3008.
Inside the project, you'll find a class to read analog data from MCP3008 via SPI.
