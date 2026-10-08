# 🤖 ALSO Microsoft Security - Android

> Microsoft Intune security policy exports for Android Enterprise, personally owned work profiles (BYOD), AOSP, app protection, and Microsoft Defender.

> [!IMPORTANT]
> These exports are starting points, not ready-made tenant configurations. Review licensing, settings, tenant-specific values, dependencies, and assignments; pilot policies before expanding deployment.

| Resource | Description |
| --- | --- |
| 📦 **[Android packages](Android/Full/Config%20overview.md)** | Compare package scope and review package manifests. |
| 🚀 **[General prerequisites](docs/public/general-prerequisites.md)** | Check the existing licensing, permissions, and deployment preparation. |
| 🤖 **[Android prerequisites](docs/public/android-prerequisites.md)** | Android enrollment, Intune settings, and deployment guidance. |
| 📖 **[Policy naming](docs/public/policy-naming.md)** | Review the naming format and existing exceptions. |
| 📂 **[File structure](docs/public/file-structure.md)** | Find the package contents and understand the manifests. |
| 📥 **[How to import](docs/public/how-to-import.md)** | Review and import selected Android exports. |
| 🐛 **[Reporting issues](docs/public/reporting-issues.md)** | Report problems without disclosing tenant information. |
| 📜 **[License](LICENSE)** | Read the repository license. |

---

## 📦 Android configuration packages

These are pre-generated policy exports, not an Android application or a build tool. Each package includes a `Config overview.md` and a `build-manifest.json` listing its exported resources. The manifest's file paths are relative to that package.

| Package | Licence scope | Edition | Exported files |
| --- | --- | --- | ---: |
| [BP-Basic](Android/BP-Basic/Config%20overview.md) | 🏷️ **BP** | Basic | 5 |
| [E3-E5-Basic](Android/E3-E5-Basic/Config%20overview.md) | 🏷️ **E3-E5** | Basic | 5 |
| [E5-Basic](Android/E5-Basic/Config%20overview.md) | 🏷️ **E5** | Basic | 5 |
| [BP-Adv](Android/BP-Adv/Config%20overview.md) | 🏷️ **BP** | Adv | 0 |
| [E3-E5-Adv](Android/E3-E5-Adv/Config%20overview.md) | 🏷️ **E3-E5** | Adv | 0 |
| [E5-Adv](Android/E5-Adv/Config%20overview.md) | 🏷️ **E5** | Adv | 0 |
| [Full](Android/Full/Config%20overview.md) | 🏷️ **All** | Full | 31 |

The three Basic packages currently contain the same five policy exports. The Adv packages have no policy exports. Licence builds are cumulative: E3-E5 includes BP, and E5 includes BP and E3-E5. Basic and Adv are separate editions; Adv is not an additional layer on top of Basic.

> [!WARNING]
> Choose one Android package per tenant. Do not combine Basic, Adv, and Full packages or import Full after another package; Intune imports can create duplicate policies rather than reconcile packages. Full contains all Android resources in this repository, not a guarantee that every resource is suitable for every tenant, enrollment mode, or licence.

Cross-platform and tenant-wide supporting content is not included in this repository. Review dependencies and import only the resources required by the selected policies.

## 🌐 Android coverage

The Full package contains these workload folders. Availability and suitability depend on the policy, device enrollment mode, and tenant configuration.

| Workload | Resources | Included content |
| --- | ---: | --- |
| `AppConfigurationManagedDevice` | 1 | Microsoft Defender managed app configuration for Android BYOD. |
| `Applications` | 5 | Managed Home Screen, Microsoft Authenticator, Microsoft Defender Antivirus, Microsoft Intune, and Microsoft Outlook app exports. |
| `AppProtection` | 1 | Android App Protection Policy. |
| `AssignmentFilters` | 3 | Android Enterprise targeting and corporate/personal ownership filters. |
| `CompliancePolicies` | 16 | Android Enterprise, BYOD, and AOSP health, OS version, encryption, password, integrity, and Defender-risk policies, plus other Android compliance exports. |
| `DeviceConfiguration` | 2 | Corporate Android configuration and BYOD automatic enrollment to Microsoft Defender for Endpoint. |
| `SettingsCatalog` | 3 | Android VPN/Common Criteria settings, wipe after ten failed logons, and threat scanning. |

Notable capabilities include Defender integration for BYOD and device risk, Android Enterprise/BYOD/AOSP compliance policies, app protection and ownership-based assignment filters, and Settings Catalog security controls.

---

## 🛠️ Manage Android in Intune

Before importing policies, set up the Android management method that matches the devices:

1. Prepare Intune users, groups, licences, and MDM authority.
2. Connect Android Enterprise to Managed Google Play; use the separate AOSP flow for supported devices without Google Mobile Services.
3. Choose the enrollment type: BYOD work profile, corporate-owned work profile, fully managed, dedicated/kiosk, or AOSP.
4. Configure enrollment restrictions/profiles, device configuration, compliance, app deployment, app protection, and any Defender integration required by the scenario.
5. Assign to pilot users or devices, verify enrollment and policy outcomes, then enforce Microsoft Entra Conditional Access and expand gradually.

Android options vary by enrollment type and device. The [Android prerequisites and Intune settings guide](docs/public/android-prerequisites.md) explains the setup, main Intune settings areas, enrollment choices, and deployment checks. It also links to Microsoft's current Android settings references; consult those for the complete and changing catalog of supported settings.

Start with [General prerequisites](docs/public/general-prerequisites.md), then choose one package using [File structure](docs/public/file-structure.md) and follow [How to import](docs/public/how-to-import.md).
