# Microsoft Azure CLI cheat sheet

Concise set of quick-reference notes relates to [Microsoft Azure CLI][AZ-DOCS].

---
**Context**

Below cheat sheet was created in following context.

|           |                           |
|-----------|---------------------------|
| **OS**    | [Windows 11][WIN-11-DOCS] |
| **shell** | [PowerShell 7.3][PS-DOCS] |

---

| Action                      | Command                                                 |
|-----------------------------|---------------------------------------------------------|
| installation                | `winget install -e --id Microsoft.AzureCLI`             |
| list regions                | `az account list-locations -o table`                    |
| register resource providers | `az provider register --namespace 'microsoft.insights'` |

[AZ-DOCS]: https://learn.microsoft.com/en-us/cli/azure/
[WIN-11-DOCS]: https://learn.microsoft.com/en-us/windows/whats-new/windows-11-overview
[PS-DOCS]: https://learn.microsoft.com/en-us/powershell/scripting/overview?view=powershell-7.3
