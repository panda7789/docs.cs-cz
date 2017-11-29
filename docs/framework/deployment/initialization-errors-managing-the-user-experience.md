---
title: ".NET Framework – chyby inicializace: správa zkušeností uživatele"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- no framework found experience
- initialization errors [.NET Framework]
- .NET Framework, initialization errors
ms.assetid: 680a7382-957f-4f6e-b178-4e866004a07e
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a0b03f2b5c0c656b8800d1b2ceff9b774a5c65d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="net-framework-initialization-errors-managing-the-user-experience"></a>.NET Framework – chyby inicializace: správa zkušeností uživatele
Systému aktivace modulu runtime (CLR) určuje verzi modulu CLR, který se použije ke spuštění kódu spravované aplikace. V některých případech nemusí být schopni najít verzi modulu CLR načíst aktivačního systému. K této situaci obvykle dochází, pokud aplikace vyžaduje verzi CLR, která je neplatná nebo není nainstalována v daném počítači. Pokud není nalezen požadovanou verzi, systém aktivace CLR vrátí kód chyby HRESULT z funkce nebo rozhraní, která byla volána a může zobrazit chybovou zprávu pro uživatele, který je spuštěna aplikace. Tento článek obsahuje seznam kódů HRESULT a vysvětluje, jak můžete zabránit v chybové zprávě se zobrazí.  
  
 Modul CLR poskytuje infrastrukturu protokolování pro ladění problémů aktivace CLR, jak je popsáno v [postupy: ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md). Tato infrastruktura Nezaměňovat s [sestavení – vazby protokolů](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md), který se zcela liší.  
  
## <a name="clr-activation-hresult-codes"></a>Kódy HRESULT aktivace CLR  
 Aktivace CLR rozhraní API návratové kódy HRESULT nahlásit výsledek operace aktivace na hostitele. Hostitelé CLR by se měli obrátit vždy tyto návratové hodnoty před provedením další operace.  
  
-   CLR_E_SHIM_RUNTIMELOAD  
  
-   CLR_E_SHIM_RUNTIMEEXPORT  
  
-   CLR_E_SHIM_INSTALLROOT  
  
-   CLR_E_SHIM_INSTALLCOMP  
  
-   CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND  
  
-   CLR_E_SHIM_SHUTDOWNINPROGRESS  
  
## <a name="ui-for-initialization-errors"></a>Uživatelské rozhraní pro chyby inicializace  
 Pokud systém aktivace CLR nelze načíst správnou verzi modulu runtime, který je požadován pro aplikace, zobrazí chybovou zprávu uživatelům, aby informujte je, že jejich počítač není správně nakonfigurována pro spuštění aplikace a získat tak s příležitost k nápravě. V této situaci se obvykle zobrazí následující chybová zpráva. Uživatel může vybrat **Ano** přejít na webu společnosti Microsoft, kde si můžete stáhnout správnou verzi rozhraní .NET Framework pro aplikaci.  
  
 ![Dialogové okno chyby inicializace rozhraní .NET framework](../../../docs/framework/deployment/media/initerrordialog.png "InitErrorDialog")  
Typické chybovou zprávu pro chyby inicializace  
  
## <a name="resolving-the-initialization-error"></a>Řešení chyby inicializace  
 Jako vývojář máte různé možnosti pro řízení chybová zpráva inicializace rozhraní .NET Framework. Například můžete použít rozhraní API příznak zabránit zpráva se zobrazuje, jak je popsáno v následující části. Ale máte k vyřešení problému, která zabránila načítání modulu runtime požadované aplikace. Jinak vaše aplikace nemusí vůbec spustit nebo některé funkce nemusí být k dispozici.  
  
 Vyřešte problémy s základní a dosažení optimálního výkonu uživatele (méně chybové zprávy), doporučujeme následující:  
  
-   Pro aplikace .NET Framework 3.5 (a starší): Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5 (viz [pokyny](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)).  
  
-   Pro aplikace rozhraní .NET Framework 4: Nainstalujte redistribuovatelný balíček .NET Framework 4 jako součást instalace aplikace. V tématu [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md).  
  
