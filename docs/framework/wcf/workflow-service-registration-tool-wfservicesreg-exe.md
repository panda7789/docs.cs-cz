---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 0a9cd5039c085f82f5507c93ebe0855cc620825d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916828"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Nástroj WorkFlow Service Registration (WFServicesReg.exe)
Nástroj pro registraci služby Workflow Services (WFServicesReg. exe) je samostatný nástroj, který se dá použít k přidání, odebrání nebo opravě elementů konfigurace pro služby programovací model Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj najdete na [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] instalačním umístění, konkrétně na%windir%\Microsoft.Net\Framework\v3.5 nebo na%windir%\Microsoft.NET\framework64\v3.5 v 64-bitových počítačích.  
  
 Následující tabulky popisují možnosti, které se dají použít s nástrojem pro registraci služby pracovních postupů (WFServicesReg. exe).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c`|Konfiguruje služby Windows Workflow Services. Používá se v scénářích instalace a opravy.|  
|`/r`|Odebere konfiguraci služby Windows Workflow Services.|  
|`/v`|Vytiskne podrobné informace o konfiguraci nebo odebrání.|  
|`/m`|Povolí formát protokolování MSI.|  
|`/i`|Minimalizuje okno při spuštění aplikace.|  
  
## <a name="registration"></a>Registrace  
 Nástroj zkontroluje soubor Web. config a zaregistruje následující:  
  
- [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]referenční sestavení.  
  
- Poskytovatel sestavení pro soubory. xoml.  
  
- Obslužné rutiny HTTP pro soubory. XOML a. Rules.  
  
 Nástroj zkontroluje soubor Machine. config a zaregistruje následující rozšíření:  
  
- behaviorExtensions  
  
- bindingElementExtensions  
  
- bindingExtensions  
  
 Nástroj také zaregistruje následující nástroje pro import metadat klienta:  
  
- policyImporters  
  
- wsdlImporters  
  
 Nástroj také zaregistruje mapy skriptů a obslužných rutin v metabázi služby IIS.  
  
 V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítačích [!INCLUDE[wxp](../../../includes/wxp-md.md)] a (IIS 5,1 a IIS 6,0) se zaregistruje jedna sada map. XOML a. Rules.  
  
 V 64 bitových počítačích nástroj zaregistruje v režimu WoW mapy skriptů `Enable32BitAppOnWin64` , pokud je přepínač povolený, nebo nativní 64 mapy skriptů `Enable32BitAppOnWin64` , pokud je přepínač zakázán.  
  
 V [!INCLUDE[wv](../../../includes/wv-md.md)] počítačích se systémem a Windows Server 2008 (IIS 7,0 a vyšší) jsou registrovány dvě sady obslužných rutin. XOML a. Rules: jeden pro integrovaný režim a jeden pro klasický režim.  
  
 Na 64ch bitových počítačích jsou zaregistrovány tři sady obslužných rutin (bez ohledu na stav `Enable32BitAppOnWin64` přepínače): jeden pro integrovaný režim, jeden pro integrovaný režim WoW a jeden pro nativní 64 klasický režim.  
  
> [!NOTE]
> Na rozdíl od ServiceModelreg. exe nepovoluje WFServicesReg. exe přidávání, odebírání ani opravy mapování skriptů nebo obslužných rutin pro konkrétní web. Alternativní řešení tohoto problému najdete v části "Oprava map skriptů".  
  
## <a name="usage-scenarios"></a>Scénáře použití  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalace služby IIS po instalaci .NET Framework 3,5  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] V[!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] počítači je nainstalován před instalací služby IIS. Z důvodu nedostupnosti metabáze služby IIS je instalace aplikace [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] úspěšná bez instalace skriptů mapy. XOML a. Rules.  
  
 Po instalaci služby IIS můžete použít nástroj WFServicesReg. exe s `/c` přepínačem k instalaci těchto specifických mapování skriptů.  
  
### <a name="repairing-the-scriptmaps"></a>Oprava map skriptů  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>V uzlu weby byly odstraněny mapy skriptů.  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] V počítači,. XOML nebo. pravidla se náhodně odstraní z uzlu weby. To lze opravit spuštěním nástroje WFServicesReg. exe s `/c` přepínačem.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapování skriptů se odstranilo v rámci určitého webu.  
 [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] V počítači se nechtěně odstraní z konkrétního webu (například výchozího webu), nikoli z uzlu weby.  
  
 Chcete-li opravit odstraněné obslužné rutiny pro konkrétní web, spusťte příkaz "WFServicesReg. exe/r" pro odebrání obslužných rutin ze všech webů a pak spuštěním příkazu "WFServicesReg. exe/c" vytvořte vhodné obslužné rutiny pro všechny weby.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurace obslužných rutin po přepnutí režimu služby IIS  
 Když je služba IIS v režimu sdílené konfigurace [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] a je nainstalovaná, je metabáze IIS nakonfigurovaná v rámci sdíleného umístění. Pokud přepnete službu IIS do nesdíleného konfiguračního režimu, místní metabáze nebude obsahovat požadované obslužné rutiny. Chcete-li správně nakonfigurovat místní metabázi, můžete buď importovat sdílenou metabázi do místní, nebo spustit příkaz "WFServicesReg. exe/c", který konfiguruje místní metabázi.
