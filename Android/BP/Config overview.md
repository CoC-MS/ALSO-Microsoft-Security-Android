# Config overview - Android - BP

This package contains all policies marked for BP, regardless of Basic or Adv tier.

> [!WARNING]
> Choose one BP or E5 package per platform for a tenant. Do not combine them for the same platform or import either after the whole-build Full package. Microsoft Intune imports can create duplicate policies rather than reconcile packages.

Shared and unclassified resources are intentionally excluded. They are available only in the Full edition.



Workload folders are directly inside this platform package. Shared is separate supporting content, not an additional platform baseline; review dependencies and import only the resources required. Review tenant-specific values, licences, dependencies, and assignments before import. Do not bulk import assignments. Import to a pilot group and validate the outcome before wider deployment.
