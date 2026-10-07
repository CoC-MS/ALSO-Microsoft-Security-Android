# 📥 How to import

[Public documentation](README.md)

Complete the [Prerequisites](prerequisites.md) and review [File structure](file-structure.md) before importing.

This repository follows the source template's workflow using the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement). Follow the tool's current setup and authentication instructions.

1. Download and extract this repository and the Intune Management Tool.
2. Sign in to the intended Microsoft Intune tenant with an account that has the required permissions. Confirm the tenant before making changes.
3. Choose one package under `Android` and review its `Config overview.md` and `build-manifest.json`.
4. Import only the required JSON resources from the package's workload folders. The manifest is metadata, not a policy to import. Review and import required app and assignment-filter dependencies before policies that reference them.
5. Inspect imported resources in Intune. Update tenant-specific values, applications, groups, filters, and scope as needed.
6. Assign reviewed policies to a pilot group, validate deployment and user impact, then expand in stages.

> [!WARNING]
> Do not combine Android packages or bulk-import assignments. Review tenant-specific values, dependencies, and any security controls with user impact before assignment.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
