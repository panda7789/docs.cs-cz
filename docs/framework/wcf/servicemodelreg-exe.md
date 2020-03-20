---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: a6f65ccc6caa0a7e496e7de8c83259ab48903753
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183110"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Nástroj ServiceModel Registration (ServiceModelReg.exe)
Tento nástroj příkazového řádku poskytuje možnost spravovat registraci komponent WCF a WF na jednom počítači. Za normálních okolností byste neměli používat tento nástroj jako WCF a WF komponenty jsou konfigurovány při instalaci. Pokud však dochází k potížím s aktivací služby, můžete se pokusit zaregistrovat součásti pomocí tohoto nástroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Poznámky  
 Nástroj lze nalézt v následujícím umístění:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
> Při spuštění nástroje ServiceModel Registration Tool v systému Windows Vista nemusí dialogové okno **Funkce systému Windows** odrážet, že je zapnuta možnost **aktivace http verze systému Windows Communication Foundation** v rámci rozhraní Microsoft **.NET Framework 3.0.** Dialogové okno **Funkce systému Windows** lze získat klepnutím na tlačítko **Start**, potom klepněte na tlačítko **Spustit** a potom zadáním **příkazu OptionalFeatures**.  
  
 Následující tabulky popisují možnosti, které lze použít s ServiceModelReg.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-ia`|Nainstaluje všechny součásti WCF a WF.|  
|`-ua`|Odinstaluje všechny součásti WCF a WF.|  
|`-r`|Opravuje všechny součásti WCF a WF.|  
|`-i`|Nainstaluje součásti WCF a WF zadané pomocí –c.|  
|`-u`|Odinstaluje součásti WCF a WF zadané pomocí –c.|  
|`-c`|Nainstaluje nebo odinstaluje součást:<br /><br /> - httpnamespace - HTTP Namespace rezervace<br />- tcpportsharing – služba sdílení portů TCP<br />- tcpaktivace – služba aktivace TCP (nepodporovaná na profilu klienta .NET 4)<br />- namedpipeactivation – služba aktivace pojmenovaného kanálu (nepodporovaná na profilu klienta .NET 4<br />- msmqaktivace – služba aktivace služby MSMQ (nepodporovaná na profilu klienta .NET 4<br />- etw - ETW události trasování manifestů (Windows Vista nebo novější)|  
|`-q`|Tichý režim (pouze zobrazení chyby při protokolování)|  
|`-v`|Podrobný režim.|  
|`-nologo`|Potlačí autorská práva a bannerové zprávy.|  
|`-?`|Zobrazí text nápovědy.|  
  
## <a name="fixing-the-fileloadexception-error"></a>Oprava chyby FileLoadException  
 Pokud jste nainstalovali předchozí verze WCF v počítači, může dojít k `FileLoadFoundException` chybě při spuštění nástroje ServiceModelReg zaregistrovat novou instalaci. K tomu může dojít i v případě, že jste ručně odebrali soubory z předchozí instalace, ale ponechali nastavení machine.config beze změny.  
  
 Chybová zpráva je podobná následující.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Z chybové zprávy byste si měli uvědomit, že sestavení System.ServiceModel verze 2.0.0.0 bylo nainstalováno včasnou verzí Verze CTP (Customer Technology Preview). Aktuální verze vydaného sestavení System.ServiceModel je 3.0.0.0. Proto k tomuto problému dochází, pokud chcete nainstalovat oficiální verzi WCF v počítači, kde byla nainstalována časná verze CTP WCF, ale není zcela odinstalována.  
  
 ServiceModelReg.exe nelze vyčistit předchozí verze položky, ani může zaregistrovat nové verze položky. Jediným řešením je ruční úprava souboru machine.config. Tento soubor můžete najít v následujícím umístění.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Pokud používáte WCF v 64bitovém počítači, měli byste také upravit stejný soubor v tomto umístění.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Vyhledejte všechny uzly XML v tomto souboru, které odkazují na "System.ServiceModel, Version=2.0.0.0", odstraňte je a všechny podřízené uzly. Uložte soubor a znovu spusťte serviceModelReg.exe tento problém vyřeší.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ukazují, jak používat nejběžnější možnosti nástroje ServiceModelReg.exe.  
  
```console  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
