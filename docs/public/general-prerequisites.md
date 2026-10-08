# 🚀 General prerequisites

[Public documentation](README.md)

Check these items before importing Android resources into Microsoft Intune.

> [!IMPORTANT]
> Confirm the target tenant and review each resource before import. Package names and policy names do not replace checking the licensing and service requirements for the individual settings.

---

## 🔐 Licensing and platform

The repository provides `BP`, `E3-E5`, and `E5` Basic packages, plus matching Adv package names. Check the required licences and service availability for the policies you intend to use.

Identify the target Android management scenario: Android Enterprise, personally owned work profile (BYOD), or AOSP. Confirm that each selected setting supports the target enrollment type and operating-system version.

## 🧰 Access and dependencies

Use an account with the Intune permissions needed to import and manage the selected resources. Follow your organization's approval process for any consent requested by an import tool.

Review each policy's description, settings, references, and assignments. Prepare tenant-specific application, group, filter, and service dependencies where the policy requires them. For app resources, confirm the relevant Android app deployment and Managed Google Play setup in the target tenant.

## 🧪 Deployment readiness

Choose one package for the Android platform. Prepare a pilot group and a way to validate deployment results and user impact before expanding assignments.

See [File structure](file-structure.md) to compare package contents and [How to import](how-to-import.md) for the import sequence.
