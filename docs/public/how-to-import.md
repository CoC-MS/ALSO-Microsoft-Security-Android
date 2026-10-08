# 📥 How to import

[Public documentation](README.md)

Complete the [General prerequisites](general-prerequisites.md) and [Android prerequisites](android-prerequisites.md), then review [File structure](file-structure.md) before importing.

This repository follows the source template's workflow using the [Micke M Intune Management Tool](https://github.com/Micke-K/IntuneManagement). Follow the tool's current setup and authentication instructions.

## Download and extract

> [!IMPORTANT]
> **Unzip the downloaded files into your OneDrive folder.** Windows File Explorer can fail to extract the long filenames and paths in these exports. Keep the destination path short (for example, a folder named `Android` directly under OneDrive). OneDrive does not remove Windows path limits; if Explorer still fails, use an extraction tool that supports long paths.

1. Download this repository using **Code > Download ZIP**, then extract it into your OneDrive folder.

   ![GitHub Code menu showing Download ZIP](https://github.com/user-attachments/assets/b4005205-abc8-4e9b-a8b0-d6f919f99c06)

2. Download and extract the [Intune Management Tool](https://github.com/Micke-K/IntuneManagement). On Windows, launch `Start.cmd` from the extracted tool folder, following the tool's current setup instructions.

   ![Start.cmd in the extracted Intune Management Tool folder](https://github.com/user-attachments/assets/ae7405c2-17cb-43a1-a96e-cd60181a2619)

## Sign in and import

The screenshots below come from the [Conditional Access repository's import guide](https://github.com/CoC-MS/ALSO-Microsoft-Security-Conditional-Access#how-to-import). They illustrate the shared tool workflow; select the Android resource types described here, not the Conditional Access resource types in that guide. The interface may differ in newer tool versions.

1. The command window and tool UI will open. Use the icon in the upper-right corner to sign in to the intended Microsoft Intune tenant with an account that has the required permissions. Confirm the tenant before making changes.

   ![Intune Management Tool interface with the sign-in icon in the upper-right corner](https://github.com/user-attachments/assets/2e835f79-5e07-4c7d-bd7c-5bd4976fde50)

2. If the tool requires API permission consent, have an administrator authorized to grant tenant-wide consent review the requested permissions. After sign-in, use the same icon and select **Request Consent** if needed.

   ![Account menu showing Request Consent](https://github.com/user-attachments/assets/675ebdc9-dc87-4633-bfa5-fbb92f7ba53d)

3. Choose one package under `Android` and review its `Config overview.md` and `build-manifest.json`.
4. Open **Bulk > Import** in the upper-left corner of the tool.

   ![Bulk menu showing the Import action](https://github.com/user-attachments/assets/9e8b32ce-93fe-4ef8-9c19-325d138add8c)

5. Select the chosen package's folder and only the required Android resource types from its workload folders. Import only the required JSON resources; the manifest is metadata, not a policy to import. Review and import required app and assignment-filter dependencies before policies that reference them. Leave assignment import disabled.
6. Inspect imported resources in Intune and review errors in the tool's command window. Update tenant-specific values, applications, groups, filters, and scope as needed.
7. Assign reviewed policies to a pilot group, validate deployment and user impact, then expand in stages.

> [!WARNING]
> Do not combine Android packages or bulk-import assignments. Review tenant-specific values, dependencies, and any security controls with user impact before assignment.

For import problems or documentation corrections, see [Reporting issues](reporting-issues.md).
