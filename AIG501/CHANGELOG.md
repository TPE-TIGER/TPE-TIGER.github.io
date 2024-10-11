# API version release notes
## V1.4.0 (2024-10)
The functionality and changes below were added in AIG-501 V1.4.0

### New Features
- Support Modbus Slave
- Support Backup Logging for Modbus Slave

## V1.3.0 (2023-12)
The functionality and changes below were added in AIG-501 V1.3.0

### New
#### Digital IO (Device)
- Added support for retrieving AIG Digital IO interface settings and value.
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Device | IO | `GET /device/io/di` | Get information of all managed DIs |
    | Device | IO | `GET /device/io/do` | Get information of all managed DOs |
- Added support for updating AIG Digital IO interface settings and value.
    |  Category  |  Function | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Device | IO | `PATCH /device/io/di/{channel}` | Patch to set DI by channel |
    | Device | IO | `PATCH /device/io/do/{channel}` | Patch to set DO by channel |
#### OpenVPN (Cloud)
- Added support for retrieving AIG OpenVPN Client settings and value.
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | CLOUD | OpenVPN | `GET /openvpn` | Get OpenVPN client setting |
    | CLOUD | OpenVPN | `GET /openvpn/profile` | Export current OpenVPN client profile file (get smaple config by qurey string) |
    | CLOUD | OpenVPN | `GET /openvpn/log` | Export an OpenVPN client logs file |
- Added support for updating AIG OpenVPN Client settings and value.
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | CLOUD | OpenVPN | `PUT /openvpn` | Enable/Disable OpenVPN client with current profile file |
    | CLOUD | OpenVPN | `PATCH /openvpn/profile` | Import an OpenVPN client profile file |
    | CLOUD | OpenVPN | `DELETE /openvpn/profile` | Delete current OpenVPN client profile file |

### Changed
- Some fields for message group have changed in the following endpoints. 
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Cloud | MQTT/AWS/Azure | `GET /{cloud}/{id}/messages` | (*New Schema) |
    | Cloud | MQTT/AWS/Azure | `POST /{cloud}/{id}/messages` | (*New Schema) |
    | Cloud | MQTT/AWS/Azure | `GET /{cloud}/{id}/messages/{group_id}` | (*New Schema) |
    | Cloud | MQTT/AWS/Azure | `PUT /{cloud}/{id}/messages/{group_id}` | (*New Schema) |
    | Cloud | MQTT/AWS/Azure | `DELETE /{cloud}/{id}/messages/{group_id}` | (*New Schema) |

    **New Schema**
    | Name |Description| 
    | ---|---|
    |description| Message group description |
    |samplingMode| `[ all values, all latest values, all changed alues, latest changed values ]` |
    |onChange| Send message if value changed |
    |sendOutThreshold.mode| `[ by size, by time, immediately ]` |
    |sendOutThreshold.sizeIdleTimer.enable|Enable send message as reaching the idle time for by size mode  |
    |sendOutThreshold.sizeIdleTimer.time|The idle time for by size mode|
    |minPublishInterval| The least delay time between the publishing for immediately mode|
    |customSamplingRate| Enable polling interval |
    |sendOutFormat| Advance format jq filter|
    

- Added support for cellular to select the cellular network .
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Device | Cellular | `GET /device/cellulars` |  `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `PATCH /device/cellulars` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `GET /device/cellulars/{id}` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `PATCH /device/cellulars/{id}` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |

- Added support for  to select the cellular network .
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | Device | Cellular | `GET /device/cellulars` |  `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `PATCH /device/cellulars` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `GET /device/cellulars/{id}` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |
    | Device | Cellular | `PATCH /device/cellulars/{id}` | `preferedNetwork`: selected cellular network type.<br />`[ auto, 4g, 3g ]` |

- ssh support for setting whitelist .
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | System | Sshserver | `GET /system/sshserver` | (*New Schema) |
    | System | Sshserver | `PATCH /system/sshserver` | (*New Schema) | 
    | System | Sshserver | `PUT /system/sshserver` | (*New Schema) |
    | System | Sshserver | `GET /system/sshserver/sshwhitelist` | (*New Schema) | 
    | System | Sshserver | `POST /system/sshserver/sshwhitelist` | (*New Schema) |    
    | System | Sshserver | `DELETE /system/sshserver/sshwhitelist/{id}` | (*New Schema) |  

    **New Schema**
    | Name |Description| 
    | ---|---|
    |sshWhiteList| WhiteList of SSh server |
    **sshWhiteList**
    | Name |Description| 
    | ---|---|
    |id| id of WhiteList |
    |ipRange| ipRange of WhiteList |
    |firewallId| firewallId of iptables |

- http support for setting whitelist .
    |  Category  |  Name | Endpoints | Changes |
    |  ----  |  ----  | --- | ---- |
    | System | httpserver | `GET /system/httpserver` | (*New Schema) |
    | System | httpserver | `PATCH /system/httpserver` | (*New Schema) | 
    | System | httpserver | `PUT /system/httpserver` | (*New Schema) |
    | System | httpserver | `GET /system/httpserver/httpwhitelist` | (*New Schema) | 
    | System | httpserver | `POST /system/httpserver/httpwhitelist` | (*New Schema) |    
    | System | Sshserver | `DELETE /system/httpserver/httpwhitelist/{id}` | (*New Schema) |
    | System | httpserver | `GET /system/httpserver/httpswhitelist` | (*New Schema) | 
    | System | httpserver | `POST /system/httpserver/httpswhitelist` | (*New Schema) |    
    | System | Sshserver | `DELETE /system/httpserver/httpswhitelist/{id}` | (*New Schema) |   

    **New Schema**
    | Name |Description| 
    | ---|---|
    |httpWhiteList| WhiteList of HTTP server |
    |httpsWhiteList| WhiteList of HTTPS server |
    **httpWhiteList**
    | Name |Description| 
    | ---|---|
    |id| id of WhiteList |
    |ipRange| ipRange of WhiteList |
    |firewallId| firewallId of iptables |
    **httpsWhiteList**
    | Name |Description| 
    | ---|---|
    |id| id of WhiteList |
    |ipRange| ipRange of WhiteList |
    |firewallId| firewallId of iptables |
    

