# 1. Locate every single graphics driver device instance folder inside the registry
$Paths = Get-ChildItem -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}" -Name

# 2. Loop through every folder and force-rename the display driver descriptions
foreach ($P in $Paths) {
    if ($P -match '^\d{4}$') {
        Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\$P" -Name "DriverDesc" -Value "NVIDIA Video Framebuffer" -ErrorAction SilentlyContinue
    }
}

Write-Host "All virtual display adapters successfully renamed to NVIDIA variables!" -ForegroundColor Green
