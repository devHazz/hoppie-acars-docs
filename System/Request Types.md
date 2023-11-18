## 🔎 Request Type Attributes


| Request Type (11) | Attributes |
| -- | -- |
|  Progress  | Payload Type: [Progress Format](/Messaging/Progress%20Format.md) |
|  CPDLC  | Payload Type: [CPDLC Format](/Messaging/CPDLC%20Format.md) <br> Comments: Simulates the FANS 1/A Network |
|  ADS-C  | Payload Type: [ADS-C Format](/Messaging/ADS-C%20Format.md) |
|  Telex  | Payload Type: Freetext Data (256 Char Limit) |
|  Ping  | Payload Type: ACARS Callsign List (Optional) <br> Comments: Payload containing `ALL-CALLSIGNS` returns a list of all recently seen callsigns  |
|  Position  | Payload Type: *Unknown* |
|  PosReq (Position Request)  | Payload Type: ❌ <br> Comments: Requests the return of a Position Message |
|  Poll  | |
|  Peek  | |
|  DataReq (File Download Request)  | |
|  InfoReq (Weather Information Request)  | |