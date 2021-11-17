# Pulse Secure VPN

## Get it to work on Win 11 despite of the 'keeps reconnecting issue'

- Download the latest version from [here](https://software.uconn.edu/pulse-secure-client-download/) (v9.1.13) - maybe this step can be skipped, not tested that
- Connect to the VPN as usual, it keeps reconnecting at this point (but that's ok)
- Open Network Connections (the oldschool/hidden one in windows)
- When the VPN is trying to connect an adapter named Pulse Secure shows up
- Edit the properties of this adapter and enable the `Juniper Network Service` ([original article](https://docs.pulsesecure.net/WebHelp/PCS/9.1R1/AG/Content/ps-pcs-gettingstartedguide-9.1R1/Download_Software.htm))
- VPN connection should stabilise immediately

Downside is that you need to enable the `Juniper Network Service` on every connection
