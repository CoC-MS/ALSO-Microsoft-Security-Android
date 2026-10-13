# 📂 File structure

[Public documentation](README.md)

This repository contains pre-generated Android policy packages. The workload folders are directly inside each package.

## 📦 Available packages

| Package | Resources in manifest | Scope |
| --- | ---: | --- |
| [`BP`](../../Android/BP/Config%20overview.md) | 13 | Android resources at BP licence classification, with applicable Conditional Access policies and dependencies. |
| [`E5`](../../Android/E5/Config%20overview.md) | 13 | Android resources up to E5 licence classification, with applicable Conditional Access policies and dependencies. |
| [`Full`](../../Android/Full/Config%20overview.md) | 39 | All Android resources, with applicable Conditional Access policies and dependencies. |

Check the selected package's `build-manifest.json` for its exact file list, including the supporting `MigrationTable.json`. The manifest is package metadata, not an Intune policy to import.

> [!WARNING]
> Choose one Android package for a tenant. Do not combine BP, E5, or Full packages, or import Full after another package; overlapping imports can create duplicate policies.

## 🗂️ Full package workloads

The `Full` package currently contains:

| Workload folder | Resources |
| --- | ---: |
| `AppConfigurationManagedDevice` | 1 |
| `Applications` | 5 |
| `AppProtection` | 1 |
| `AssignmentFilters` | 3 |
| `CompliancePolicies` | 16 |
| `ConditionalAccess` | 4 |
| `DeviceConfiguration` | 2 |
| `Groups` | 3 |
| `SettingsCatalog` | 3 |

The Full package also includes `MigrationTable.json`. Workload and resource names can be browsed under [`Android/Full`](../../Android/Full). Review the package overview and manifest before import. The separate `Shared` packages described by the source template are not included in this repository.

See [General prerequisites](general-prerequisites.md), [Android prerequisites](android-prerequisites.md), and [How to import](how-to-import.md) before deployment.
