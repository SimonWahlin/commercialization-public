---
author: kpacquer
Description: 'Introduced in Windows 10 Mobile, manufacturing mode is a mode of the full operating system that can be used for manufacturing-related tasks, such as component and support testing.'
ms.assetid: 9c5831f5-a200-436c-97cc-8bd92b30cb3e
MSHAttr: 'PreferredLib:/library/windows/hardware'
title: Manufacturing Mode
---

# Manufacturing Mode


Introduced in Windows 10 Mobile, manufacturing mode is a mode of the full operating system that can be used for manufacturing-related tasks, such as component and support testing.

In Windows Phone 8.1, you had to flash the Microsoft Manufacturing Operating System (MMOS) to do manufacturing tests and processes, such as test hardware, blow fuses, and provision security keys. Once the tests were completed, you had to flash the full operating system. This added extra time on the manufacturing floor.

This new feature allows you to boot into a manufacturing mode of the full operating system (and do those manufacturing steps) without having to flash an MMOS image.

## <span id="Manufacturing_profiles"></span><span id="manufacturing_profiles"></span><span id="MANUFACTURING_PROFILES"></span>Manufacturing profiles


A manufacturing profile defines settings that should be used when the operating system boots in manufacturing mode. The device can have more than one manufacturing profile. A profile named Default is included with Windows 10 Mobile. The default profile contains the settings for Microsoft components that let the device boot into a minimal environment for Manufacturing Mode.

Manufacturing profiles are stored in the registry on the device in the following location:

**HKEY\_LOCAL\_MACHINE\\System\\CurrentControlSet\\Control\\ManufacturingMode**
You must create a subkey for each manufacturing profile. Under the profile key, you can change the settings for some select operating system components for when the system is booting in manufacturing mode. For example, you can alter which services are started when this manufacturing profile is enabled. You can add your own services in the Services subkey, as shown below. If you want to set all services to the same start type, you can use an \* for the service name. If the \* wildcard is not used, all Win32 services that are not included in the manufacturing profile will use their default start type.

**Note**  The \* wildcard only applies to Win32 services, excluding kernel-mode drivers.

 

The following example creates a manufacturing profile named CustomProfile, causes the service named OEMFactoryTestService to automatically start, and all other Win32 services to demand start:

``` syntax
[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services]

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\OEMFactoryTestService]
"Start"=dword:00000002

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\ManufacturingMode\CustomProfile\Services\*]
"Start"=dword:00000003
```

The manufacturing profile name must be less than 64 characters.

You cannot use **Current** for the name of your manufacturing profile. This name is reserved for the currently active manufacturing profile.

 

 

[Send comments about this topic to Microsoft](mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phManuRetail\p_phManuRetail%5D:%20Manufacturing%20Mode%20%20RELEASE:%20%284/11/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Send comments about this topic to Microsoft")


