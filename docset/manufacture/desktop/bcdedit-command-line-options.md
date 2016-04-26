---
author: Justinha
Description: 'BCDEdit is a command-line tool for managing Boot Configuration Data (BCD).'
ms.assetid: cf7d52f0-13fb-416d-9ec5-9e4eff4fd774
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: 'BCDEdit Command-Line Options'
---

# <span id="p_adk_online.bcdedit_command-line_options"></span>BCDEdit Command-Line Options


BCDEdit is a command-line tool for managing Boot Configuration Data (BCD).

BCD files provide a store that is used to describe boot applications and boot application settings.

BCDEdit can be used for a variety of purposes, including creating new stores, modifying existing stores, adding boot menu options, and so on.

You'll need administrative privileges to use BCDEdit to modify BCD. Start the Command Prompt (Admin) or use Windows PE.

A normal shutdown and reboot is necessary to ensure that any modified BCDEdit settings are flushed to disk.

BCDEdit is included in the %WINDIR%\\System32 folder.

BCDEdit is limited to the standard data types and is designed primarily to perform single common changes to BCD. Related resources:

-   Some common BCD operations, such as recovering a partition or setting up a new PC's system partition, may be more easily accomplished by using [BCDboot](bcdboot-command-line-options-techref-di.md).
-   For complex operations or nonstandard data types, consider using the BCD Windows Management Instrumentation (WMI) application programming interface (API) to create more powerful and flexible custom tools.

## <span id="BCDEdit_Command-Line_Options"></span><span id="bcdedit_command-line_options"></span><span id="BCDEDIT_COMMAND-LINE_OPTIONS"></span>BCDEdit Command-Line Options


The following command-line options are available for BCDEdit.exe.

**BCDEdit /Command***\[Argument1\] \[Argument2\] ...*

### <span id="Help"></span><span id="help"></span><span id="HELP"></span>Help

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/? [commmand]</td>
<td align="left"><p>Displays a list of BCDEdit commands.</p>
<p>To display detailed help for a particular command, run <strong>bcdedit /?</strong><em>command</em>, where <em>command</em> is the name of the command you are searching for more information about.</p>
<pre class="syntax" space="preserve"><code>bcdedit /? createstore</code></pre></td>
</tr>
</tbody>
</table>

 

### <span id="Operating_on_a_store"></span><span id="operating_on_a_store"></span><span id="OPERATING_ON_A_STORE"></span>Operating on a store

| Option       | Description                                                                                                                                                                                                                                                             |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /createstore | Creates a new empty boot configuration data store. The created store is not a system store.                                                                                                                                                                             |
| /export      | Exports the contents of the system store into a file. This file can be used later to restore the state of the system store. This command is valid only for the system store.                                                                                            |
| /import      | Restores the state of the system store by using a backup data file previously generated by using the /export option. This command deletes any existing entries in the system store before the import takes place. This command is valid only for the system store.      |
| /store       | This option can be used with most BCDedit commands to specify the store to be used. If this option is not specified, then BCDEdit operates on the system store. Running the bcdedit /store command by itself is equivalent to running the bcdedit /enum active command. |
| /sysstore    | Sets the system store device. This only affects EFI-based systems. It does not persist across reboots, and is only used in cases where the system store device is ambiguous.                                                                                            |

 

### <span id="Operating_on_entries_in_a_store"></span><span id="operating_on_entries_in_a_store"></span><span id="OPERATING_ON_ENTRIES_IN_A_STORE"></span>Operating on entries in a store

| Option  | Description                                                                                                                                                                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /copy   | Makes a copy of a specified boot entry in the same system store.                                                                                                                                                                                                                                  |
| /create | Creates a new entry in the boot configuration data store. If a well-known identifier is specified, then the /application, /inherit, and /device options cannot be specified. If an identifier is not specified or not well known, an /application, /inherit, or /device option must be specified. |
| /delete | Deletes an element from a specified entry.                                                                                                                                                                                                                                                        |
| /mirror | Creates mirror of entries in the store.                                                                                                                                                                                                                                                           |

 

### <span id="Changing_entry_options"></span><span id="changing_entry_options"></span><span id="CHANGING_ENTRY_OPTIONS"></span>Changing entry options

| Option       | Description                                    |
|--------------|------------------------------------------------|
| /deletevalue | Deletes a specified element from a boot entry. |
| /set         | Sets an entry option value.                    |

 

