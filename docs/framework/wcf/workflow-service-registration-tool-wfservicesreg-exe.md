---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: da377e865258169bdca16cfb0db3f8612d4e0f0d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613067"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Nástroj WorkFlow Service Registration (WFServicesReg.exe)
Nástroj pro registraci služby pracovních postupů (WFServicesReg.exe) je samostatný nástroj, který slouží k přidání, odebrání nebo opravte elementů konfigurace pro služby Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Poznámky  
 Nástroj lze nalézt v [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] umístění instalace, konkrétně % windir%\Microsoft.NET\Framework\v3.5, nebo na %windir%\Microsoft.NET\Framework64\v3.5 v 64bitových počítačích.  
  
 Následující tabulky popisují požadované možnosti, které je možné pomocí nástroje pro registraci služby pracovních postupů (WFServicesReg.exe).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c`|Nakonfiguruje služby pracovního postupu Windows. Při instalaci a opravte scénáře.|  
|`/r`|Odebere konfigurace služby pracovního postupu Windows.|  
|`/v`|Vytisknout podrobné informace (pro konfiguraci nebo odebrání).|  
|`/m`|Povolí formát protokolování MSI.|  
|`/i`|Minimalizuje okno při spuštění aplikace.|  
  
## <a name="registration"></a>Registrace  
 Nástroj zkontroluje v souboru Web.config a zaregistruje následující:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] referenční sestavení.  
  
- Sestavení zprostředkovatele pro soubory XOML.  
  
- Obslužné rutiny HTTP pro soubory XOML a .rules.  
  
 Nástroj zkontroluje soubor Machine.config a registruje následující rozšíření:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Nástroj také zaregistruje následující metadata importers klienta:  
  
- policyImporters  
  
- wsdlImporters  
  
 Nástroj také zaregistruje XOML a .rules mapy skriptů a obslužné rutiny v metabázi služby IIS.  
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)] počítače (služba IIS 5.1 a [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jedna sada XOML a .rules mapy skriptů jsou registrované.  
  
 Na 64bitových počítačích, nástroj zaregistruje mapy skriptů režimu WOW, pokud `Enable32BitAppOnWin64` přepínač je povolený, nebo nativní 64bitové mapy skriptů, pokud `Enable32BitAppOnWin64` přepínač je zakázaný.  
  
 Na [!INCLUDE[wv](../../../includes/wv-md.md)] a Windows Server 2008 (služba IIS 7.0 a vyšší) počítače, dvě sady XOML a .rules obslužné rutiny jsou registrovány: jeden pro integrovaný režim a jeden pro klasický režim.  
  
 Na 64bitových počítačích jsou registrovány tři páry obslužné rutiny (bez ohledu na stav `Enable32BitAppOnWin64` přepnout): jeden pro integrovaný režim, jeden pro WOW klasického režimu a jeden pro nativní 64bitové klasickém režimu.  
  
> [!NOTE]
>  Na rozdíl od ServiceModelreg.exe WFServicesReg.exe neumožňuje přidání, odebrání nebo oprava mapování skriptů nebo obslužné rutiny pro určitý web. Alternativní řešení těchto potíží najdete v části "Oprava the mapy skriptů".  
  
## <a name="usage-scenarios"></a>Scénáře použití  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalace služby IIS po instalaci rozhraní .NET Framework 3.5  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítače, [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] nainstalovaný před instalací služby IIS. Kvůli nedostupnosti metabáze služby IIS, instalaci [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] bude úspěšné bez instalace XOML a .rules mapy skriptů.  
  
 Po instalaci služby IIS, můžete použít nástroj WFServicesReg.exe s `/c` přepínač k instalaci těchto konkrétních mapy skriptů.  
  
### <a name="repairing-the-scriptmaps"></a>Oprava mapování skriptů  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Odstranit pod uzlem weby v mapě skriptů  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules náhodně odstraní ze uzel weby. To lze opravit spuštěním nástroje WFServicesReg.exe s `/c` přepnout.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapování skriptů odstranit v rámci určitého webového serveru  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules náhodně odstraní z určitého webového serveru (například výchozí web), nikoli z uzlu webových serverů.  
  
 K opravě odstraněné obslužné rutiny pro určitý web, měli byste spustit "WFServicesReg.exe r" k odebrání obslužných rutin ze všech webů, spusťte "WFServicesReg.exe c" k vytvoření odpovídající obslužné rutiny pro všechny weby.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurace obslužné rutiny po změně režimu služby IIS  
 Když služba IIS pracuje v režimu sdílenou konfiguraci a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalovaný, metabáze služby IIS je nakonfigurované v rámci sdílené umístění. Pokud přepnete do režimu bez sdílená konfigurace služby IIS, nebude obsahovat místní metabáze požadované obslužné rutiny. Pokud chcete nakonfigurovat místní metabáze správně, můžete buď importovat sdílené metabáze na místní nebo spuštění "WFServicesReg.exe /c", který konfiguruje místní metabáze.
