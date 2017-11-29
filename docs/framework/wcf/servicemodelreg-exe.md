---
title: "Nástroj ServiceModel Registration (ServiceModelReg.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 396ec5ae-e34f-4c64-a164-fcf50e86b6ac
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7032fd6005d5eccf27e0ca34cd89c050260d6e4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicemodel-registration-tool-servicemodelregexe"></a>Nástroj ServiceModel Registration (ServiceModelReg.exe)
Tento nástroj příkazového řádku umožňuje spravovat registraci komponent WCF a WF na jednom počítači. Za normálních podmínek by neměl budete muset použít tento nástroj jako WCF a konfigurace WF součástí při instalaci. Ale pokud dochází k potížím s aktivací prostřednictvím služby, můžete zkusit k registraci komponenty pomocí tohoto nástroje.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ServiceModelReg.exe[(-ia|-ua|-r)|((-i|-u) -c:<command>)] [-v|-q] [-nologo] [-?]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj naleznete v následujícím umístění:  
  
 Foundation\ %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace  
  
> [!NOTE]
>  Pokud je spuštěn nástroj ServiceModel Registration [!INCLUDE[wv](../../../includes/wv-md.md)], **funkce systému Windows** nemusí odrážet dialogu, který **aktivace Windows Communication Foundation HTTP** možnosti v části **Rozhraní Microsoft .NET Framework 3.0** je zapnutý. **Funkce systému Windows** dialogové okno můžete dostat kliknutím na **spustit**, pak klikněte na tlačítko **spustit** a zadáním **OptionalFeatures**.  
  
 Následující tabulka popisuje možnosti, které lze použít s ServiceModelReg.exe.  
  
|Možnost|Popis|  
|------------|-----------------|  
|`-ia`|Nainstaluje všechny komponenty WCF a WF.|  
|`-ua`|Odinstaluje všechny součásti WCF a WF.|  
|`-r`|Opraví všechny součásti WCF a WF.|  
|`-i`|Nainstaluje komponenty WCF a WF zadaným – c.|  
|`-u`|Odinstaluje součásti WCF a WF zadaným – c.|  
|`-c`|Instaluje a odinstaluje součásti:<br /><br /> -httpnamespace – Namespace rezervaci protokolu HTTP<br />služby Sdílení portů - tcpportsharing – TCP<br />aktivační služba - tcpactivation – TCP (nepodporovaný profil klienta rozhraní .NET 4)<br />služby - namedpipeactivation – pojmenovaný kanál aktivace (nepodporovaný profil klienta rozhraní .NET 4<br />aktivační služba - služba msmqactivation – služby MSMQ (nepodporovaný profil klienta rozhraní .NET 4<br />manifesty trasování událostí - etw – trasování událostí pro Windows (Windows Vista nebo novější)|  
|`-q`|Tichý režim (jenom protokolování chyb zobrazení)|  
|`-v`|Podrobné režimu.|  
|`-nologo`|Potlačí zprávu o autorských právech a hlavičku.|  
|`-?`|Zobrazí text nápovědy|  
  
## <a name="fixing-the-fileloadexception-error"></a>Oprava chyby FileLoadException  
 Pokud jste nainstalovali předchozí verze [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] na počítači, může dojít `FileLoadFoundException` při spuštění nástroje ServiceModelReg zaregistrovat nové instalace došlo k chybě. Tomu může dojít i v případě, že máte ručně odebrat soubory z předchozí instalace, ale zůstává nedotčeno nastavení souboru machine.config.  
  
 Chybová zpráva je podobný následujícímu.  
  
```  
Error: System.IO.FileLoadException: Could not load file or assembly 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies. The located assembly's manifest definition does not match the assembly reference. (Exception from HRESULT: 0x80131040)  
File name: 'System.ServiceModel, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'  
```  
  
 Nezapomeňte přitom z chybová zpráva, že byl nainstalován System.ServiceModel verzi 2.0.0.0 sestavení pomocí předběžnou verzi zákazníka Technology Preview (CTP). Aktuální verze sestavení System.ServiceModel vydané 3.0.0.0 se místo toho. Proto je tento problém zjistil při chcete nainstalovat oficiální [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] verze na počítači, kde vydání časná CTP [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] byl nainstalován, ale není zcela odinstalována.  
  
 ServiceModelReg.exe nelze vyčistit předchozí verze položky, ani můžete zaregistrovat na novou verzi položky. Jediným řešením je ruční úpravy souboru machine.config. Tento soubor v následujícím umístění lze vyhledat.  
  
```  
%windir%\Microsoft.NET\Framework\v2.0.50727\config\machine.config   
```  
  
 Pokud používáte [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] na 64bitový počítač, by také upravit stejný soubor v tomto umístění.  
  
```  
%windir%\Microsoft.NET\Framework64\v2.0.50727\config\machine.config   
```  
  
 Vyhledejte žádnému z uzlů XML v tomto souboru, který najdete "System.ServiceModel, verze = 2.0.0.0", odstraňte je a všechny podřízené uzly. Uložte tento soubor a znovu spusťte ServiceModelReg.exe Tento problém se vyřeší.  
  
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
