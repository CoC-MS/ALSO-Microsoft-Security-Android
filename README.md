# 🛡️ ALSO Microsoft Security - Android

> A collection of Microsoft Intune policy exports and supporting artifacts designed to help partners accelerate secure, managed Android deployments.
>
> **Includes Android Enterprise, personally owned work profiles (BYOD), Android (AOSP), app protection, and Microsoft Defender configurations. Licence requirements depend on the individual policy and service.**

---

> [!IMPORTANT]
> **⚠️ Read this before importing policies.**
>
> Every export is a starting point. Review settings, tenant-specific values, licences, dependencies, and assignments before deployment. Import policies to a pilot group first and validate their outcome before expanding assignments.

| Resource | Description |
| --- | --- |
| 📦 **Choose a Package** | See [Android configuration packages](#-android-configuration-packages) for edition contents and limitations. |
| 📖 **Naming Convention** | See [Policy naming](#-policy-naming) for the standard format and exceptions. |
| 🚀 **Before Importing** | See [Before importing](#-before-importing) for prerequisites and configuration requirements. |
| 📥 **How to Import** | See [How to import](#-how-to-import) for the Intune Management Tool workflow. |
| 🤖 **Full Android Package** | Browse all Android resources in [`Android/Full`](Android/Full). |
| 🔗 **Source Template** | Copied from [`CoC-MS/also-security-template-internal/out/Android`](https://github.com/CoC-MS/also-security-template-internal/tree/3890f64350a5be655c1ca6f8dcc760171bebb985/out/Android). |

---

## 📂 File structure

The Android exports are organized by licence edition and Intune workload:

```text
Android/
├── BP-Basic/
│   ├── Config overview.md
│   ├── build-manifest.json
│   ├── DeviceConfiguration/
│   └── SettingsCatalog/
├── E3-E5-Basic/
│   ├── Config overview.md
│   ├── build-manifest.json
│   ├── DeviceConfiguration/
│   └── SettingsCatalog/
├── E5-Basic/
│   ├── Config overview.md
│   ├── build-manifest.json
│   ├── DeviceConfiguration/
│   └── SettingsCatalog/
├── BP-Adv/
│   ├── Config overview.md
│   └── build-manifest.json
├── E3-E5-Adv/
│   ├── Config overview.md
│   └── build-manifest.json
├── E5-Adv/
│   ├── Config overview.md
│   └── build-manifest.json
└── Full/
    ├── Config overview.md
    ├── build-manifest.json
    ├── AppConfigurationManagedDevice/
    ├── Applications/
    ├── AppProtection/
    ├── AssignmentFilters/
    ├── CompliancePolicies/
    ├── DeviceConfiguration/
    └── SettingsCatalog/
```

## 📦 Android configuration packages

These are pre-generated packages copied from the internal template, not an Android application or a build tool. Each package includes a `Config overview.md` describing its scope and a `build-manifest.json` listing its resource files. Manifest paths are relative to the package itself.

| Package | Resource count | Included content |
| --- | --- | --- |
| [`BP-Basic`](Android/BP-Basic) | 5 | Two device configuration profiles and three Settings Catalog policies marked `BP` and `Basic`. |
| [`E3-E5-Basic`](Android/E3-E5-Basic) | 5 | Currently the same five policies as `BP-Basic`. |
| [`E5-Basic`](Android/E5-Basic) | 5 | Currently the same five policies as `BP-Basic`. |
| [`BP-Adv`](Android/BP-Adv) | 0 | Overview and manifest only; no Android policies currently match this edition. |
| [`E3-E5-Adv`](Android/E3-E5-Adv) | 0 | Overview and manifest only; no Android policies currently match this edition. |
| [`E5-Adv`](Android/E5-Adv) | 0 | Overview and manifest only; no Android policies currently match this edition. |
| [`Full`](Android/Full) | 31 | All Android resources, including the five Basic policies and resources without tier/licence markers. |

Licence builds are cumulative: `E3-E5` includes `BP`, and `E5` includes `BP` and `E3-E5`. Basic and Adv packages contain only resources explicitly marked with the matching tier and a supported licence. **Adv is not an additional layer on top of Basic**, and the copied Adv editions currently contain no policy exports.

> [!WARNING]
> **Choose one Android package per tenant. Do not combine Basic, Adv, and Full, or import Full after another package.**
>
> Intune imports can create duplicate policies rather than reconcile packages. `Full` means all Android resources, not that every resource is appropriate for every tenant, enrolment mode, or licence.

Cross-platform and tenant-wide dependencies remain in the source template's [`out/Shared/Full`](https://github.com/CoC-MS/also-security-template-internal/tree/3890f64350a5be655c1ca6f8dcc760171bebb985/out/Shared/Full) and are **not included in this repository**. Review that supporting content and import only required dependencies, not the whole Shared package.

## 🌐 Android coverage

The Full package contains the following workloads. Availability and suitability depend on the policy, device enrolment mode, and tenant configuration.

| Workload | Resources | Template content |
| --- | --- | --- |
| **AppConfigurationManagedDevice** | 1 | Microsoft Defender managed app configuration for Android BYOD. |
| **Applications** | 5 | Managed Home Screen, Microsoft Authenticator, Microsoft Defender, Microsoft Intune, and Microsoft Outlook app exports. |
| **AppProtection** | 1 | Android App Protection Policy. |
| **AssignmentFilters** | 3 | Android Enterprise targeting and corporate/personal ownership filters. |
| **CompliancePolicies** | 16 | Android Enterprise, BYOD, and AOSP health, OS version, encryption, password, integrity, and Defender risk policies, plus general Android compliance exports. |
| **DeviceConfiguration** | 2 | Corporate Android configuration and BYOD automatic enrolment to Microsoft Defender for Endpoint. |
| **SettingsCatalog** | 3 | Android Enterprise VPN/Common Criteria settings, wipe after ten failed logons, and threat scanning. |

## ✨ Notable capabilities

- **Defender integration:** BYOD device configuration and managed app configuration, with compliance policies for Defender risk.
- **Device compliance:** Separate Android Enterprise, BYOD, and AOSP policies covering device health and system security.
- **App protection and targeting:** An Android app protection policy, managed app exports, and ownership-based assignment filters.
- **Device restrictions:** Settings Catalog exports for threat scanning, VPN/Common Criteria controls, and failed-logon wipe behaviour.

## 📖 Policy naming

The source template's standard format is:

```text
<Licence> - <Company> - <Impact> - <Tier> - <Version> - <Platform> - <Category> - <Policy purpose> - <Scope>
```

| Component | Description | Examples |
| --- | --- | --- |
| `Licence` | Minimum licence marker in the template | `BP`, `E3-E5`, `E5` |
| `Company` | Template provider | `ALSO` |
| `Impact` | Expected implementation impact | `LI`, `MI`, `HI` |
| `Tier` | Baseline tier | `Basic`, `Adv` |
| `Version` | Policy version when present | `v1.0` |
| `Platform` | Target platform or enrolment mode | `Android`, `Android (BYOD)` |
| `Category` | Intune or security area | `Device Restriction` |
| `Policy purpose` | What the policy configures | `Threat Scan`, `Auto Enrollment to MDE` |
| `Scope` | Assignment scope when present | `D`, `U` |

`D` identifies a device-targeted policy and `U` identifies a user-targeted policy. For newly named policies, use ` - ` as the separator; do not use `/` in Intune policy names.

### Existing-name exceptions

The copied Android exports retain their original filenames and policy names, including en-dash separators, abbreviated names, omitted components, and the source spelling `Android Enterprice`. Compliance policies and assignment filters commonly use shorter `ALSO`-prefixed names; applications and app protection/configuration resources can use descriptive names without licence or tier markers. The files have not been renamed or normalized during this import.

## 🚀 Before importing

1. Choose one package and review its `Config overview.md` and `build-manifest.json`. The Adv packages currently have no policies to import.
2. Review every policy's settings, descriptions, assignments, and tenant-specific references. Match policies to the intended enrolment mode: Android Enterprise, personally owned work profile, or AOSP. General Android exports are also present; verify current Intune support before using them.
3. Confirm required Intune, app protection, and Defender licences. Configure the relevant Android enrolment prerequisites and Managed Google Play connection where applicable before importing app resources.
4. For Defender policies, review the Intune/Defender connector, app deployment, onboarding configuration, and device risk requirements. Review app references and assignment filter dependencies before importing resources that use them.
5. Review security controls with user impact, especially failed-logon wipe, password requirements, OS minimums, VPN restrictions, and compliance actions. Do not assume all Full-package compliance policies should be assigned together.
6. Import to a pilot group, validate the result in Intune, then expand assignments in stages.

## 📥 How to import

This repository follows the internal template's import workflow using the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement).

1. Download this repository and extract it, then download and extract the Intune Management Tool.
2. Start the tool using its documented launch instructions (`start.cmd` on Windows).
3. Authenticate to the target Microsoft Intune tenant with an account that has the required Intune permissions.
4. Browse to your chosen package under `Android` and import the matching JSON resources from its workload folders. `build-manifest.json` is package metadata, not an Intune policy.
5. Import required app and filter dependencies before policies that reference them. Resolve tenant-specific app, group, and filter references; do not assume source-tenant identifiers are usable in the target tenant.
6. Review the imported resources in Intune before assignment. Update tenant-specific values, groups, filters, and scope as required.
7. Assign the reviewed policies to a pilot group. Confirm deployment results and user impact before expanding to production.

> [!WARNING]
> Do not bulk import assignments. These exports can contain security controls, destructive wipe behaviour, and tenant-specific values that must be reviewed and approved before assignment to the target environment.

## 🔗 Source and licence

The `Android` folder is an unchanged copy of `out/Android` from [CoC-MS/also-security-template-internal](https://github.com/CoC-MS/also-security-template-internal) at revision [`3890f64350a5be655c1ca6f8dcc760171bebb985`](https://github.com/CoC-MS/also-security-template-internal/commit/3890f64350a5be655c1ca6f8dcc760171bebb985). This is a snapshot; changes in the source template do not automatically update this repository.

The upstream Apache License 2.0 is retained in [`LICENSE`](LICENSE).
