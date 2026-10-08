# 🤖 Android prerequisites and Intune settings

[Public documentation](README.md)

This guide covers the Android-specific tenant setup and the main Intune settings areas to review before deploying this repository's Android exports. Intune's Android options vary by enrollment type, device capabilities, licensing, and tenant configuration; this is a deployment checklist, not a copy of every setting Microsoft exposes.

> [!IMPORTANT]
> Decide which Android enrollment scenario you are managing before creating policies. Android Enterprise work profiles, fully managed, dedicated, and AOSP devices do not support identical settings. Review each policy in the Intune admin center, verify current Microsoft requirements, and pilot before broad assignment.

## 1. Prepare the tenant

Complete the [General prerequisites](general-prerequisites.md) and then verify the Android-specific items:

1. **Users, groups, licences, and authority:** Add the users and groups that will receive policies, assign appropriate Intune licences, and set Intune as the mobile device management (MDM) authority. Use least-privilege Intune roles. Conditional Access requires the applicable Microsoft Entra ID licensing.
2. **Choose the management platform and ownership:** Use Android Enterprise for Google Mobile Services (GMS) devices. Choose a work profile for personal/BYOD use, a corporate-owned work profile (COPE) for company devices with a personal area, fully managed for company devices used for work, or dedicated for kiosk/shared single-purpose devices. Use AOSP for supported devices that do not use GMS; AOSP has its own enrollment and policy limitations.
3. **Connect Managed Google Play:** For Android Enterprise, connect the Intune tenant to Managed Google Play from **Devices > Enrollment > Android > Managed Google Play**. This is needed to manage Android Enterprise enrollment and deploy managed Google Play apps. Use an organizational account with a working mailbox and keep more than one administrator for continuity.
4. **Check device and network support:** Confirm the device model, Android version, Google services, enrollment route, and required Microsoft/Google endpoints are supported and reachable. Microsoft's supported Android versions change; check the current [supported platforms](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms) and [AOSP supported devices](https://learn.microsoft.com/en-us/intune/fundamentals/aosp-supported-devices). The current reference lists Android 10+ for user-based management and Android 8+ for userless Android Enterprise dedicated and AOSP methods. App protection policies and app configuration delivered through Managed apps also require Android 10+.
5. **Plan enrollment controls:** Configure Android enrollment restrictions, ownership restrictions, and the enrollment profiles or tokens for your scenario. Corporate-owned fully managed, dedicated, and COPE enrollment generally needs a new or factory-reset device. Decide whether to use QR code, zero-touch, Samsung Knox Mobile Enrollment, or another supported corporate provisioning method.
6. **Plan identity and access:** Decide how users authenticate during enrollment and how Android compliance, app protection, and Microsoft Entra Conditional Access will work together. Test sign-in and enrollment with a pilot account before enforcing access rules.

> [!WARNING]
> Android Device Administrator (legacy) is deprecated; it is no longer available for GMS devices. Use Android Enterprise or a supported AOSP scenario for new Android deployments. Android BYOD work-profile enrollment is transitioning to Google's Android Management API and web-based enrollment. Test the current enrollment flow and update helpdesk instructions; enabling web-based enrollment is a tenant-level change for new personal work-profile enrollments and cannot be reversed.

## 2. Select the enrollment model

| Scenario | Use it for | Key considerations |
| --- | --- | --- |
| Android Enterprise personally owned work profile (BYOD) | Personal phones with a separate work profile | The organization manages work data, not the personal profile. Users enroll their own device. Intune's web-based and app-based flows depend on tenant setup; review the Android Management API transition before enabling web enrollment. |
| Android Enterprise corporate-owned work profile (COPE) | Company-owned device with separate work and personal areas | Corporate provisioning and Managed Google Play are required. Decide which device features and personal-use boundaries are appropriate. |
| Android Enterprise fully managed | Company-owned device dedicated to one user for work | The organization manages the whole device. Provision using a supported corporate enrollment method; factory reset is normally required. |
| Android Enterprise dedicated | Kiosk, shared, or single-purpose company device | Usually userless; target device groups and configure kiosk/Managed Home Screen behavior where needed. A userless device without Microsoft Entra shared device mode cannot use user-based Conditional Access to access resources. |
| Android Open Source Project (AOSP) | Supported devices without GMS, including specialized hardware | Uses a separate enrollment method and policy set. Confirm the specific device is on Microsoft's supported list and do not assume Google-dependent settings, apps, or integrity checks will work. |

See Microsoft's [Android enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/android/guide) and setup pages for [personally owned work profiles](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-personal-work-profile), [corporate-owned work profiles](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-corporate-work-profile), [fully managed devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-fully-managed), and [dedicated devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-dedicated).

## 3. Intune settings to configure and review

The admin center's labels can change. These are the Android management areas to work through; exact available settings depend on enrollment type and the device.

