:: ** Gather IMS Logs **

%~dp0
MD LOGS-%COMPUTERNAME%
CD LOGS-%COMPUTERNAME%
WMIC Computersystem get Model /format:list > Info.txt
WMIC CPU get Name, VirtualizationFirmwareEnabled /Format:list >> Info.txt

:: [Common]
robocopy /e C:\_SMSTaskSequence\Logs %~dp0LOGS-%COMPUTERNAME%\_SMSTaskSequence\logs
robocopy C:\Windows\inf %~dp0LOGS-%COMPUTERNAME%\WINDOWS\inf setupapi.app.log
robocopy C:\Windows\inf %~dp0LOGS-%COMPUTERNAME%\WINDOWS\inf setupapi.offline.log
robocopy C:\Windows\inf %~dp0LOGS-%COMPUTERNAME%\WINDOWS\inf setupapi.dev.log
robocopy C:\Windows %~dp0LOGS-%COMPUTERNAME%\WINDOWS setupact.log
robocopy C:\Windows %~dp0LOGS-%COMPUTERNAME%\WINDOWS setuperr.log
robocopy C:\Windows %~dp0LOGS-%COMPUTERNAME%\WINDOWS windowsupdate.log
robocopy C:\Windows\Panther %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Panther setupact.log
robocopy C:\Windows\Panther %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Panther setuperr.log
robocopy C:\Windows\Panther %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Panther unattend.xml
robocopy C:\Windows\Panther\UnattendGC %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Panther\UnattendGC setupact.log
robocopy C:\Windows\Panther\UnattendGC %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Panther\UnattendGC setuperr.log
robocopy C:\Windows\debug %~dp0LOGS-%COMPUTERNAME%\WINDOWS\Debug NetSetup.LOG

::  [CM]
MD SCCM

robocopy /e C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM\CCM\LOGS /xd IMSPRECHK
robocopy /e C:\Windows\CCM\Logs\IMSPRECHK %~dp0LOGS-%COMPUTERNAME%\SCCM\IMSPRECHK
robocopy /e C:\WINDOWS\ccmsetup\logs %~dp0LOGS-%COMPUTERNAME%\SCCM\ccmsetup\logs
robocopy C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM DISMImportCustomDrivers.log
robocopy C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM DISMImportCustomPatches.log
robocopy C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM OSD_CustomDrivers.log
robocopy C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM OSD_CustomPatches.log
robocopy C:\Windows\CCM\Logs %~dp0LOGS-%COMPUTERNAME%\SCCM smsts.log

:: [MDT]
MD MDT

robocopy /e C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT\DeploymentLogs /xd IMSPRECHK
robocopy /e C:\Windows\Temp\IMSPRECHK %~dp0\LOGS-%COMPUTERNAME%\MDT\IMSPRECHK
robocopy C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT DISMImportCustomDrivers.log
robocopy C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT DISMImportCustomPatches.log
robocopy C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT OSD_CustomDrivers.log
robocopy C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT OSD_CustomPatches.log
robocopy C:\Windows\Temp\DeploymentLogs %~dp0\LOGS-%COMPUTERNAME%\MDT smsts.log

