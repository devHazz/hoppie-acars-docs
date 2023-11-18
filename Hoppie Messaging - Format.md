
## Foreword

For the most part (from what I've seen), the Hoppie ACARS follows the FAA Guidance Material for ATS Data Link Services pretty perfectly. It follows the same UL (Uplink) & DL (Downlink) templates whereas the logon has been simplified.


### Format Skeleton

##### `/data2/{1}/{2}/{3}/{4}`

| Parameter | Description |
| -- | -- |
| `data2` | Common prefix used in all CPDLC Messages |
| `{1}` | **MIN (Message Identification Number)**: Refer to [[Hoppie Messaging - Format#MINs & MRNs - What are they?]] |
| `{2}` | **MRN (Message Reference Number)**: Refer to [[Hoppie Messaging - Format#MINs & MRNs - What are they?]] |
| `{3}` | **Response**: Refer to [[Hoppie Messaging - Format#Response Requirements Key]] |
| `{4}` | **Message Element**: Page 53 onwards of [ATS Data link Services in NAT Airspace](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf)

# An Example Hoppie ACARS Exchange:

---

(LRBL->SWR160)
##### `/data2/3//WU/PROCEED DIRECT TO @UDROS`

**WU** = Response Type: Wilco/Unable

***PROCEED DIRECT TO @UDROS*** = Message Element: These elements can be found from Page 53 of [ATS Data link Services in NAT Airspace](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf) and reference the response required (if any). UDROS is prefixed with a `@` symbol to show as a variable field.

---

(SWR160->LRBL) (Response to MIN 3)
##### `/data2/8/3/N/WILCO`

MRN = **3** (Relabels LRBL's MIN)

**N** = Response Type: Response not required

***WILCO*** = Message Element: Will close the uplink message


---
# MINs & MRNs - What are they?

**MIN (Message Identification Number)** - A unique identifier that is assigned to every uplink and downlink message during each CPDLC connection. MINs for uplink messages will be assigned by the ground system, and those for downlink messages by the avionics. MINs ***should be*** assigned sequentially to each uplink message within each CPDLC connection by the ground system. **Some, but not all, avionics systems will assign MINs to downlink messages sequentially**

**MRN (Message Reference Number)** - A number used to respond to a message. When responding to a message, the MIN from that message is included, relabeled as the MRN. This relates responses to the messages that prompted them ([ATS Data link Services in NAT Airspace - 5.4.2](https://www.notams.faa.gov/downloads/CPDLC_ver_10.pdf)).


# Response Requirements Key

![[chrome_lDhKX6XOlx.png]]

# Example MIN and MRN Correlation Sequences

![[chrome_SvfDA9SNAh.png]]