---
title: Nástroj WorkFlow Service Registration (WFServicesReg.exe)
ms.date: 03/30/2017
ms.assetid: 9e92c87b-99c5-4e8d-9d53-7944cc2b47d3
ms.openlocfilehash: 3ea0f737cc050ec3f918044e0e105a41011a3e25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506558"
---
# <a name="workflow-service-registration-tool-wfservicesregexe"></a>Nástroj WorkFlow Service Registration (WFServicesReg.exe)
Nástroj pro registraci služby pracovního postupu (WFServicesReg.exe) je samostatný nástroj, který slouží k přidání, odebrání nebo opravte konfigurační prvky pro služby systému Windows Workflow Foundation (WF).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WFServicesReg.exe [-c | -r | -v | -m | -i]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj najdete na [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] umístění instalace, konkrétně % windir%\Microsoft.NET\Framework\v3.5, nebo v %windir%\Microsoft.NET\Framework64\v3.5 v 64bitové počítače.  
  
 Následující tabulka popisuje možnosti, které lze použít s nástroj pro registraci služby pracovního postupu (WFServicesReg.exe).  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/c`|Nakonfiguruje službu pracovního postupu systému Windows. Použít v instalaci a opravte scénáře.|  
|`/r`|Odebere konfigurace služby pracovního postupu systému Windows.|  
|`/v`|Tisk podrobné informace (pro konfiguraci nebo odebrání).|  
|`/m`|Umožňuje formát protokolování MSI.|  
|`/i`|Minimalizuje okno, pokud je aplikace spuštěná.|  
  
## <a name="registration"></a>Registrace  
 Tento nástroj kontroluje v souboru Web.config a zaregistruje následující:  
  
-   [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] referenční sestavení.  
  
-   Sestavení zprostředkovatele pro soubory XOML.  
  
-   Obslužné rutiny HTTP XOML a .rules souborů.  
  
 Tento nástroj kontroluje souboru Machine.config a zaregistruje následující rozšíření:  
  
-   behaviorExtensions  
  
-   bindingElementExtensions  
  
-   bindingExtensions  
  
 Nástroj také zaregistruje následující společnosti metadata importers pro klienta:  
  
-   policyImporters  
  
-   wsdlImporters  
  
 Nástroj také zaregistruje XOML a .rules mapy skriptů a obslužné rutiny v metabázi služby IIS.  
  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] a [!INCLUDE[wxp](../../../includes/wxp-md.md)] počítače (služba IIS 5.1 a [!INCLUDE[iis601](../../../includes/iis601-md.md)]), jedna sada XOML a .rules mapy skriptů jsou registrované.  
  
 Na 64bitových počítačích, nástroj zaregistruje mapy skriptů režimu WOW, pokud `Enable32BitAppOnWin64` přepínač je povolený nebo nativní 64bitové verze mapy skriptů, pokud `Enable32BitAppOnWin64` přepínač je zakázána.  
  
 Na [!INCLUDE[wv](../../../includes/wv-md.md)] a Windows Server 2008 (služby IIS 7.0 a vyšší) jsou registrované počítače, dvě sady XOML a .rules obslužné rutiny: jeden pro integrovaný režim a jeden pro klasický režim.  
  
 Na 64bitové počítače jsou registrované tři sady obslužné rutiny (bez ohledu na stav `Enable32BitAppOnWin64` přepínače): jeden pro integrovaný režim, jednu pro WOW klasickém režimu a jeden pro nativní 64bitové verze klasickém režimu.  
  
> [!NOTE]
>  Na rozdíl od ServiceModelreg.exe WFServicesReg.exe nepovoluje přidání, odebrání nebo opravu mapy skriptů nebo obslužné rutiny pro konkrétní web. Alternativní řešení tohoto problému najdete v části "Oprava mapy skriptů".  
  
## <a name="usage-scenarios"></a>Scénáře použití  
  
### <a name="installing-iis-after-net-framework-35-is-installed"></a>Instalace služby IIS po instalaci rozhraní .NET Framework 3.5  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítače [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalována před instalací služby IIS. Z důvodu nedostupnosti metabáze služby IIS, instalace [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] úspěšné bez instalace XOML a .rules mapy skriptů.  
  
 Po instalaci služby IIS, můžete použít nástroj WFServicesReg.exe s `/c` přepínač tak, aby nainstalovat tyto konkrétní mapy skriptů.  
  
### <a name="repairing-the-scriptmaps"></a>Oprava mapy skriptů  
  
#### <a name="scriptmap-deleted-under-web-sites-node"></a>Mapování skriptů odstranit pod uzlem webové stránky  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač, XOML nebo .rules se náhodou smazala z uzlu webových serverů. To lze opravit spuštěním nástroje WFServicesReg.exe s `/c` přepínače.  
  
#### <a name="scriptmap-deleted-under-a-particular-web-site"></a>Mapování skriptů odstranit v rámci určitého webového serveru  
 Na [!INCLUDE[ws2003](../../../includes/ws2003-md.md)] počítač XOML odstraněna nebo .rules je náhodně z určitého webového serveru (například výchozí web) a nikoli z uzlu webových serverů.  
  
 K opravě odstraněné obslužné rutiny pro určitý web, byste měli spustit "WFServicesReg.exe r" odebrat obslužné rutiny ze všech webů, spusťte "WFServicesReg.exe c" k vytvoření odpovídající obslužné rutiny pro všechny weby.  
  
### <a name="configuring-handlers-after-switching-iis-mode"></a>Konfigurace obslužné rutiny po přepnutí režimu služby IIS  
 Pokud služby IIS je v režimu sdílené konfigurace a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] je nainstalovaná, metabáze služby IIS je nakonfigurovaný pod sdílené umístění. Pokud přejdete na režim nesdílené konfigurace služby IIS, nebude obsahovat místní metabáze požadované obslužné rutiny. Konfigurace místního metabáze správně, můžete buď importovat sdílené metabáze na místní nebo spuštění "WFServicesReg.exe /c", který nakonfiguruje místní metabáze.
