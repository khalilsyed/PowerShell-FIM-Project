# PowerShell-FIM-Project
  [File Integrity Monitoring with PowerShell]

## Overview

This project demonstrates a simple File Integrity Monitoring (FIM) system using PowerShell. It provides the ability to collect a new baseline of file hashes and continuously monitor files for changes, notifying users of any alterations.

## PowerShell Functions

```powershell
Function Calculate-File-Hash($filepath) {
    # Function to calculate the hash of a file
    $filehash = Get-FileHash -Path $filepath -Algorithm SHA512
    return $filehash
}

Function Erase-Baseline-If-Already-Exists() {
    # Function to delete the baseline file if it already exists
    $baselineExists = Test-Path -Path .\baseline.txt

    if ($baselineExists) {
        Remove-Item -Path .\baseline.txt
    }
}