| Intune area | What to configure for Android | Relevant exports in this repository |
| --- | --- | --- |
| **Devices > Enrollment** | Android enrollment restrictions, personal/corporate ownership handling, Android Enterprise connection, and scenario-specific enrollment profiles, tokens, or provisioning methods. | No enrollment profile or tenant enrollment restriction is exported. Configure these in the target tenant. |
| **Devices > Configuration** | Android Enterprise/AOSP device settings such as restrictions, password and device features, Wi-Fi, VPN, certificates, and kiosk behavior. Use the Settings Catalog or supported profile templates, and check the setting's supported enrollment types. | Corporate Android configuration; BYOD Defender onboarding; Settings Catalog controls for VPN/Common Criteria, wipe after ten failed logons, and threat scanning. |
| **Devices > Compliance** | Depending on enrollment type: device health and integrity/Play Protect, rooted-device status, OS and security patch levels, encryption, device or work-profile password requirements, and mobile threat-defense risk. Set actions for noncompliance and a grace period suitable for the organization. | Android Enterprise, BYOD, and AOSP compliance exports include health, OS/property, encryption, password, app-integrity, and Defender-risk controls. Review policy applicability and overlapping policies before assignment. |
| **Apps > All apps / Android** | Add and assign required apps; approve or sync apps from Managed Google Play for Android Enterprise. Configure app installation/update behavior and kiosk apps where applicable. | Microsoft Intune, Authenticator, Defender, Outlook, and Managed Home Screen app exports. Confirm each app and assignment in the tenant. |
| **Apps > App configuration policies** | Deliver app-specific settings to managed apps (and, where supported, managed devices). Use the app's documented keys and target the correct Android management type. | Microsoft Defender managed app configuration for BYOD. |
| **Apps > App protection policies** | Protect organization data inside supported apps on enrolled or unenrolled devices: data transfer, save/copy controls, access requirements, conditional launch, and selective wipe. Scope to users and supported apps. | Android App Protection Policy export. App protection (MAM) is not a substitute for device enrollment where device-wide controls are required. |
| **Endpoint security / mobile threat defense** | Connect Microsoft Defender for Endpoint or another supported mobile threat defense provider, deploy its app, provide required app configuration, and use its risk signal only after verifying the connector and licensing. | Defender app, BYOD onboarding/configuration, and compliance policies that consume Defender risk. |
| **Assignments and filters** | Assign to deliberate user or device groups. Use filters to distinguish Android Enterprise, ownership, and enrollment scope. For dedicated userless devices, target device groups. Exclude pilot/test populations and resolve conflicting profiles. | Android Enterprise and corporate/personal ownership assignment filters. |
| **Microsoft Entra Conditional Access** | Create and test access policies separately from importing these exports. Common designs require compliant devices for device-based access or approved/protected apps for app-based access. Provide an enrollment and remediation path before blocking access. | Conditional Access policies are not included. They are tenant-wide access controls and must be designed for the organization's users, apps, and emergency access accounts. |

Use Microsoft's [Android deployment guide](https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-android) for the complete workflow and its links to current setting references. For setting-by-setting references, see [Android Enterprise compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-enterprise-settings), [Android Settings Catalog](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/ref-android-settings), [Android Enterprise device restrictions](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-android-enterprise), [Android Enterprise Wi-Fi settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android-enterprise), [Android Enterprise VPN settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise), and [Android App Protection settings](https://learn.microsoft.com/en-us/intune/app-management/protection/ref-settings-android).

## 4. Deploy safely

1. Choose **one** Android package and compare its `Config overview.md` and `build-manifest.json`. The repository's `Full` package combines Android resources across tiers; it is not a universal configuration for every enrollment type.
2. Import only needed resources and dependencies. These exports do not create tenant groups, enrollment profiles, Conditional Access policies, licensing, or other tenant-level prerequisites.
3. Review each imported setting for business impact, platform support, OEM behavior, licensing, app availability, and tenant-specific values. Do not assume an imported policy's assignment is suitable for your tenant.
4. Assign to a small pilot group or device group. Verify check-in, app deployment, compliance state, Defender signals, sign-in, and user experience for every enrollment scenario you use.
5. Configure staged noncompliance actions and Conditional Access only after confirming users can enroll, remediate, and regain access. Expand deployment gradually and monitor Intune reports.

For package selection and import steps, see [File structure](file-structure.md) and [How to import](how-to-import.md).

## Microsoft references

- [Deployment guide: Manage Android devices in Microsoft Intune](https://learn.microsoft.com/en-us/intune/fundamentals/platform-guide-android)
- [Android device enrollment guide](https://learn.microsoft.com/en-us/intune/device-enrollment/android/guide)
- [Connect Intune to Managed Google Play](https://learn.microsoft.com/en-us/intune/device-enrollment/android/connect-managed-google-play)
- [Android Management API for personally owned work profiles](https://learn.microsoft.com/en-us/intune/device-enrollment/android/android-management-api-overview)
- [Use Conditional Access with Intune compliance policies](https://learn.microsoft.com/en-us/intune/device-security/conditional-access-integration/overview)
- [Android Enterprise compliance settings](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-android-enterprise-settings)
- [Android Settings Catalog reference](https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/ref-android-settings)
- [Android Enterprise Wi-Fi settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-wifi-settings-android-enterprise)
- [Android Enterprise VPN settings](https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-vpn-settings-android-enterprise)
- [Android App Protection settings](https://learn.microsoft.com/en-us/intune/app-management/protection/ref-settings-android)
