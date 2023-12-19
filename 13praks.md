# 13. praktikumi aruanne 

Siin on minu operastioonisüsteemide kursuse kolmeteistkümnenda praktikumi esitus. Aega kulus umb 4-5h ja enda arust sain kõik ilusti tehtud.
Tekkis palju küsimusi vahepeal selle kohta, et mida täpselt küsiti või, millist vastust oodatakse(nt kui palju infot peaks sisaldama protsessori kirjeldus), aga sain vist kõigele ka õigesti vastatud. 
Antud praktikum osutus veidi ajakulukamaks kui algselt ootasin, aga sellegipoolest oli huvitav ja mõnus nokitsemine.
Selle praktikumi raames õppisin Windowsi PowerShelli käske ja võimalusi, praktikumi raames katsetasin uut õpitud ning vastasin ka küsimustele.  <br />


Siin on script: <br />

<pre>
#siin on ette antud funktsioon
function valjasta{
	param ($nr, $param, $sisu)
	$fail = "C:\Users\lhoogand\Desktop\OPS-prax4\OPS13.txt"
	$aeg = Get-Date -Format "HH:mm:ss.fff"
	if($sisu -eq $null){
		$rida = "$nr.	$aeg	${param}:	NULL"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}elseif($sisu.GetType().Name -eq "Object[]"){
		$rida = "$nr.	$aeg	${param}:"
		Write-Output $rida $sisu
		$rida | Out-File -FilePath $fail -Append
		$sisu | Out-File -FilePath $fail -Append
	}else{
		$rida = "$nr.	$aeg	${param}:	$sisu"
		Write-Output $rida
		$rida | Out-File -FilePath $fail -Append
	}
}

[int]$aegA = (Get-Date).Millisecond
Valjasta 0 "ALGUS" ("Aeg: "+(Get-Date -Format "dddd MM/dd/yyyy HH:mm K")+" Teostaja: Liina") 
Valjasta 1 "host" (hostname) 

#kõikide ülesannete puhul püüdsin järgida näidisülesande vormistust ning alguses teha kõik vajalikud muutujad ning hiljem vormistada väljund

#$nr:	ÜL 1
#$param: COMPUTERNAME, PSVersion, Caption
#$sisu:	Masina nimi, PowerShelli versioon ja Windowsi versioon. Kasutasin .PSVersion ja .Captionn.
$masinaNimi = $env:COMPUTERNAME
$powershellVersioon = $PSVersionTable.PSVersion
$windowsVersioon = (Get-CimInstance Win32_OperatingSystem).Captionn 
Valjasta 1 "Üldinfo" "$masinaNimi, PowerShell $powershellVersioon, Windows $windowsVersioon"

#$nr:	ÜL 2
#$param:IPAddress, IPSubnet, DefaultIPGateway, DHCPEnabled, MACAddress
#$sisu:	Võrgu konfiguratsioon, gateway, kas DHCP on lubatud ja MAC-aadress. Osutus keerulisemaks kui ootasin, lõpuks sai foreasch tsükliga tehtud, kuna neid on mitu. Kasutasin Get-WmiObject ja siis noppisin sealt kõik vajaliku.
$networkConfig = Get-WmiObject Win32_NetworkAdapterConfiguration -Filter "IPEnabled='True'"
foreach ($config in $networkConfig) {
    $ipAddress = $config.IPAddress
    $subnetMask = $config.IPSubnet
    $gateway = $config.DefaultIPGateway
    $dhcpEnabled = $config.DHCPEnabled
    $macAddress = $config.MACAddress

    $formattedInfo = "IP-aadress: $($ipAddress -join ', '), Võrgumask: $($subnetMask -join ', '), Gateway: $($gateway -join ', '), DHCP lubatud: $dhcpEnabled, MAC-aadress: $macAddress"
    Valjasta 2 "Võrgu konfiguratsioon" "$formattedInfo"
}

#$nr:	ÜL 3
#$param:Win32_Processor,  Win32_ComputerSystem, Name, TotalPhysicalMemory
#$sisu:	Arvuti protsessori kirjeldus ja põhimälu RAM kogus (loodan et sellest piisab). Leidsin protsessori info Win32_Processor ja RAM suuruse Win32_ComputerSystem. Kui oleks olnud vaja rohkem infot siis oleksin noppinud veel andmeid protsessori kohta samamoodi nagu ma leidsin nende nimed.
$processorInfo = Get-WmiObject Win32_Processor
$computerSystemInfo = Get-WmiObject Win32_ComputerSystem
$protsessorKirjeldus = $processorInfo.Name
$ramKogusGB = [math]::Round($computerSystemInfo.TotalPhysicalMemory / 1GB, 2)
Valjasta 3 "Arvuti protsessor ja RAM" "Protsessor: $protsessorKirjeldus`nRAM: $ramKogusGB GB"