## <a name="controlling-the-error-message"></a>Řízení chybová zpráva  
 Zobrazení chybovou zprávu pro komunikaci, aby nebyla nalezena požadovaná verze rozhraní .NET Framework lze zobrazit jako užitečné službu nebo dílčí obtěžování hlukem uživatelům. V obou případech můžete řídit toto uživatelské rozhraní pomocí předání příznaky aktivace rozhraní API.  
  
 [Iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda přijímá [METAHOST_POLICY_FLAGS](../../../docs/framework/unmanaged-api/hosting/metahost-policy-flags-enumeration.md) – člen výčtu jako vstup. Můžete zahrnout příznak METAHOST_POLICY_SHOW_ERROR_DIALOG požádat o chybovou zprávu, pokud není nalezena požadovanou verzi modulu CLR. Ve výchozím nastavení se chybová zpráva nezobrazí. ( [Iclrmetahost::getruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md) metoda nepřijímá tento příznak a neposkytuje žádné jiný způsob, jak zobrazit chybová zpráva.)  
  
 Systém Windows nabízí [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkID=255242) funkce, která vám pomůže deklarovat, jestli chcete chybové zprávy, která se má zobrazit v důsledku kód, který běží v rámci procesu. Můžete zadat příznak SEM_FAILCRITICALERRORS k zabránění zobrazení chybovou zprávu.  
  
 V některých scénářích, je důležité pro přepsání nastavení SEM_FAILCRITICALERRORS nastavit aplikační proces. Například pokud máte nativní komponenty modelu COM, který je hostitelem modulu CLR a který je hostován v procesu, kde je nastaven SEM_FAILCRITICALERRORS, můžete přepsat příznak, v závislosti na dopad zobrazení chybové zprávy v rámci tohoto procesu konkrétní aplikace. V takovém případě můžete provádět následující příznaky přepsat SEM_FAILCRITICALERRORS:  
  
-   Použít METAHOST_POLICY_IGNORE_ERROR_MODE s [iclrmetahostpolicy::getrequestedruntime –](../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metoda.  
  
-   Použít RUNTIME_INFO_IGNORE_ERROR_MODE s [getrequestedruntimeinfo –](../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md) funkce.  
  
## <a name="ui-policy-for-clr-provided-hosts"></a>Zásady uživatelského rozhraní pro zadaný CLR hostitele  
 Modul CLR zahrnuje na skupinu hostitelů pro celou řadu scénářů a všichni tito hostitelé zobrazí chybovou zprávu, když narazí na problémy s načtením požadovanou verzi modulu runtime. Následující tabulka obsahuje seznam hostitelů a jejich zásady zprávu chyby.  
  
|CLR hostitele|Popis|Zásada pro chybové zprávy|Je možné zakázat chybová zpráva?|  
|--------------|-----------------|--------------------------|------------------------------------|  
|Spravovaného hostitele EXE|Spustí spravované souborů exe.|Se zobrazí v případě chybějící verze rozhraní .NET Framework|Ne|  
|Spravovaného hostitele COM|Načítání spravované komponenty modelu COM do procesu.|Se zobrazí v případě chybějící verze rozhraní .NET Framework|Ano, a to nastavením SEM_FAILCRITICALERRORS příznak|  
|Hostitele ClickOnce|Spustí se aplikace ClickOnce.|Se zobrazí v případě chybějící verze rozhraní .NET Framework, od verze[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Ne|  
|XBAP hostitele|Spustí se aplikace WPF XBAP.|Se zobrazí v případě chybějící verze rozhraní .NET Framework, od verze[!INCLUDE[net_v45](../../../includes/net-v45-md.md)]|Ne|  
  
## <a name="includewin8includeswin8-mdmd-behavior-and-ui"></a>[!INCLUDE[win8](../../../includes/win8-md.md)]Chování a uživatelského rozhraní  
 Systém aktivace CLR poskytuje stejné chování a uživatelského rozhraní na [!INCLUDE[win8](../../../includes/win8-md.md)] jako na ostatních verzí operačního systému Windows, kromě případů, kdy zjistí problémy načítání CLR 2.0. [!INCLUDE[win8](../../../includes/win8-md.md)]zahrnuje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], který používá CLR 4.5. Ale [!INCLUDE[win8](../../../includes/win8-md.md)] neobsahuje rozhraní .NET Framework 2.0, 3.0 nebo 3.5, které použít CLR 2.0. V důsledku toho se aplikace, které závisí na CLR 2.0 nespouštějte [!INCLUDE[win8](../../../includes/win8-md.md)] ve výchozím nastavení. Místo toho se zobrazit následující dialogové okno Povolit uživatelům pro instalaci rozhraní .NET Framework 3.5. Uživatele můžete také povolit rozhraní .NET Framework 3.5 v Ovládacích panelech. Obě možnosti jsou popsané v článku [nainstalovat rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md).  
  
 ![Dialogové okno pro 3.5 instalace v systému Windows 8](../../../docs/framework/deployment/media/installdialog.png "installdialog")  
Řádku pro instalaci rozhraní .NET Framework 3.5 na vyžádání  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Nahrazuje rozhraní .NET Framework 4 (CLR 4) v počítači uživatele. Proto rozhraní .NET Framework 4 aplikace běžely, bez zobrazení toto dialogové okno, v [!INCLUDE[win8](../../../includes/win8-md.md)].  
  
 Při instalaci rozhraní .NET Framework 3.5, uživatelé mohou spouštět aplikace, které závisí na rozhraní .NET Framework 2.0, 3.0 nebo 3.5 na jejich [!INCLUDE[win8](../../../includes/win8-md.md)] počítače. Rozhraní .NET Framework 1.0 a 1.1 aplikace, mohou spouštět také za předpokladu, že tyto aplikace nejsou explicitně nakonfigurovaný pro spouštění jenom v rozhraní .NET Framework 1.0 nebo 1.1. V tématu [migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).  
  
 Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zahrnout položky protokolu, které zaznamenávají, kdy a proč se zobrazí chybová zpráva inicializace se zlepšila protokolování aktivace CLR. Další informace najdete v tématu [postupy: ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce nasazením pro vývojáře](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo 4.5](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)  
 [Postupy: ladění problémů aktivace CLR](../../../docs/framework/deployment/how-to-debug-clr-activation-issues.md)  
 [Nainstalujte rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)
