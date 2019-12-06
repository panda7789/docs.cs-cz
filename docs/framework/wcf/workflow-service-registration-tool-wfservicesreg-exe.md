---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: cf5ea345c900dec0e4859d81fcb272c1ba3d3df6
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837750"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Nástroj WorkFlow Service Registration (WFServicesReg.exe)
Nástroj pro registraci služby Workflow Services (WFServicesReg. exe) je samostatný nástroj, který se dá použít k přidání, odebrání nebo opravě elementů konfigurace pro služby programovací model Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj najdete v umístění instalace .NET Framework 3,5, konkrétně na%windir%\Microsoft.NET\Framework\v3.5 nebo na%windir%\Microsoft.NET\Framework64\v3.5 v 64 bitové počítače.  
  
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
  
- Referenční sestavení .NET Framework 3,5.  
  
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
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)]ch počítačích (IIS 5,1 a IIS 6,0) se zaregistruje jedna sada map. XOML a. Rules.  
  
 V 64 bitových počítačích nástroj zaregistruje v režimu WOW mapy skriptů, pokud je povolený přepínač `Enable32BitAppOnWin64`, nebo nativní 64é mapy skriptů, pokud je přepínač `Enable32BitAppOnWin64` zakázaný.  
  
 V počítačích se systémem Windows Vista a Windows Server 2008 (IIS 7,0 a vyšší) jsou registrovány dvě sady obslužných rutin. XOML a. Rules: jeden pro integrovaný režim a jeden pro klasický režim.  
  
 Na 64ch bitových počítačích jsou registrovány tři sady obslužných rutin (bez ohledu na stav přepínače `Enable32BitAppOnWin64`): jeden pro integrovaný režim, jeden pro integrovaný režim WOW a jeden pro nativní 64 klasický režim.  
  
> [!NOTE]
> Na rozdíl od ServiceModelreg. exe nepovoluje WFServicesReg. exe přidávání, odebírání ani opravy mapování skriptů nebo obslužných rutin pro konkrétní web. Alternativní řešení tohoto problému najdete v části "Oprava map skriptů".  
  
## <a name="usage-scenarios"></a>Scénáře použití  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalace služby IIS po instalaci .NET Framework 3,5  
 V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači se před instalací služby IIS nainstaluje .NET Framework 3,5. Z důvodu nedostupnosti metabáze služby IIS je instalace .NET Framework 3,5 úspěšná, aniž by bylo potřeba instalovat. XOML a. Rules mapy skriptů.  
  
 Po instalaci služby IIS můžete použít nástroj WFServicesReg. exe s přepínačem `/c` k instalaci těchto specifických mapování skriptů.  
  
### <a name="repairing-the-scriptmaps"></a>Oprava map skriptů  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>V uzlu weby byly odstraněny mapy skriptů.  
 V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači,. XOML nebo. Rules se omylem odstraní z uzlu weby. To lze opravit spuštěním nástroje WFServicesReg. exe s přepínačem `/c`.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapování skriptů se odstranilo v rámci určitého webu.  
 V [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítači,. XOML nebo. pravidla se náhodně odstraní z konkrétního webu (například z výchozího webu), nikoli z uzlu weby.  
  
 Chcete-li opravit odstraněné obslužné rutiny pro konkrétní web, spusťte příkaz "WFServicesReg. exe/r" pro odebrání obslužných rutin ze všech webů a pak spuštěním příkazu "WFServicesReg. exe/c" vytvořte vhodné obslužné rutiny pro všechny weby.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurace obslužných rutin po přepnutí režimu služby IIS  
 Když je služba IIS v režimu sdílené konfigurace a je nainstalovaná .NET Framework 3,5, je metabáze IIS nakonfigurovaná v rámci sdíleného umístění. Pokud přepnete službu IIS do nesdíleného konfiguračního režimu, místní metabáze nebude obsahovat požadované obslužné rutiny. Chcete-li správně nakonfigurovat místní metabázi, můžete buď importovat sdílenou metabázi do místní, nebo spustit příkaz "WFServicesReg. exe/c", který konfiguruje místní metabázi.