#$nr:	ÜL 4
#$param:Description, DriverVersion, DriverDate, CurrentHorizontalResolution, CurrentVerticalResolution
#$sisu: Graafikakaardi nimi, draiveri versioon, kuupäev ja ekraani lahutus (märksõna VideoController). Leidsin info Win32_VideoController ning Resolutioni joinisin nii horisontaal kui ka vertikaal resolutionist.
$graphicsInfo = Get-WmiObject Win32_VideoController
$graphicsName = $graphicsInfo.Description
$driverVersion = $graphicsInfo.DriverVersion
$driverDate = $graphicsInfo.DriverDate
$screenResolution = $graphicsInfo.CurrentHorizontalResolution, $graphicsInfo.CurrentVerticalResolution -join "x"
Valjasta 4 "Graafikakaardi info" "Nimi: $graphicsName`nDraiveri versioon: $driverVersion`nKuupäev: $driverDate`nEkraani lahutus: $screenResolution"

#$nr:	ÜL 5
#$param:Win32_DiskDrive, Partitions, Win32_LogicalDisk, FreeSpace, DeviceID
#$sisu:Arvuti kõvaketaste informatsioon. Leidsin info Win32_DiskDrive ning kasutasin foreach tsüklit et noppida kõigist Partitions, Capacity(muutsin et oleks GB), ning vabamahu(samuti muutsin GB-ks).
$hardDriveInfo = Get-WmiObject Win32_DiskDrive
foreach ($drive in $hardDriveInfo) {
    $partitionStyle = $drive.Partitions | ForEach-Object { $_.PartitionStyle }
    $totalCapacityGB = [math]::Round($drive.Size / 1GB, 2)
    $cDriveFreeSpaceGB = Get-WmiObject Win32_LogicalDisk | Where-Object { $_.DeviceID -eq 'C:' } | ForEach-Object { [math]::Round($_.FreeSpace / 1GB, 2) }
    Valjasta 5 "Kõvaketaste info" "Partitsioonitabel: $partitionStyle`nMahutavus: ${totalCapacityGB}GB`nVaba ruum C:-kettal: ${cDriveFreeSpaceGB}GB"
}

#$nr:	ÜL 6
#$param: Description, Manufacturer, DriverVersion, Win32_PnpSignedDriver, DeviceID
#$sisu: PCI-siinil olevate seadmete draiverite info. Leidsin käsu PDF-ist ning sealt noppisin vajaliku foreach tsükliga.
$pciDevices = Get-WmiObject –Class Win32_PnpSignedDriver | Where-Object {$_.DeviceID –like „PCI*“}
foreach ($device in $pciDevices) {
    $description = $device.Description
    $manufacturer = $device.Manufacturer
    $version = $device.DriverVersion
    Valjasta 6 "PCI-siinil olevate seadmete draiver" "Kirjeldus: $description`nTootja: $manufacturer`nVersioon: $version"
}

#$nr:	ÜL 7
#$param:Win32_UserAccount, Name, Description, LocalAccount, Disabled
#$sisu:Arvutis olevad kasutajad. Leidsin info Win32_UserAccount ja noppisin foreach tsükliga vajaliku.
$users = Get-WmiObject Win32_UserAccount
foreach ($user in $users) {
    $name = $user.Name
    $description = $user.Description
    $isLocalAccount = $user.LocalAccount
    $isDisabled = $user.Disabled
    Valjasta 7 "Arvutis olev kasutaja" "Nimi: $name`nKirjeldus: $description`nLokaalne kasutaja: $isLocalAccount`nKeelatud: $isDisabled"
}

#$nr:	ÜL 8
#$param:Count
#$sisu:Käimasolevate protsesside arv. See oli lihtne, tuli kasutada counti.
$processCount = (Get-Process).Count
Valjasta 8 "Käimasolevate protsesside arv" $processCount

#$nr:	ÜL 9
#$param:, name, Id, starttime, -First 10
#$sisu:10 viimasena käivitatud protsessi. Nõudis veidi nuputamist, aga sai ilusti tehtud, alguses vaatlesin kõiki protsesse, siis valisin nende lahtriteks nime, id (ehk PID) ja algusaja , sordib algusaja põhiselt ning väljastab esimesed 10 ehk varaseimad.
$recentProcesses = Get-Process | select name, Id, starttime | Select-Object -First 10 | Sort-Object starttime
Valjasta 9 "Viimati käivitatud 10 protsessi" $recentProcesses

#$nr:	ÜL 10
#$param: puudub
#$sisu:Kuupäev ja kellaaeg. Get-Date andis kõik vajaliku.
$dateandtime = Get-Date
Valjasta 10 "Kuupäev ja kellaaeg" $dateandtime


[int]$aegL = (Get-Date).Millisecond
$ajakulu = ($aegL - $aegA)

Valjasta "*" "TEHTUD" "$ajakulu`n`n"

<pre>
