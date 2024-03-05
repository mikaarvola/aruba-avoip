# aruba-avoip
minimal AV-over-IP configuration for HPE Aruba Networking 2930F Switch Series

Tested with [Crestron DM-NVX-360](https://www.crestron.com/Products/Video/DigitalMedia-Streaming-Solutions/Hardware-Encoders-Decoders/DM-NVX-360) and [Kramer KDS-7](https://www.kramerav.com/feat-products/kds-7/) series.

Minimum network requirements Crestron DM-NVX must be met for a successful installation. Minimum requirements consist of the following:
- **Network switch:**
  - 1-Gigabit port for every connected DM NVX endpoint
  - Nonblocking backplane
  - Layer 3
  - IGMPv2 implementation
- **Network switch settings:** 
  - IGMPv2 snooping enabled
  - IGMPv2 querier enabled
  - Fast-leave enabled (also known as immediate-leave)
- **Inter-switch uplinks (if required):**
  - The uplinks must have sufficient bandwidth for all encoders and decoders connected to the network switch. Allocate 1 Gigabit per encoder or decoder connected to the switch.
  - Uplinks must be configured properly to support multicast traffic.
 
With Kramer KDS, network switch configuration supporting AV over IP says the following:
| FEATURE       					          | SINGLE SWITCH NETWORKING 			    |
| ---------------------------------	| ---------------------------------	|
| Jumbo Frames 						          | frame size to 9216				        |
| IGMP Snooping						          | Enable							              |
| Multicast forwarding or filtering	| Enable							              |
| IP address of IGMP Querier		    | Must be assigned a valid value*	  |
| IGMP Querier						          | Enable[^1]	                      |
| IGMP snooping fast leave			    | Enable[^2]		                    |
| Dynamic multicast router port		  | Disable[^3]		                    |
| Forwarding unknown multicast		  | Disable[^4]          	            |
| Green or energy-saving feature	  | Disable							              |

[^1]: disable for CORE SWITCH and EXTENDED SWITCH
[^2]: N/A for CORE SWITCH and EXTENDED SWITCH
[^3]: disable for CORE SWITCH
[^4]: at CORE SWITCH, router port only indicates that extended Ethernet switches must forward unknown multicast
