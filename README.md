:: Kill any background Roblox processes
taskkill /F /IM RobloxPlayerBeta.exe /T 2>nul

:: Purge the local application data caches and log repositories
rmdir /s /q "%localappdata%\Roblox"
rmdir /s /q "%localappdata%\Temp\Roblox"

:: Clear out the main web storage cache used by Hyperion
rmdir /s /q "%userprofile%\AppData\LocalLow\Roblox"
