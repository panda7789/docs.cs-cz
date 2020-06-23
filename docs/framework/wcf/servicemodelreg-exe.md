---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
description: Pomocí tohoto nástroje příkazového řádku můžete spravovat registraci komponent WCF a WF na jednom počítači, pokud dojde k potížím s aktivací služby.
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 347b1b8071abe7d8eb7e16ffd879c1fdb9825bc7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245892"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Nástroj ServiceModel Registration (ServiceModelReg.exe)
Tento nástroj příkazového řádku poskytuje možnost spravovat registraci komponent WCF a WF na jednom počítači. Za normálních okolností byste neměli tento nástroj používat, protože komponenty technologie WCF a WF se nakonfigurují po instalaci. Pokud ale máte problémy s aktivací služby, můžete se pokusit zaregistrovat komponenty pomocí tohoto nástroje.  
  
## <a name="syntax"></a>Syntax  
  
```console  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Poznámky  
 Nástroj najdete v následujícím umístění:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation \  
  
> [!NOTE]
> Když se nástroj pro registraci ServiceModel v systému Windows Vista spustí, dialog **funkcí Windows** se nemusí projevit, protože je zapnutá možnost **Windows Communication Foundation aktivace protokolem HTTP** pod **Microsoft .NET Framework 3,0** . K dialogovému oknu **funkcí Windows** se dostanete tak, že kliknete na **Start**, pak na **Spustit** a pak zadáte **optionalfeatures**.  
  
 V následujících tabulkách jsou popsány možnosti, které lze použít s ServiceModelReg.exe.  
  
|Možnost|Description|  
|------------|-----------------|  
|`-ia`|Nainstaluje všechny součásti WCF a WF.|  
|`-ua`|Odinstaluje všechny součásti WCF a WF.|  
|`-r`|Opraví všechny součásti WCF a WF.|  
|`-i`|Nainstaluje WCF a součásti WF zadané pomocí – c.|  
|`-u`|Odinstaluje komponenty WCF a WF zadané pomocí – c.|  
|`-c`|Nainstaluje nebo odinstaluje součást:<br /><br /> -httpnamespace – rezervace oboru názvů HTTP<br />-tcpportsharing – služba sdílení portů TCP<br />-tcpactivation – aktivační služba TCP (nepodporovaná v profilu klienta .NET 4)<br />-namedpipeactivation – aktivační služba pojmenovaného kanálu (nepodporovaná v profilu klienta .NET 4<br />-Služba MsmqActivation – aktivační služba MSMQ (nepodporovaná v profilu klienta .NET 4<br />-ETW – manifesty trasování událostí ETW (Windows Vista nebo novější)|  
|`-q`|Tichý režim (zobrazí se pouze protokolování chyb)|  
|`-v`|Podrobný režim.|  
|`-nologo`|Potlačí zprávu o autorských právech a bannerech.|  
|`-?`|Zobrazí text v nápovědě.|  
  
## <a name="fixing-the-fileloadexception-error"></a>Oprava chyby FileLoadException  
 Pokud jste na svém počítači nainstalovali předchozí verze služby WCF, může se `FileLoadFoundException` při spuštění nástroje ServiceModelReg k registraci nové instalace zobrazit chyba. K tomu může dojít i v případě, že jste ručně odebrali soubory z předchozí instalace, ale ponechali jsme nastavení machine.config beze změny.  
  
 Chybová zpráva se podobá následujícímu.  
  
```console  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Poznamenejte si z chybové zprávy, že sestavení System. ServiceModel verze 2.0.0.0 bylo nainstalováno vydáním verze CTP (Release Customer Technology Preview). Aktuální verze sestavení System. ServiceModel byla uvolněna místo toho 3.0.0.0. Proto k tomuto problému dochází, když chcete nainstalovat oficiální verzi služby WCF na počítač, na kterém je nainstalovaná verze služby WCF pro starší verzi CTP, ale ne úplně odinstalována.  
  
 ServiceModelReg.exe nemůže vyčistit předchozí položky verze, ani nemůže registrovat nové položky verze. Jediným alternativním řešením je ruční úprava machine.config. Tento soubor najdete v následujícím umístění.  
  
```console  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config
```  
  
 Pokud používáte WCF na 64m počítači, měli byste také upravit stejný soubor v tomto umístění.  
  
```console  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config
```  
  
 Vyhledejte v tomto souboru všechny uzly XML, které odkazují na "System. ServiceModel, Version = 2.0.0.0", odstraňte je a všechny podřízené uzly. Uložte soubor a znovu spusťte ServiceModelReg.exe vyřeší tento problém.  
  
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
