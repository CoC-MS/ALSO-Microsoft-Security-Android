# 📂 File structure

[Public documentation](README.md)

This repository contains pre-generated Android policy packages. The workload folders are directly inside each package.

## 📦 Available packages

| Package | Resources in manifest | Scope |
| --- | ---: | --- |
| [`BP-Basic`](../../Android/BP-Basic/Config%20overview.md) | 5 | Basic package at BP licence classification. |
| [`E3-E5-Basic`](../../Android/E3-E5-Basic/Config%20overview.md) | 5 | Basic package at E3-E5 licence classification. |
| [`E5-Basic`](../../Android/E5-Basic/Config%20overview.md) | 5 | Basic package at E5 licence classification. |
| [`BP-Adv`](../../Android/BP-Adv/Config%20overview.md) | 0 | Overview and manifest only; no resources are currently listed. |
| [`E3-E5-Adv`](../../Android/E3-E5-Adv/Config%20overview.md) | 0 | Overview and manifest only; no resources are currently listed. |
| [`E5-Adv`](../../Android/E5-Adv/Config%20overview.md) | 0 | Overview and manifest only; no resources are currently listed. |
| [`Full`](../../Android/Full/Config%20overview.md) | 31 | All Android resources in this repository's Full package. |

The three Basic package manifests each list the same five policy exports. Check the selected package's `build-manifest.json` for its exact file list. The manifest is package metadata, not an Intune policy to import.

> [!WARNING]
> Choose one Android package for a tenant. Do not combine Basic, Adv, or Full packages, or import Full after another package; overlapping imports can create duplicate policies.

## 🗂️ Full package workloads

The `Full` package currently contains:

| Workload folder | Resources |
| --- | ---: |
| `AppConfigurationManagedDevice` | 1 |
| `Applications` | 5 |
| `AppProtection` | 1 |
| `AssignmentFilters` | 3 |
| `CompliancePolicies` | 16 |
| `DeviceConfiguration` | 2 |
| `SettingsCatalog` | 3 |

Workload and resource names can be browsed under [`Android/Full`](../../Android/Full). Review the package overview and manifest before import. The separate cross-platform and tenant-wide `Shared` resources described by the source template are not included in this repository.

See [General prerequisites](general-prerequisites.md), [Android prerequisites](android-prerequisites.md), and [How to import](how-to-import.md) before deployment.
