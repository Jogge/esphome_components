### Installation

## V2 - Genvex
```yaml
packages:
  remote_package:
    url: https://github.com/heinekmadsen/esphome_components
    ref: "1.0.0-stable"
    #ref: "main"
    #ref: "develop"
    files: [components/genvexv2/optima250.yaml]
    #files: [components/genvexv2/optima250_develop.yaml]
    refresh: 0s

uart:
  - id: uart_genvex
    rx_pin: GPIO16
    tx_pin: GPIO17
    parity: EVEN
    baud_rate: 19200
    stop_bits: 1
  
modbus:
    - id: genvex_modbus
      uart_id: uart_genvex
      # Command spacing lives on the hub since ESPHome 2026.8 (was modbus_controller:
      # command_throttle, which is now a no-op). Default is 600ms; lower it if polling
      # the whole register set takes too long.
      #turnaround_time: 100ms
 
modbus_controller:
  id: genvex_modbus_controller
  address: 1
  modbus_id: genvex_modbus
  update_interval: 60s
```
