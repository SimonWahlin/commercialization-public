---
author: joshbax-msft
title: WiFi Direct Scenario Tests - BasicPlus (a38222aa-6a67-4b3c-84d0-ac34e40ba6e0)
description: WiFi Direct Scenario Tests - BasicPlus (a38222aa-6a67-4b3c-84d0-ac34e40ba6e0)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 791aa81c-f1d9-45c6-a0ba-16e347078f4a
---

# WiFi Direct Scenario Tests - BasicPlus (a38222aa-6a67-4b3c-84d0-ac34e40ba6e0)


This test suite verifies basic Wi-Fi Direct (WFD) pairing and ReInvoke Invitation. The test also verifies the operation of the stop discovery OID.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>Device.Network.WLAN.CSBWiFiDirect.SupportAtLeast2WiFiDirectPortsConcurrently Device.Network.WLAN.CSBWiFiDirect.SupportAtLeast4Clients Device.Network.WLAN.WiFiDirect.SupportAtLeast2WiFiDirectPortsConcurrently Device.Network.WLAN.WiFiDirect.SupportAtLeast4Clients</p>
<p>[See the device hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254483)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~6 minutes</p></td>
</tr>
<tr class="even">
<td><p><strong>Categories</strong></p></td>
<td><p>Certification Functional</p></td>
</tr>
<tr class="odd">
<td><p><strong>Type</strong></p></td>
<td><p>Automated</p></td>
</tr>
</tbody>
</table>

 

## Running the test


Before you run the test, complete the test setup as described in the test requirements: [Wireless LAN (802.11) Testing Prerequisites](wireless-lan--80211--testing-prerequisites.md).

This test suite does the following:

1.  ReInvoke Invitation

    1.  The system under test (SUT) acts as a listener and waits in discoverable mode.

    2.  The device under test (DUT) discovers the SUT and pairs with it by using the Device Association Framework (DAF).

    3.  The DUT waits for the connection to be automatically destroyed in a few seconds.

    4.  The DUT reconnects to the SUT.

    5.  The DUT disconnects from the SUT.

    6.  The paired SUT is removed (DAF Remove Association).

2.  The SUT acts as a device in listen mode.

    1.  The DUT discovers the SUT and confirms that it is visible and that the discovered SUT has the correct PrimaryDeviceType attribute in the device descriptor.

    2.  The DUT starts a discover request and cancels it after one second.

    3.  The DUT starts a discover request and cancels it after two seconds.

    4.  The DUT starts a discover request and cancels it after three seconds.

    5.  The DUT starts a discover request and cancels it after ten seconds.

    In all four test variations, it is confirmed that the cancel discovery request and the original discovery request were both successful.

## Troubleshooting


For troubleshooting information, see [Troubleshooting Wireless LAN (802.11) Tests](troubleshooting-wireless-lan--80211--tests.md).

## More information


### Command syntax

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PIN</strong></p></td>
<td><p>The WPS-PIN for WFD pairing.</p>
<p>Default value: 12345670</p></td>
</tr>
</tbody>
</table>

 

## Related topics


[WiFi Direct Scenario Tests](wifi-direct-scenario-tests.md)

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20WiFi%20Direct%20Scenario%20Tests%20-%20BasicPlus%20%28a38222aa-6a67-4b3c-84d0-ac34e40ba6e0%29%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")




