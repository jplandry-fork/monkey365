<p align="center">
  <img src="https://user-images.githubusercontent.com/5271640/181045413-1d17333c-0533-404a-91be-2070ccc6ee29.png" width="300" height="300" />
</p>

<p align="center">
  <a href="https://github.com/silverhack/monkey365/releases"><img src="https://img.shields.io/github/v/release/silverhack/monkey365?display_name=tag&sort=semver" alt="GitHub release"></a>
  <a href="https://www.powershellgallery.com/packages/monkey365/"><img src="https://img.shields.io/powershellgallery/v/monkey365" alt="PowerShell Gallery"></a>
  <a href="https://github.com/silverhack/monkey365/stargazers"><img src="https://img.shields.io/github/stars/silverhack/monkey365?style=social" alt="Stars"></a>
  <a href="https://twitter.com/tr1ana"><img src="https://img.shields.io/twitter/follow/tr1ana?style=social" alt="Follow @tr1ana"></a>
</p>

<p align="center">
  <a href="https://github.com/silverhack/monkey365/issues"><img alt="Issues" src="https://img.shields.io/github/issues/silverhack/monkey365"></a>
  <a href="https://github.com/silverhack/monkey365/blob/main/LICENSE"><img src="https://img.shields.io/github/license/silverhack/monkey365" alt="License"></a>
</p>

<p align="center">
  <a href="https://github.com/silverhack/monkey365/releases"><img src="https://img.shields.io/github/downloads/silverhack/monkey365/total?style=flat&logo=powershell&label=GitHub%20Release%20Download" alt="GitHub Downloads"></a>
  <a href="https://www.powershellgallery.com/packages/monkey365"><img src="https://img.shields.io/powershellgallery/dt/monkey365.svg?style=flat&logo=powershell&label=PSGallery%20Download" alt="PowerShell Gallery Downloads"></a>
</p>

Monkey365 is an open-source security assessment tool for Microsoft 365, Azure, and Microsoft Entra ID. It helps administrators, consultants, and security professionals identify misconfigurations, review cloud security posture, and evaluate environments against industry security best practices and compliance standards.

Monkey365 is designed to simplify Microsoft cloud security assessments without requiring users to learn complex APIs or navigate multiple administration portals.

---

# Features

- Self-contained PowerShell module with bundled dependencies
- No external module installation required
- No additional Microsoft PowerShell modules required
- Security posture assessment for Microsoft 365, Azure, and Microsoft Entra ID
- CIS benchmark and compliance checks
- HTML, JSON, and CSV reporting
- Support for Azure Public, China, and Government cloud environments
- Collector-based and extensible architecture
- Easy deployment across workstations, jump boxes, and assessment environments

---

# Quick Start

Install Monkey365 from the PowerShell Gallery:

```powershell
Install-Module -Name monkey365 -Scope CurrentUser
```

Import the module:

```powershell
Import-Module monkey365
```

Run a basic assessment:

```powershell
$options = @{
    Instance = 'Microsoft365';
    Collect = 'SharePointOnline';
    PromptBehavior = 'SelectAccount';
    IncludeEntraID = $true;
    ExportTo = 'HTML';
}
$assets = Invoke-Monkey365 @options
```

Get available options and examples:

```powershell
Get-Help Invoke-Monkey365 -Detailed
```

---

# Introduction

Monkey365 is a collector-based PowerShell module used to review the security posture of cloud environments. It scans Microsoft 365, Azure, and Microsoft Entra ID for potential security issues, configuration weaknesses, and deviations from security best practices.

The tool provides recommendations to help organizations strengthen their cloud security posture and improve compliance readiness.

---

# Installation

## PowerShell Gallery

Install the latest stable version:

```powershell
Install-Module -Name monkey365 -Scope CurrentUser
```

Install the latest prerelease version:

```powershell
Install-Module -Name monkey365 -Scope CurrentUser -AllowPrerelease
```

Update Monkey365:

```powershell
Update-Module -Name monkey365 -Scope CurrentUser
```

Force reinstall Monkey365:

