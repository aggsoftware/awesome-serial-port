# Awesome Serial Port and MODBUS

A curated list of tools, libraries, drivers, specifications and reference pages for RS-232, RS-485, USB-serial and MODBUS work. Maintained by [AGG Software](https://www.aggsoft.com/); our own tools are marked with (AGG). Everything else is listed because we use it or our customers do. Pull requests welcome; one line per entry, no marketing text.

## Contents

- [Terminals](#terminals)
- [Browser-based tools](#browser-based-tools)
- [Libraries](#libraries)
- [Virtual ports and serial over network](#virtual-ports-and-serial-over-network)
- [Sniffing and analysis](#sniffing-and-analysis)
- [Data logging](#data-logging)
- [USB-to-serial chips and drivers](#usb-to-serial-chips-and-drivers)
- [MODBUS](#modbus)
- [NMEA and GPS](#nmea-and-gps)
- [Specifications and reference](#specifications-and-reference)
- [Programming guides](#programming-guides)

## Terminals

Windows

- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/) - SSH and telnet client with a serial mode and session logging.
- [Tera Term](https://teratermproject.github.io/) - Terminal emulator with a macro language, serial and TCP.
- [RealTerm](https://realterm.sourceforge.io/) - Terminal for binary data, hex display, capture to file, port sniffing with two ports.
- [CoolTerm](https://freeware.the-meiers.org/) - Simple serial terminal for Windows, macOS and Linux, hex view, logging.
- [Termite](https://www.compuphase.com/software_termite.htm) - Small RS-232 terminal with a message-oriented view.
- [Hercules SETUP utility](https://www.hw-group.com/software/hercules-setup-utility) - Serial, TCP client/server and UDP terminal in one window.
- [YAT](https://sourceforge.net/projects/y-a-terminal/) - Terminal with predefined commands, binary and text modes, scripting.
- [Docklight](https://docklight.de/) - Terminal with send sequences, receive sequences and a protocol test mode (commercial).
- [SerialTool](https://www.serialtool.com/) - Terminal with CAN, MODBUS and sniffer functions (commercial, free edition).
- [Advanced Serial Port Monitor](https://www.aggsoft.com/serial-port-monitor.htm) (AGG) - Terminal, port sniffer and MODBUS tester for Windows (commercial, trial).

Linux and macOS

- [minicom](https://salsa.debian.org/minicom-team/minicom) - The classic text-mode serial terminal.
- [picocom](https://github.com/npat-efault/picocom) - Minimal terminal, no configuration files.
- [tio](https://github.com/tio/tio) - Serial device I/O tool with sensible defaults, hex mode and logging.
- [GNU screen](https://www.gnu.org/software/screen/) - `screen /dev/ttyUSB0 115200` is often all you need.
- [CuteCom](https://gitlab.com/cutecom/cutecom) - Graphical terminal for Linux and macOS.
- [moserial](https://wiki.gnome.org/Apps/Moserial) - GNOME serial terminal.
- [Serial](https://www.decisivetactics.com/products/serial/) - macOS terminal with built-in drivers for most USB-serial adapters (commercial).

## Browser-based tools

- [Web Serial API](https://wicg.github.io/serial/) - The specification. Chromium browsers only, needs HTTPS and a user gesture.
- [Web Serial API on MDN](https://developer.mozilla.org/en-US/docs/Web/API/Web_Serial_API) - Reference and examples.
- [Serial Terminal](https://googlechromelabs.github.io/serial-terminal/) - Google's Web Serial demo terminal.
- [ESP Web Tools](https://esphome.github.io/esp-web-tools/) - Flash ESP32/ESP8266 from the browser over Web Serial.
- [Serial Port Tester](https://www.aggsoft.com/serial-port-tester.htm) (AGG) - Open, loopback and listen tests from the browser.
- [MODBUS Tester](https://www.aggsoft.com/modbus-tester.htm) (AGG) - Send MODBUS RTU/ASCII requests from the browser and decode the reply.

## Libraries

- [pySerial](https://github.com/pyserial/pyserial) - Python, the de-facto standard, with RFC 2217 and `serial.tools.list_ports`.
- [node-serialport](https://github.com/serialport/node-serialport) - Node.js bindings, parsers and a CLI.
- [libserialport](https://sigrok.org/wiki/Libserialport) - Minimal cross-platform C library from the sigrok project.
- [serialport-rs](https://github.com/serialport/serialport-rs) - Rust, cross-platform.
- [wjwwood/serial](https://github.com/wjwwood/serial) - C++ cross-platform library.
- [jSerialComm](https://github.com/Fazecast/jSerialComm) - Java, no native installation needed.
- [go-serial](https://github.com/bugst/go-serial) - Go, cross-platform, used by the Arduino tooling.
- [System.IO.Ports.SerialPort](https://learn.microsoft.com/dotnet/api/system.io.ports.serialport) - .NET.
- [QSerialPort](https://doc.qt.io/qt-6/qserialport.html) - Qt.
- [termios(3)](https://man7.org/linux/man-pages/man3/termios.3.html) - The POSIX terminal interface every Unix library sits on.
- [Communications Resources (Win32)](https://learn.microsoft.com/windows/win32/devio/communications-resources) - `CreateFile`, `SetCommState`, `WaitCommEvent` and friends.

## Virtual ports and serial over network

- [com0com](https://com0com.sourceforge.net/) - Virtual null-modem driver for Windows, with hub4com for sharing and routing.
- [tty0tty](https://github.com/freemed/tty0tty) - Null-modem emulator for Linux.
- [socat](http://www.dest-unreach.org/socat/) - Relay between a serial port, a PTY, TCP and more; `socat PTY,link=/dev/ttyV0 TCP:host:port`.
- [ser2net](https://github.com/cminyard/ser2net) - Serial-to-network proxy daemon with RFC 2217 support.
- [RFC 2217](https://www.rfc-editor.org/rfc/rfc2217) - Telnet COM port control option, the standard for serial over TCP.
- [esp-link](https://github.com/jeelabs/esp-link) - ESP8266 as a Wi-Fi serial bridge.
- [HW VSP3](https://www.hw-group.com/software/hw-vsp3-virtual-serial-port) - Free virtual serial port for HW group devices.
- [Virtual Serial Port Driver](https://www.virtual-serial-port.org/) - Virtual COM port pairs for Windows (commercial).
- [TCP COM Bridge](https://www.aggsoft.com/tcp-com/) (AGG) - COM port to TCP/UDP redirector for Windows, server and client modes (commercial, trial).
- [Virtual Null Modem](https://www.virtual-null-modem.com/) (AGG) - Virtual COM port pairs for Windows (commercial, trial).

## Sniffing and analysis

- [Wireshark](https://www.wireshark.org/) - With [USBPcap](https://desowin.org/usbpcap/) on Windows it captures USB-serial traffic; dissectors exist for MODBUS/TCP and many serial protocols over TCP.
- [sigrok and PulseView](https://sigrok.org/wiki/PulseView) - Logic analyzer software with UART, SPI, I2C and MODBUS decoders.
- [Saleae Logic](https://www.saleae.com/) - Logic analyzers with a UART analyzer (commercial hardware, free software).
- [Portmon](https://learn.microsoft.com/sysinternals/downloads/portmon) - Sysinternals serial and parallel port monitor. Legacy, 32-bit kernels only.
- [Free Serial Analyzer](https://freeserialanalyzer.com/) - Windows serial port sniffer (free edition with limits).
- [Serial Port Monitor](https://www.serial-port-monitor.org/) - Windows serial port sniffer (commercial).
- [Advanced Serial Port Monitor](https://www.aggsoft.com/serial-port-monitor.htm) (AGG) - Sniffer mode logs traffic of a port opened by another program.

## Data logging

- [Advanced Serial Data Logger](https://www.aggsoft.com/serial-data-logger.htm) (AGG) - Logs RS-232/RS-485 data to files, Excel and databases with parsers for scales, meters, analysers and more (commercial, trial).
- [Advanced TCP/IP Data Logger](https://www.aggsoft.com/tcpip-data-logger.htm) (AGG) - The same for TCP and UDP sources.
- [WinWedge](https://www.taltech.com/winwedge) - Keyboard-wedge software for serial devices (commercial).
- [node-red-node-serialport](https://flows.nodered.org/node/node-red-node-serialport) - Serial nodes for Node-RED.
- PuTTY, Tera Term, tio and picocom above all log a session to a file.

## USB-to-serial chips and drivers

- [FTDI drivers](https://ftdichip.com/drivers/) - VCP and D2XX for FT232 family chips.
- [Silicon Labs CP210x drivers](https://www.silabs.com/developer-tools/usb-to-uart-bridge-vcp-drivers) - CP2102, CP2104 and others.
- [Prolific](https://www.prolific.com.tw/) - PL2303 drivers; many clone chips stop working with new drivers.
- [WCH](https://www.wch-ic.com/) - CH340, CH341, CH343 drivers.
- [USB CDC class definitions](https://www.usb.org/document-library/class-definitions-communication-devices-12) - The standard behind "USB serial" devices that need no vendor driver.
- [USB pinouts and wire colors](https://www.aggsoft.com/usb-pinout-cable/usb2.htm) (AGG) - USB 2, USB 3 and USB-C connector reference.

## MODBUS

Specifications

- [MODBUS specifications](https://modbus.org/specs.php) - Application protocol, serial line and TCP specifications from the Modbus Organization.
- [Wireshark Modbus/TCP display filter reference](https://www.wireshark.org/docs/dfref/m/mbtcp.html) - Fields of the built-in Modbus/TCP dissector.

Libraries

- [libmodbus](https://libmodbus.org/) - C, RTU and TCP, the reference for many bindings.
- [pymodbus](https://github.com/pymodbus-dev/pymodbus) - Python client and server, sync and async.
- [MinimalModbus](https://github.com/pyhys/minimalmodbus) - Python RTU/ASCII master, small and readable.
- [modbus-tk](https://github.com/ljean/modbus-tk) - Python master and slave, RTU and TCP.
- [uModbus](https://github.com/AdvancedClimateSystems/uModbus) - Python, pure, RTU and TCP.
- [node-modbus-serial](https://github.com/yaacov/node-modbus-serial) - Node.js RTU and TCP master.
- [jsmodbus](https://github.com/Cloud-Automation/node-modbus) - Node.js client and server.
- [NModbus](https://github.com/NModbus/NModbus) - .NET.
- [EasyModbusTCP](https://github.com/rossmann-engineering/EasyModbusTCP.NET) - .NET client, simple API.
- [j2mod](https://github.com/steveohara/j2mod) - Java, fork of jamod.
- [tokio-modbus](https://github.com/slowtec/tokio-modbus) - Rust, async.
- [goburrow/modbus](https://github.com/goburrow/modbus) - Go client.
- [FreeMODBUS](https://github.com/cwalter-at/freemodbus) - Embedded slave stack in C.
- [nanoMODBUS](https://github.com/debevv/nanoMODBUS) - Tiny C library for microcontrollers, client and server.

Masters, simulators and testers

- [Modbus Poll and Modbus Slave](https://www.modbustools.com/) - Windows master and slave simulators (commercial, trial).
- [mbpoll](https://github.com/epsilonrt/mbpoll) - Command-line master for Linux, macOS and Windows.
- [modpoll and diagslave](https://www.modbusdriver.com/) - Command-line master and slave simulator (free for non-commercial use).
- [QModMaster](https://sourceforge.net/projects/qmodmaster/) - Qt-based master with a bus monitor.
- [ModbusPal](https://modbuspal.sourceforge.net/) - Java slave simulator with scripted register values.
- [pyModSlave](https://sourceforge.net/projects/pymodslave/) - Python slave simulator with a GUI.
- [Radzio! Modbus Master Simulator](https://en.radzio.dxp.pl/modbus-master-simulator/) - Free Windows master.
- [ModRSsim2](https://sourceforge.net/projects/modrssim2/) - Windows slave simulator for RTU and TCP.
- [CAS Modbus Scanner](https://store.chipkin.com/products/tools/cas-modbus-scanner) - Free Windows register scanner.
- [Simply Modbus](https://www.simplymodbus.ca/) - Tutorials on the frame formats, plus master and slave tools.
- [MODBUS CRC calculator](https://www.aggsoft.com/modbus-crc-calculator.htm) (AGG) - CRC-16 and LRC for RTU and ASCII frames in the browser.
- [MODBUS Tester](https://www.aggsoft.com/modbus-tester.htm) (AGG) - Browser RTU/ASCII tester over Web Serial, with type detection for the reply.
- [MODBUS register maps](https://www.aggsoft.com/modbus-data-logging/) (AGG) - Register maps and logging notes for meters, inverters, PLCs and sensors.

## NMEA and GPS

- [NMEA revealed](https://gpsd.gitlab.io/gpsd/NMEA.html) - The best free description of NMEA 0183 sentences, from the gpsd project.
- [gpsd](https://gpsd.gitlab.io/gpsd/) - GPS service daemon for Unix.
- [pynmea2](https://github.com/Knio/pynmea2) - Python NMEA 0183 parser.
- [TinyGPS++](https://github.com/mikalhart/TinyGPSPlus) - Arduino NMEA parser.
- [NMEA decoder](https://www.aggsoft.com/nmea-decoder.htm) (AGG) - Paste a sentence, see the fields.
- [AIS decoder](https://www.aggsoft.com/ais-decoder.htm) (AGG) - Decode AIVDM/AIVDO messages in the browser.

## Specifications and reference

- [RS-232 (Wikipedia)](https://en.wikipedia.org/wiki/RS-232) - Signals, voltage levels, connector history.
- [RS-485 (Wikipedia)](https://en.wikipedia.org/wiki/RS-485) - Differential signalling, termination, topology.
- [The RS-485 Design Guide (TI)](https://www.ti.com/lit/pdf/slla272) - Application note on cabling, termination and biasing.
- [RS232 specifications and standard (Lammert Bies)](https://www.lammertbies.nl/comm/info/rs-232-specs) - Compact reference with the signal table.
- [Serial Port Central (Jan Axelson)](https://www.lvr.com/serport.htm) - Companion site to "Serial Port Complete".
- [RS232 pinouts and cables](https://www.aggsoft.com/rs232-pinout-cable/) (AGG) - DB9, DB25, RJ45 pinouts, null-modem and loopback wiring with diagrams.
- [pinouts.ru](https://pinouts.ru/) - Connector pinouts for thousands of devices.

## Programming guides

- [Serial Programming Guide for POSIX Operating Systems](https://www.cmrr.umn.edu/~strupp/serial.html) - Michael Sweet's classic.
- [Serial HOWTO](https://tldp.org/HOWTO/Serial-HOWTO.html) - Linux Documentation Project.
- [Arduino Serial reference](https://www.arduino.cc/reference/en/language/functions/communication/serial/) - `Serial.begin`, `Serial.read` and the rest.

## Contributing

One entry per line, in the form `[Name](url) - one sentence.` Mark commercial tools. No link shorteners, no affiliate links. Our own tools are listed with (AGG); we do not list our tools above others in a section.

## License

[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)
