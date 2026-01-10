# Intune network drive mapping generator

> **Note:** This is a fork of [nicolonsky's IntuneDriveMapping](https://github.com/nicolonsky/IntuneDriveMapping) project. This fork focuses on providing VBScript alternatives for network drive mapping in modern Intune environments. Credit to the original author for the foundational work.

* Generate Intune PowerShell scripts to map network drives on Entra ID joined devices
* Seamlessly migrate existing network drive mapping group policies
* Generate a network drive mapping configuration from scratch
* Supports security group filtering (with nested groups)
* Supports recurring execution on clients
* **Requires Windows 11** for silent execution using `conhost.exe --headless`

For additional context and troubleshooting, refer to the [original project's wiki](https://github.com/nicolonsky/IntuneDriveMapping/wiki#troubleshooting) and [blog post](https://tech.nicolonsky.ch/next-level-network-drive-mapping-with-intune/) by nicolonsky.

![image](https://user-images.githubusercontent.com/32899754/88693062-21c4b980-d0ff-11ea-8e5e-adbc655fe0e6.png)
