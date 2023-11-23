# CPDLC Format

## 🩻 Format Skeleton

##### `/data2/{min}/{mrn}/{res}/{elem}`

| Parameter | Description |
| -- | -- |
| `data2` | Common prefix used in all CPDLC Messages |
| `{min}` | **MIN (Message Identification Number)**: Refer to [MINs & MRNs - What are they?](#MINs%20&%20MRNs%20-%20What%20are%20they?) |
| `{mrn}` | **MRN (Message Reference Number)**: Refer to [MINs & MRNs - What are they?](#MINs%20&%20MRNs%20-%20What%20are%20they?) |
| `{res}` | **Response**: Refer to [Response Requirements Key](#Response%20Requirements%20Key) |
| `{elem}` | **Message Element**: Page 53 onwards of [ATS Data link Services in NAT Airspace](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf)

## Logon

Hoppie's ACARS System has a simplified login protocol. The avionic system (Downlink) sends a CPDLC Message with a **Response Required** (**Y**) type and packet content of `REQUEST LOGON`

The uplink system will then respond with a CPDLC message which could include:
 - A message with a **NE attribute (which requires an operational response)** with a packet content of `LOGON ACCEPTED` which shows the uplink is ready to accept messages.  
or
 - A message with a **NE attribute (which requires an operational response)** with a usual packet content of `UNABLE` which shows the uplink station cannot accept messages.  

## 🗣️ Example Hoppie ACARS Exchange:

```
(From) -> (To):
LRBL -> SWR160

Packet Content:
/data2/3//WU/PROCEED DIRECT TO @UDROS

MIN=3
```

`WU` = Requires a Wilco/Unable Response  
`PROCEED DIRECT TO @UDROS`= Message Element: These elements can be found from Page 53 of [ATS Data link Services in NAT Airspace](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf) and reference the response required (if any). UDROS is prefixed with a `@` symbol to show as a variable field.

---
```
(From) -> (To):
SWR160 -> LRBL

Packet Content:
/data2/8/3/N/WILCO

MIN=8
MRN=3 (Relabels LRBL's MIN)
```

`N` = Response not required  
`WILCO` = Message Element: Will close the uplink message

---
## MINs & MRNs - What are they?

**MIN (Message Identification Number)** - A unique identifier that is assigned to every uplink and downlink message during each CPDLC connection. MINs for uplink messages will be assigned by the ground system, and those for downlink messages by the avionics. MINs ***should be*** assigned sequentially to each uplink message within each CPDLC connection by the ground system. **Some, but not all, avionics systems will assign MINs to downlink messages sequentially**

**MRN (Message Reference Number)** - A number used to respond to a message. When responding to a message, the MIN from that message is included, relabeled as the MRN. This relates responses to the messages that prompted them ([ATS Data link Services in NAT Airspace - 5.4.2](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf)).


## Response Requirements Key

![chrome_lDhKX6XOlx](/img/chrome_lDhKX6XOlx.png)

## Example MIN and MRN Correlation Sequences

![chrome_SvfDA9SNAh](/img/chrome_SvfDA9SNAh.png)