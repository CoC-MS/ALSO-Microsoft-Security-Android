# 📖 Policy naming

[Public documentation](README.md)

The source template's common policy naming format is:

```text
<Licence> - <Company> - <Impact> - <Tier> - <Version> - <Platform> - <Category> - <Policy purpose> - <Scope>
```

## Naming components

| Component | Description | Examples |
| --- | --- | --- |
| `Licence` | Licence classification | `BP`, `E3-E5`, `E5` |
| `Company` | Template provider | `ALSO` |
| `Impact` | Expected implementation impact | `LI`, `MI`, `HI` |
| `Tier` | Baseline tier | `Basic`, `Adv` |
| `Version` | Policy version when present | `v1.0` |
| `Platform` | Target platform or enrollment scenario | `Android`, `Android (BYOD)` |
| `Category` | Intune or security area | `Device Restriction` |
| `Policy purpose` | What the policy configures | `Threat Scan` |
| `Scope` | Assignment scope when present | `D` (device), `U` (user) |

Use ` - ` as the separator for new names; do not use `/` in Intune policy names. Names in this repository are copied exports and have not been normalized. See [Short-name exceptions](short-name-exceptions.md) for current examples.

> [!NOTE]
> The exported names and filenames are not a substitute for reviewing a resource's settings, description, licensing, and intended enrollment scenario.