```powershell
Install-Module -Name monkey365 -Scope CurrentUser -Force
```

> [!NOTE]
> Monkey365 is distributed as a self-contained PowerShell module and includes all required dependencies. No additional Microsoft PowerShell modules are required.

## GitHub Releases

Download the latest release from the following page:

https://github.com/silverhack/monkey365/releases

After downloading the release package, extract the archive to a suitable directory.

Use the PowerShell `Unblock-File` cmdlet to unblock extracted files if required:

```powershell
Get-ChildItem -Recurse C:\monkey365 | Unblock-File
```

Import the module:

```powershell
Import-Module monkey365
```

If Monkey365 is not located in a `PSModulePath` directory, import it using an explicit path:

```powershell
Import-Module C:\temp\monkey365
```

Reimport the module into the current PowerShell session:

```powershell
Import-Module C:\temp\monkey365 -Force
```

---

# Basic Usage

Display available command options:

```powershell
Get-Help Invoke-Monkey365
```

Display usage examples:

```powershell
Get-Help Invoke-Monkey365 -Examples
```

Display detailed help information:

```powershell
Get-Help Invoke-Monkey365 -Detailed
```

Example assessment:

```powershell
$options = @{
    Instance        = 'Microsoft365'
    Collect         = 'ExchangeOnline'
    PromptBehavior  = 'SelectAccount'
    IncludeEntraID  = $true
    ExportTo        = 'HTML'
}

Invoke-Monkey365 @options
```

If credentials are not supplied, Monkey365 prompts for authentication.

---

# Running Monkey365 in National or Government Cloud Environments

Use the `-Environment` parameter with `Invoke-Monkey365` to specify the target cloud environment.

Supported environments:

- `AzurePublic` (default)
- `AzureChina`
- `AzureUSGovernment`

Example:

```powershell
$options = @{
    Environment     = 'AzureUSGovernment'
    Instance        = 'Microsoft365'
    Collect         = @('ExchangeOnline', 'SharePointOnline')
    PromptBehavior  = 'SelectAccount'
    IncludeEntraID  = $true
    ExportTo        = @('JSON', 'HTML')
}

Invoke-Monkey365 @options
```

---

# Regulatory Compliance Checks

Monkey365 helps streamline Microsoft 365, Azure, and Microsoft Entra ID security reviews through hundreds of built-in checks aligned with industry security best practices.

The tool helps consultants, administrators, and security teams identify security gaps, validate tenant configurations, and assess risk exposure across cloud environments.

Assessment reports include structured and actionable data for rapid analysis and verification.

<p align="center">
  <img src="https://silverhack.github.io/monkey365/assets/images/htmlreport.png" />
</p>

---

# Supported Standards

By default, the HTML report displays CIS (Center for Internet Security) benchmark mappings for Microsoft Azure and Microsoft 365 environments.

Currently supported standards include:

- CIS Microsoft Azure Foundations Benchmark v3.0.0
- CIS Microsoft Azure Database Services Benchmark v2.0.0
- CIS Microsoft Azure Compute Services Benchmark v2.0.0
- CIS Microsoft 365 Foundations Benchmark v3.0.0
- CIS Microsoft 365 Foundations Benchmark v4.0.0
- CIS Microsoft 365 Foundations Benchmark v5.0.0

Additional standards and frameworks may be added in future releases, including:

- NIST
- HIPAA
- GDPR
- PCI-DSS

---

# Documentation

Detailed installation guides, advanced usage examples, configuration references, and additional documentation are available at:

https://silverhack.github.io/monkey365/

---

> [!TIP]
> **Give us a Star!** If you find Monkey365 useful, please consider starring the repository on GitHub. It helps improve visibility and supports ongoing development.

---

# Star History

<a href="https://www.star-history.com/#silverhack/monkey365&type=date&legend=top-left">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=silverhack/monkey365&type=date&theme=dark&legend=top-left" />
    <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=silverhack/monkey365&type=date&legend=top-left" />
    <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=silverhack/monkey365&type=date&legend=top-left" />
  </picture>
</a>
