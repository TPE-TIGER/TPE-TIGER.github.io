# API version release notes
## V1.5 (2023-08)
The functionality and changes below were added in AIG-301 V1.5.

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


/api/v1/{cloud}/messages
