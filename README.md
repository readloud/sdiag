# sdiag.ps1 🛠️

**PowerShell Security Diagnostics & Enumeration Tool**

`sdiag` is a specialized PowerShell script designed for rapid system diagnostics, security configuration auditing, and local enumeration. It is built to be "living off the land," requiring minimal dependencies to provide a comprehensive snapshot of a Windows host's security posture.

## ✨ Key Features

* **Privilege Audit:** Checks current user rights, SID information, and UAC configuration.
* **Network Mapping:** Enumerates listening ports, active connections, and DNS cache.
* **Security Software Discovery:** Identifies installed Antivirus, EDR, and Firewall status.
* **Patch Analysis:** Lists installed Hotfixes and identifies missing security updates (where possible).
* **Credential/Secret Hunting:** Scans for common misconfigurations in the registry and environment variables.

## 🚀 Getting Started

### Prerequisites

* **PowerShell 5.1+** (Compatible with PowerShell Core/7)
* Administrative privileges are recommended for a full diagnostic, but the script runs in "Low Integrity" mode with reduced output.

### Quick Execution

To run the script directly from the web (not recommended for sensitive environments):

```powershell
iex (New-Object Net.WebClient).DownloadString('https://raw.githubusercontent.com/readloud/sdiag/main/sdiag.ps1')

```

### Manual Installation

```powershell
git clone https://github.com/readloud/sdiag.git
cd sdiag
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
.\sdiag.ps1

```

## 🛠 Usage

**Run all standard diagnostics:**

```powershell
.\sdiag.ps1 -All

```

**Run specific modules:**

```powershell
.\sdiag.ps1 -Module Network,Users

```

**Export findings to a report:**

```powershell
.\sdiag.ps1 -OutReport .\host_audit.txt

```

### Parameters

| Parameter | Description |
| --- | --- |
| `-All` | Runs every available diagnostic module. |
| `-Module` | Specifies a comma-separated list of modules (e.g., `Registry`, `Services`). |
| `-Quick` | Performs a high-level scan optimized for speed. |
| `-NoColor` | Disables ANSI color output for clean logging. |

## 📂 Structure

* `sdiag.ps1`: The primary script containing the logic and module definitions.
* `Modules/`: (Optional) External helper scripts for complex checks.
* `Reports/`: Default directory for saved diagnostic output.

## 🤝 Contributing

1. Fork the repo.
2. Create a feature branch (`git checkout -b feature/NewCheck`).
3. Ensure your code follows the [PowerShell Practice and Style Guide](https://poshcode.gitbook.io/powershell-practice-and-style/).
4. Submit a Pull Request.

## ⚠️ Disclaimer

*This tool is intended for authorized security testing and administrative diagnostics only. Using this script against systems you do not have explicit permission to test is illegal and unethical.*