### <span id="Controlling_output"></span><span id="controlling_output"></span><span id="CONTROLLING_OUTPUT"></span>Controlling output

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">/enum</td>
<td align="left">Lists entries in a store. The /enum option is the default value for BCEdit, so running the bcdedit command without options is equivalent to running the bcdedit /enum active command.</td>
</tr>
<tr class="even">
<td align="left">/v</td>
<td align="left">Verbose mode. Usually, any well-known entry identifiers are represented by their friendly shorthand form. Specifying /v as a command-line option displays all identifiers in full.
<p>Running the bcdedit /v command by itself is equivalent to running the bcdedit /enum active /v command.</p></td>
</tr>
</tbody>
</table>

 

### <span id="Controlling_the_boot_manager"></span><span id="controlling_the_boot_manager"></span><span id="CONTROLLING_THE_BOOT_MANAGER"></span>Controlling the boot manager

| Option             | Description                                                                                                                                                                                                                                          |
|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /bootsequence      | Specifies a one-time display order to be used for the next boot. This command is similar to the /displayorder option, except that it is used only the next time the computer starts. Afterwards, the computer reverts to the original display order. |
| /default           | Specifies the default entry that the boot manager selects when the timeout expires.                                                                                                                                                                  |
| /displayorder      | Specifies the display order that the boot manager uses when displaying boot options to a user.                                                                                                                                                       |
| /timeout           | Specifies the time to wait, in seconds, before the boot manager selects the default entry.                                                                                                                                                           |
| /toolsdisplayorder | Specifies the display order for the boot manager to use when displaying the Tools menu.                                                                                                                                                              |

 

### <span id="Emergency_Management_Services_options"></span><span id="emergency_management_services_options"></span><span id="EMERGENCY_MANAGEMENT_SERVICES_OPTIONS"></span>Emergency Management Services options

| Option       | Description                                                                                                               |
|--------------|---------------------------------------------------------------------------------------------------------------------------|
| /bootems     | Enables or disables Emergency Management Services (EMS) for the specified entry.                                          |
| /ems         | Enables or disables EMS for the specified operating system boot entry.                                                    |
| /emssettings | Sets the global EMS settings for the computer. /emssettings does not enable or disable EMS for any particular boot entry. |

 

### <span id="Debugging"></span><span id="debugging"></span><span id="DEBUGGING"></span>Debugging

| Option              | Description                                                                                                                                                                                                                                                               |
|---------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /bootdebug          | Enables or disables the boot debugger for a specified boot entry. Although this command works for any boot entry, it is effective only for boot applications.                                                                                                             |
| /dbgsettings        | Specifies or displays the global debugger settings for the system. This command does not enable or disable the kernel debugger; use the /debug option for that purpose. To set an individual global debugger setting, use the bcdedit /setdbgsettings type value command. |
| /debug              | Enables or disables the kernel debugger for a specified boot entry.                                                                                                                                                                                                       |
| /hypervisorsettings | Sets the hypervisor parameters.                                                                                                                                                                                                                                           |

 

To troubleshoot a new installation, enable debug mode by modifying the boot configuration file (BCD). For example, use the following syntax to enable kernel or boot debug.

``` syntax
bcdedit /set <id> debug on
```

-or-

``` syntax
bcdedit /set <id> bootdebug on
```

where &lt;id&gt; is the GUID of the Loader object that is used to load the operating system. "Default" can be used if the operating system is the default option of the Boot Manager menu.

For examples of BCDEdit, see [Boot Configuration Data in Windows Vista](http://go.microsoft.com/fwlink/?LinkId=69448).

### <span id="Remote_event_logging"></span><span id="remote_event_logging"></span><span id="REMOTE_EVENT_LOGGING"></span>Remote event logging

| Option         | Description                                                             |
|----------------|-------------------------------------------------------------------------|
| /eventsettings | Sets the global remote event logging parameters.                        |
| /event         | Enables or disables remote event logging for an operating system entry. |

 

## <span id="related_topics"></span>Related topics


[BCDboot](bcdboot-command-line-options-techref-di.md)

[BCD System Store Settings for UEFI](bcd-system-store-settings-for-uefi.md)

[BCDEdit Commands for Boot Environment](https://msdn.microsoft.com/library/windows/hardware/dn653986)

[4-Gigabyte Tuning: BCDEdit and Boot.ini](base.4_gigabyte_tuning)

[Boot Configuration Data in Windows Vista](http://go.microsoft.com/fwlink/?LinkId=69448)

Boot Configuration Data Editor Frequently Asked Questions
 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_adk_online\p_adk_online%5D:%20BCDEdit%20Command-Line%20Options%20%20RELEASE:%20%284/11/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")



