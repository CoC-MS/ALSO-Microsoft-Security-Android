# Config overview - Android - Full

This package contains all resources classified as Android, for every tier and licence.

> [!WARNING]
> Choose one package per platform for a tenant. Do not combine Basic, Adv, or Full packages for the same platform, and do not import Full after another package. Microsoft Intune imports can create duplicate policies rather than reconcile packages.

This edition includes resources without tier and licence markers. Cross-platform and tenant-wide resources are kept separately in Shared/Full.



Workload folders are directly inside this package. Shared/Full is separate supporting content, not an additional platform baseline; review dependencies and import only the resources required. Review tenant-specific values, licences, dependencies, and assignments before import. Do not bulk import assignments. Import to a pilot group and validate the outcome before wider deployment.
