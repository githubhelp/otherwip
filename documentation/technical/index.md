## Under the hood: listeners and buffers

Listerners and buffers are classes that are instanciated by the gateway.

Listeners manage data inputs and forward data to buffers. Buffers send data to processing/display applications.

The gateway links one or more listeners to one or more buffers.

### Listeners

Listeners derive the OemGatewayListener class:

    OemGatewayListener
      |
      |-- OemGatewaySerialListener
      |     |
      |     |-- OemGatewayRFM2PiListener
      |           |
      |           |-- OemGatewayRFM2PiListenerRepeater
      |
      |-- OemGatewaySocketListener

#### OemGatewaySerialListener 

Receives data on the serial port.

##### Init settings

* com_port: path to the COM port (e.g. /dev/ttyAMA0)

##### Runtime settings

None

#### OemGatewayRFM2PiListener 

Receives data on the serial port through the RFM2Pi module.

##### Init settings

* com_port: path to the COM port (e.g. /dev/ttyAMA0)

##### Runtime settings

RFM settings:
* sgroup
* frequency
* baseid

* sendtimeinterval: if not 0, period in seconds. The gateway will send time 
on the radio link with this period, for other devices, typically emonGLCD.

#### OemGatewayRFM2PiListenerRepeater

Receives data on the serial port through the RFM2Pi module, and transmits 
messages received throught a socket on the RF link.

Note that neither acknowledgement nor authentication is implemented.

##### Init settings

* com_port: path to the COM port (e.g. /dev/ttyAMA0)
* port_nb: port number

##### Runtime settings

Same as OemGatewayRFM2PiListener

#### OemGatewaySocketListener

Receives data through a socket. From another machine on the network or from 
another application on the same host.

Note that neither acknowledgement nor authentication is implemented.

##### Init settings

* port_nb: port number

##### Runtime settings

None

### Buffers

Buffers derive the OemGatewayBuffer class.

    OemGatewayBuffer
      |
      |-- OemGatewayEmoncmsBuffer

#### OemGatewayEmoncmsBuffer

Send data to an emoncms server. If connection is lost, the data is buffered
until the network is up again.

##### Init settings

None

##### Runtime settings

* protocol: http:// or https://
* domain (e.g. emoncms.org)
* path (e.g. /emoncms)
* apikey
* active: if False, neither record nor send data, but hold unsent data.
