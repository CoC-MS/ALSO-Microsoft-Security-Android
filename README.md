# 🤖 ALSO Microsoft Security - Android

> Microsoft Intune security policy exports and supporting artifacts for Android Enterprise, personally owned work profiles (BYOD), AOSP, app protection, and Microsoft Defender.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

---

<a id="getting-started"></a>
## 🚀 Getting started

1. ✅ Review [General prerequisites](docs/public/general-prerequisites.md) and [Android prerequisites](docs/public/android-prerequisites.md).
2. 📂 [Download the repository ZIP](https://github.com/CoC-MS/ALSO-Microsoft-Security-Android/archive/refs/heads/main.zip) and follow the extraction guidance in [How to import](docs/public/how-to-import.md).
3. 📥 Follow [How to import](docs/public/how-to-import.md) to import only the resources you need. Review tenant-specific settings and dependencies, and leave assignment import disabled.
4. 🚀 Assign reviewed policies to a pilot group, check deployment reports and user impact, then expand in stages.

**Need help or have feedback?** See [Reporting issues](docs/public/reporting-issues.md) to report problems or suggest improvements.

> [!WARNING]
> All issues are public; do not include sensitive information.

### Quick navigation

| Section | What you will find |
| --- | --- |
| [Getting started](#getting-started) | Prerequisites, download, package selection, import, and staged rollout. |
| [Android licensing guide](#android-licensing-guide) | Review the BP and E5 package licensing guidance. |
| [Android configuration packages](#android-configuration-packages) | Compare package scope and open their overviews and manifests. |
| [Android coverage](#android-coverage) | Workloads and security areas covered by the Full package. |
| [Notable capabilities](#notable-capabilities) | Key features and deployment considerations. |
| [Documentation](#documentation) | Links to supporting guides and the repository license. |

---

<a id="android-licensing-guide"></a>
## Android Licensing Guide

Choose one standalone package.

### ✅ E5 Folder (Full Experience)

Package: [`E5`](Android/E5)

The **E5 folder** is intended for organizations that have access to full experience of Defender for Cloud apps with these licenses.

| License | Supported |
|----------|----------|
| Microsoft 365 E7 | ✅ Full support |
| Microsoft 365 E5 | ✅ Full support |
| Microsoft 365 E3 + Defender Suite | ✅ Full support |
| Business Premium + Defender Suite | ✅ Full support |
| Microsoft 365 F3 + Defender Suite | ✅ Full support |
| Microsoft 365 F1 + Defender Suite | ✅ Full support |

### ⚠️ BP Folder (Limited Experience)

Package: [`BP`](Android/BP)

The **Business Premium folder** is designed for organizations using Microsoft 365 Business Premium and other licenses with partial feature compatibility.

| License | Supported Features |
|----------|----------|
| Microsoft 365 Business Premium | ⚠️ Supported with limitations (without full Defender for Cloud Apps experience) |
| Microsoft 365 E3 | ⚠️ Supported with limitations (without full Defender for Cloud Apps experience) |
| Microsoft 365 F3 | ⚠️ Supported with limitations (without full Defender for Cloud Apps experience) |
| Microsoft 365 F1 | ⚠️ Intune settings only. Defender settings are not supported. |

> **Important:** Microsoft 365 F1 supports deployment of Intune configuration settings only. Microsoft Defender security policy settings included in this repository are not supported with F1 licensing.

> [!WARNING]
> Choose one Android package per tenant. Do not combine BP, E5, and Full, or import Full after another package; Intune imports can create duplicate policies rather than reconcile packages. Review tenant-specific values, dependencies, licences, and assignments before import.

---

<a id="android-configuration-packages"></a>
## 📦 Android configuration packages

Each package includes a `Config overview.md` and a `build-manifest.json` listing its exported resources. Manifest paths are relative to the package; check the selected package's manifest for its exact file list.

| Package overview | Licence classification | Scope | Resources in manifest | Manifest |
| --- | --- | --- | ---: | --- |
| [BP](Android/BP/Config%20overview.md) | 🏷️ **BP** | Android policies classified for BP | 13 | [BP manifest](Android/BP/build-manifest.json) |
| [E5](Android/E5/Config%20overview.md) | 🏷️ **BP + E3-E5 + E5** | Android policies classified up to E5 | 13 | [E5 manifest](Android/E5/build-manifest.json) |
| [Full](Android/Full/Config%20overview.md) | 🏷️ **All** | All Android resources in this repository | 39 | [Full manifest](Android/Full/build-manifest.json) |

Manifest counts include listed resources and supporting artifacts such as the migration table. The manifest and migration table are metadata, not Intune policies to import.

The BP and E5 packages contain their classified Android resources and applicable Conditional Access policies and dependencies. Full contains all Android resources in this repository, including resources not classified for BP or E5. Review the package overview and manifest before importing. Separate Shared packages are not included in this repository.

<a id="android-coverage"></a>
## 🌐 Android coverage

The Full package contains the following workload folders. Availability and suitability depend on the policy, device, enrollment type, and tenant configuration.

| Area | Included content |
| --- | --- |
| 📱 **Applications** | Microsoft Intune, Authenticator, Defender Antivirus, Outlook, and Managed Home Screen app exports. |
| 🛡️ **Compliance and device health** | Android Enterprise, BYOD, and AOSP compliance policies for OS version, encryption, passwords, integrity, and Defender risk. |
| 🔐 **App protection and configuration** | Android App Protection Policy and Microsoft Defender managed app configuration for BYOD. |
| 🎯 **Conditional Access and targeting** | Android-applicable Conditional Access policies, supporting groups, and assignment filters for Android Enterprise and device ownership. Review scope and dependencies before enabling. |
| ⚙️ **Device configuration** | Corporate Android configuration and BYOD automatic enrollment to Microsoft Defender for Endpoint. |
| 🧰 **Settings Catalog** | Android VPN/Common Criteria settings, wipe after ten failed logons, and threat scanning. |
| 📋 **Supporting artifacts** | Migration table and other package resources listed in the manifest. |

See the [Full package overview](Android/Full/Config%20overview.md) and [manifest](Android/Full/build-manifest.json) for the exact contents.

<a id="notable-capabilities"></a>
### ✨ Notable capabilities

- 🛡️ **Defender integration and device risk:** BYOD onboarding and app configuration, Defender app exports, and compliance policies that can consume mobile threat-defense risk signals. Confirm connector setup, licensing, and enrollment compatibility.
- 📱 **Multiple Android management scenarios:** Resources cover Android Enterprise personally owned work profiles, corporate-owned devices, and AOSP scenarios. Confirm each setting and app supports your target enrollment type and device.
- 🔐 **Compliance and app protection:** Android compliance exports cover device health, OS, encryption, password, integrity, and risk settings; the App Protection Policy helps protect organizational data within supported apps.
- 🎯 **Conditional Access and assignment filters:** Android-applicable access policies, supporting groups, and ownership/enrollment filters are included. Review their scope and dependencies carefully and test access with a pilot before enforcement.
- ⚙️ **Device security settings:** Settings Catalog exports include VPN/Common Criteria settings, wipe after ten failed logons, and threat scanning. Verify platform support and user impact before assignment.

---

<a id="documentation"></a>
## 📚 Documentation

| Documentation | Overview |
| --- | --- |
| 🚀 [**General prerequisites**](docs/public/general-prerequisites.md) | Check licensing, permissions, service dependencies, and deployment preparation. |
| 🤖 [**Android prerequisites and Intune settings**](docs/public/android-prerequisites.md) | Prepare Android enrollment, review Intune settings areas, and deploy the exports safely. |
| 📦 [**Android packages**](Android/Full/Config%20overview.md) | Review the Full package scope and deployment notes. |
| 📖 [**Policy naming**](docs/public/policy-naming.md) | Review the naming format and existing exceptions. |
| 🏷️ [**Short-name exceptions**](docs/public/short-name-exceptions.md) | Understand why some exported resources use shorter names. |
| 📂 [**File structure**](docs/public/file-structure.md) | Find package contents and understand the manifests. |
| 📜 [**License**](LICENSE) | Read the repository license. |
