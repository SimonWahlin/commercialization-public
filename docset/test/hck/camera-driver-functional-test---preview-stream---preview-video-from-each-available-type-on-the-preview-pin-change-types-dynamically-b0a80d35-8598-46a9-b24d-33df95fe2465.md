---
author: joshbax-msft
title: Camera Driver Functional Test - Preview Stream - Preview video from each available type on the preview pin, change types dynamically
description: Camera Driver Functional Test - Preview Stream - Preview video from each available type on the preview pin, change types dynamically
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2c26ed61-5593-4389-b2df-0e47d28ab4a3
---

# Camera Driver Functional Test - Preview Stream - Preview video from each available type on the preview pin, change types dynamically


These set of tests validate cameras functionality with the MF and IMFCaptureEngine.

-   **Camera Driver Basic Tests - \***

    Tests against a subset of camera media types and shorter duration of tests than functional or reliability.

-   **Camera Driver Functional Tests - \***

    Tests against a larger set of media types and have longer duration of the test.

-   **Camera Driver Reliability Tests - \***

    Tests against a larger set of media types and have longer duration of the test, and more complex scenarios.

-   **\*- Preview Stream - \***

    Validates that the system is able to preview from MF\_CAPTURE\_ENGINE\_PREFERRED\_SOURCE\_STREAM\_FOR\_VIDEO\_PREVIEW.

This test will stream from each available mediatype that is exposed by the preferred source stream for video preview. The source will not be stopped between changes to the mediatype desired from the source.

## Test details


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Associated requirements</strong></p></td>
<td><p>System.Client.Webcam.VideoCaptureAndCamera</p>
<p>[See the system hardware requirements.](http://go.microsoft.com/fwlink/p/?linkid=254482)</p></td>
</tr>
<tr class="even">
<td><p><strong>Platforms</strong></p></td>
<td><p>Windows RT 8.1 Windows 8.1 x64 Windows 8.1 x86</p></td>
</tr>
<tr class="odd">
<td><p><strong>Expected run time</strong></p></td>
<td><p>~2 minutes</p></td>
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


Before you run the test, complete the test setup as described in the test requirements: [System Client Testing Prerequisites](system-client-testing-prerequisites.md).

## Troubleshooting


For troubleshooting information, see [Troubleshooting System Client Testing](troubleshooting-system-client-testing.md).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Error</th>
<th>Description/Workaround</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>0x8004005 : E_FAIL</p></td>
<td><p>The most often occurrence of this error code is during the verification of the Recorded file for Video or Photo. This will occur if the resulting file contains no data because it did not receive samples.</p>
<p>Check to ensure the device is producing valid samples when it enters the run state. Valid includes that the sample is the right size, format, and time for when it was produced.</p></td>
</tr>
<tr class="even">
<td><p>0x80070102</p></td>
<td><p>This will occur when a Capture Asynchronous Operation has timed out. These include Initialize, Start Preview, Stop Preview, Start Record, Stop Record, Take Photo, and Change Mediatype. The test allows for 9-10 seconds for each operation before failing. Mediatype change can include pin tear down and bring up time.</p>
<p>Check that the device isn’t waiting for future commands that prevent it from changing state. Ensure that all buffers are flushed out of the device on device reset commands.</p></td>
</tr>
<tr class="odd">
<td><p>0xC00D3704 : MF_E_HW_MFT_FAILED_START_STREAMING</p></td>
<td><p>This error occurs when the device cannot enter the run state.</p>
<p>Check that the device is able to transition through all states without failure, or that other pins aren’t preventing the device from entering a state.</p></td>
</tr>
<tr class="even">
<td><p>0xC00D4A44 : MF_E_SINK_NO_SAMPLES_PROCESSED</p></td>
<td><p>This error occurs during finalization of files, if no samples have been delivered.</p>
<p>Check to ensure the device is producing valid samples when it enters the run state. Valid includes that the sample is the right size, format, and time for when it was produced.</p></td>
</tr>
</tbody>
</table>

 

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_hck\p_hck%5D:%20Camera%20Driver%20Functional%20Test%20-%20Preview%20Stream%20-%20Preview%20video%20from%20each%20available%20type%20on%20the%20preview%20pin,%20change%20types%20dynamically%20%20RELEASE:%20%284/27/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



