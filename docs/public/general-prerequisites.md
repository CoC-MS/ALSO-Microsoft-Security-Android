# 🚀 General prerequisites

[Public documentation](README.md)

Check these items before importing Android resources into Microsoft Intune. For the Android enrollment setup and Intune settings to review, see [Android prerequisites](android-prerequisites.md).

> [!IMPORTANT]
> Confirm the target tenant and review each resource before import. Package names and policy names do not replace checking the licensing and service requirements for individual settings.

---

## 🔐 Licensing and platform

The repository provides `BP`, `E3-E5`, and `E5` licence-classified packages, with Basic and Adv package names, as well as a Full package. These labels describe package classifications; they do not confirm that your tenant is licensed for every included feature. Check the required licences and service availability for each policy you intend to use. Review the selected package's overview and manifest to understand its scope and included resources.

Identify the target management scenario and ownership: Android Enterprise personally owned work profile (BYOD), corporate-owned work profile (COPE), fully managed, dedicated, or AOSP. Confirm that every selected setting and app supports the target enrollment type, device, and Android version. Do not assume that an Android Enterprise setting or Google-dependent feature applies to AOSP.

## 🧰 Access and dependencies

Use an account with the Intune permissions needed to import and manage the selected resources, and follow your organization's approval process for any consent requested by an import tool. Confirm Intune is the MDM authority and that users and groups have the appropriate licences and permissions.

Review each policy's description, settings, references, and assignments. These exports do not configure tenant-wide prerequisites such as enrollment restrictions and profiles, groups, Conditional Access, or service connections. Prepare the tenant-specific dependencies required by the policies you select:

| Dependency | Check before import or assignment |
| --- | --- |
| Android Enterprise | Connect Intune to the intended Managed Google Play account and make required managed apps available. This does not apply to AOSP-only deployments. |
| Microsoft Defender for Endpoint or another mobile threat defense service | Confirm the tenant connector, app deployment and configuration, required licensing, and risk-signal integration when selected policies depend on them. |
| Applications, groups, and assignment filters | Confirm required apps are available and tenant-specific group membership, filters, and assignments match the intended users or devices. |
| Conditional Access and enrollment | Design and test these separately in the tenant. Ensure users have a supported enrollment and remediation path before enforcing access requirements. |

## 🧪 Deployment readiness

Choose one Android package for the tenant; do not combine packages or import Full after another package. Prepare a pilot user or device group for each enrollment scenario and a way to validate policy deployment, app availability, compliance, access, and user impact before expanding assignments.

See [File structure](file-structure.md) to compare package contents, [Android prerequisites](android-prerequisites.md) for the enrollment and settings checklist, and [How to import](how-to-import.md) for the import sequence.
