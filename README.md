# 1. Mask the driver description key inside the VM's graphics class
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0000" -Name "DriverDesc" -Value "NVIDIA Video Controller"

# 2. Clear out any secondary synthetic framebuffer registry tags
Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0001" -Name "DriverDesc" -Value "NVIDIA Secondary display" -ErrorAction SilentlyContinue

Write-Host "Registry masking complete! The words 'Hyper-V Video' are now completely hidden." -ForegroundColor Green
