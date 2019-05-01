---
title: Nástroj ServiceModel Registration (ServiceModelReg.exe)
ms.date: 03/30/2017
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
ms.openlocfilehash: 5fab1a356cd035ed006bfe90d713e179907e0137
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051777"
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Nástroj ServiceModel Registration (ServiceModelReg.exe)
Tento nástroj příkazového řádku umožňuje spravovat registraci součástí WCF a WF v jednom počítači. Za normálních okolností by neměl muset použít tento nástroj jako WCF a WF součásti konfigurují při instalaci. Ale pokud máte problémy s aktivací služby, můžete zkusit k registraci komponenty pomocí tohoto nástroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Poznámky  
 Nástroj najdete v následujícím umístění:  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
> [!NOTE]
>  Při spuštění nástroje pro registraci ServiceModel [!INCLUDE[wv](../../../includes/wv-md.md)], **funkce Windows** dialogového okna, která nemusí odrážet **aktivace Windows Communication Foundation HTTP** možnost **Rozhraní Microsoft .NET Framework 3.0** zapnutý. **Funkce Windows** dialogového okna můžete dostat kliknutím **Start**, pak klikněte na tlačítko **spustit** a zadáním **OptionalFeatures**.  
  
 Následující tabulky popisují požadované možnosti, které lze použít s ServiceModelReg.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-ia`|Nainstaluje všechny komponenty WCF a WF.|  
|`-ua`|Odinstaluje všechny součásti WCF a WF.|  
|`-r`|Opraví všechny součásti WCF a WF.|  
|`-i`|Nainstaluje součásti WCF a WF zadaným – c.|  
|`-u`|Odinstaluje součástí WCF a WF zadaným – c.|  
|`-c`|Nainstaluje nebo odinstaluje komponentu:<br /><br /> -httpnamespace – Namespace rezervace protokolu HTTP<br />služby Sdílení portů - tcpportsharing – TCP<br />aktivační služba - tcpactivation – TCP (Nepodporovaná na profil klienta rozhraní .NET 4)<br />služby - namedpipeactivation – aktivace pojmenovaného kanálu (Nepodporovaná na profil klienta rozhraní .NET 4<br />aktivační služba - služba msmqactivation – služby MSMQ (Nepodporovaná na profil klienta rozhraní .NET 4<br />manifesty trasování událostí trasování událostí pro – Windows – trasování událostí pro Windows (Windows Vista nebo novější)|  
|`-q`|Nastaví tichý režim (jenom protokolování zobrazení chyb)|  
|`-v`|Režim s komentářem.|  
|`-nologo`|Potlačí zprávu o autorských právech a úvodní nápis.|  
|`-?`|Zobrazí text nápovědy|  
  
## <a name="fixing-the-fileloadexception-error"></a>Oprava chyby FileLoadException –  
 Pokud jste nainstalovali dřívější verze služby WCF na svém počítači, může se zobrazit `FileLoadFoundException` při spuštění nástroje ServiceModelReg zaregistrovat nové instalace došlo k chybě. Může to i v případě, že máte ručně odebrat soubory z předchozí instalace, ale nastavení machine.config zůstává nedotčeno.  
  
 Chybová zpráva podobná následující.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Nezapomeňte přitom z chybové zprávy, že byla nainstalována sestavení verze 2.0.0.0 System.ServiceModel podle raného vydání zákazníka Technology Preview (CTP). Aktuální verze sestavení System.ServiceModel vydání je 3.0.0.0 místo. Proto se tento problém je došlo při chcete nainstalovat oficiálním vydáním WCF na počítači, kde byla nainstalována dřívější verzi CTP služby WCF, ale není zcela odinstalována.  
  
 ServiceModelReg.exe nelze vymazat, starší verze položky ani můžete zaregistrovat nové verze položky. Jediným alternativním řešením je ručně upravit soubor machine.config. Můžete najít tento soubor v následujícím umístění.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Pokud používáte WCF na 64bitovém počítači, byste měli upravovat stejný soubor v tomto umístění.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Vyhledejte žádnému z uzlů XML v tomto souboru, který najdete "System.ServiceModel, verze = 2.0.0.0", odstraňte je a všechny podřízené uzly. Uložte soubor a znovu spusťte ServiceModelReg.exe Tento problém se vyřeší.  
  
## <a name="examples"></a>Příklady  
 Následující příklady ukazují, jak používat nástroj ServiceModelReg.exe nejběžnější možnosti.  
  
```  
ServiceModelReg.exe -ia  
  Installs all components  
ServiceModelReg.exe -i -c:httpnamespace -c:etw  
  Installs HTTP namespace reservation and ETW manifests  
ServiceModelReg.exe -u -c:etw  
  Uninstalls ETW manifests  
ServiceModelReg.exe -r  
  Repairs an extended install  
```
