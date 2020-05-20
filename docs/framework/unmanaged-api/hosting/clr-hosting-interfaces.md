---
title: Rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616837"
---
# <a name="clr-hosting-interfaces"></a>Rozhraní hostování CLR
Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) do svých aplikací. Informace se týkají .NET Framework verze 2,0 a novějších verzí. Tato rozhraní umožňují hostiteli řídit mnoho dalších aspektů modulu runtime, než bylo možné ve verzích 1,0 a 1,1, a poskytovat mnohem užší integraci mezi CLR a prováděcím modelem hostitele.  
  
 V .NET Framework verze 1,0 a 1,1 hostující model povolil nespravovanému hostiteli, aby načetl CLR do procesu, aby nakonfiguroval určitá nastavení a přijímal oznámení události. Obecně platí, že hostitel a CLR běžely nezávisle na tomto procesu. V .NET Framework verze 2,0 a novějších mají nové vrstvy abstrakce poskytnout hostiteli mnoho prostředků aktuálně poskytovaných typy v sestavení Win32 a rozšíření sady funkcí, které může hostitel konfigurovat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IActionOnCLREvent – rozhraní](iactiononclrevent-interface.md)  
 Poskytuje metodu, která provádí zpětné volání pro registrovanou událost.  
  
 [IApartmentCallback – rozhraní](iapartmentcallback-interface.md)  
 Poskytuje metody pro provádění zpětných volání v rámci objektu apartment.  
  
 [IAppDomainBinding – rozhraní](iappdomainbinding-interface.md)  
 Poskytuje metody pro nastavení konfigurace běhového běhu.  
  
 [ICatalogServices – rozhraní](icatalogservices-interface.md)  
 Poskytuje metody pro služby katalogu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ICLRAssemblyIdentityManager – rozhraní](iclrassemblyidentitymanager-interface.md)  
 Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestaveních.  
  
 [ICLRAssemblyReferenceList – rozhraní](iclrassemblyreferencelist-interface.md)  
 Spravuje seznam sestavení, která jsou načtena modulem CLR a nikoli hostitelem.  
  
 [ICLRControl – rozhraní](iclrcontrol-interface.md)  
 Poskytuje metody pro hostitele k získání přístupu a konfiguraci různých aspektů, CLR.  
  
 [ICLRDebugManager – rozhraní](iclrdebugmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli přidružit sadu úkolů s identifikátorem a popisným názvem.  
  
 [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)  
 Poskytuje metody, které hostiteli umožňují nakonfigurovat vlastní výpisy paměti haldy pro zasílání zpráv o chybách.  
  
 [ICLRGCManager – rozhraní](iclrgcmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti CLR.  
  
 [ICLRHostBindingPolicyManager – rozhraní](iclrhostbindingpolicymanager-interface.md)  
 Poskytuje metody pro hostitele k vyhodnocení a předávání změn v informacích o zásadách pro sestavení.  
  
 [ICLRHostProtectionManager – rozhraní](iclrhostprotectionmanager-interface.md)  
 Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ze spouštění v částečně důvěryhodném kódu.  
  
 [ICLRIoCompletionManager – rozhraní](iclriocompletionmanager-interface.md)  
 Implementuje metodu zpětného volání, která umožňuje hostiteli informovat modul CLR o stavu specifikovaných vstupně-výstupních požadavků.  
  
 [ICLRMemoryNotificationCallback – rozhraní](iclrmemorynotificationcallback-interface.md)  
 Umožňuje hostiteli hlásit podmínky pro tlak paměti pomocí přístupu podobného `CreateMemoryResourceNotification` funkci Win32.  
  
 [ICLROnEventManager – rozhraní](iclroneventmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události CLR.  
  
 [ICLRPolicyManager – rozhraní](iclrpolicymanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.  
  
 [ICLRProbingAssemblyEnum – rozhraní](iclrprobingassemblyenum-interface.md)  
 Poskytuje metody, které umožňují hostiteli získat identity sestavení pomocí informací o identitě sestavení, které jsou interní pro CLR, a to bez nutnosti vytvořit nebo porozumět této identitě.  
  
 [ICLRReferenceAssemblyEnum – rozhraní](iclrreferenceassemblyenum-interface.md)  
 Poskytuje metody, které umožňují hostiteli manipulovat s množinou sestavení, na které odkazuje soubor nebo datový proud, pomocí dat identity sestavení, která jsou interní pro CLR, aniž by bylo nutné tyto identity vytvářet nebo porozumět.  
  
 [ICLRRuntimeHost – rozhraní](iclrruntimehost-interface.md)  
 Poskytuje možnosti podobné [ICorRuntimeHost](icorruntimehost-interface.md), s další metodou pro nastavení rozhraní pro řízení hostitele.  
  
 [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)  
 Poskytuje metody pro hostitele k získání informací o požadovaných úlohách a k detekci zablokování v jeho implementaci synchronizace.  
  
 [ICLRTask – rozhraní](iclrtask-interface.md)  
 Poskytuje metody, které umožňují hostiteli vytvářet požadavky CLR, nebo poskytovat oznámení modulu CLR o přidružené úloze.  
  
 [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli explicitně požádat, aby CLR vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil zeměpisný jazyk a jazykovou verzi.  
  
 [ICLRValidator – rozhraní](iclrvalidator-interface.md)  
 Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
 [ICorConfiguration – rozhraní](icorconfiguration-interface.md)  
 Poskytuje metody pro konfiguraci CLR.  
  
 [ICorThreadpool – rozhraní](icorthreadpool-interface.md)  
 Poskytuje metody pro přístup ke fondu vláken.  
  
 [IDebuggerInfo – rozhraní](idebuggerinfo-interface.md)  
 Poskytuje metody pro získání informací o stavu služeb ladění.  
  
 [IDebuggerThreadControl – rozhraní](idebuggerthreadcontrol-interface.md)  
 Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.  
  
 [IGCHost – rozhraní](igchost-interface.md)  
 Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.  
  
 [IGCHost2 – rozhraní](igchost2-interface.md)  
 Poskytuje metodu [SetGCStartupLimitsEx –](igchost2-setgcstartuplimitsex-method.md) , která umožňuje hostiteli nastavit velikost segmentu uvolňování paměti a maximální velikost generace systému uvolňování paměti na hodnoty větší než `DWORD` .  
  
 [IGCHostControl – rozhraní](igchostcontrol-interface.md)  
 Poskytuje metodu, která umožňuje systému uvolňování paměti požádat hostitele o změnu omezení virtuální paměti.  
  
 [IGCThreadControl – rozhraní](igcthreadcontrol-interface.md)  
 Poskytuje metody pro účast v plánování vláken, která by jinak byla zablokována pro uvolňování paměti.  
  
 [IHostAssemblyManager – rozhraní](ihostassemblymanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR nebo hostitelem.  
  
 [IHostAssemblyStore – rozhraní](ihostassemblystore-interface.md)  
 Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR.  
  
 [IHostAutoEvent – rozhraní](ihostautoevent-interface.md)  
 Poskytuje reprezentaci události automatického resetování implementované hostitelem.  
  
 [IHostControl – rozhraní](ihostcontrol-interface.md)  
 Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.  
  
 [IHostCrst – rozhraní](ihostcrst-interface.md)  
 Slouží jako reprezentace kritické části pro vlákno.  
  
 [IHostGCManager – rozhraní](ihostgcmanager-interface.md)  
 Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementované modulem CLR.  
  
 [IHostIoCompletionManager – rozhraní](ihostiocompletionmanager-interface.md)  
 Poskytuje metody, které umožňují CLR pracovat s porty dokončovacího vstupu a výstupu poskytnutými hostitelem.  
  
 [IHostMalloc – rozhraní](ihostmalloc-interface.md)  
 Poskytuje metody pro modul CLR pro vyžádat detailní přidělení z haldy prostřednictvím hostitele.  
  
 [IHostManualEvent – rozhraní](ihostmanualevent-interface.md)  
 Poskytuje implementaci reprezentace události ručního resetování hostitele.  
  
 [IHostMemoryManager – rozhraní](ihostmemorymanager-interface.md)  
 Poskytuje metody pro CLR k vytváření požadavků virtuální paměti prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.  
  
 [IHostPolicyManager – rozhraní](ihostpolicymanager-interface.md)  
 Poskytuje metody, které upozorňují na hostitele akcí, které CLR provede v případě přerušení, vypršení časového limitu nebo selhání.  
  
 [IHostSecurityContext – rozhraní](ihostsecuritycontext-interface.md)  
 Umožňuje modulu CLR zachovat informace o kontextu zabezpečení implementované hostitelem.  
  
 [IHostSecurityManager – rozhraní](ihostsecuritymanager-interface.md)  
 Poskytuje metody, které umožňují přístup a řízení nad, kontext zabezpečení aktuálně prováděného vlákna.  
  
 [IHostSemaphore – rozhraní](ihostsemaphore-interface.md)  
 Poskytuje reprezentace semaforu implementovaného hostitelem.  
  
 [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)  
 Poskytuje metody pro modul CLR k vytváření synchronizačních primitiv voláním hostitele namísto použití synchronizačních funkcí Win32.  
  
 [IHostTask – rozhraní](ihosttask-interface.md)  
 Poskytuje metody, které umožňují, aby CLR komunikoval s hostitelem a spravoval úlohy.  
  
 [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)  
 Poskytuje metody, které umožňují CLR pracovat s úlohami přes hostitele namísto použití standardních vláken operačního systému nebo funkcí Fiber.  
  
 [IHostThreadPoolManager – rozhraní](ihostthreadpoolmanager-interface.md)  
 Poskytuje metody pro CLR ke konfiguraci fondu vláken a k zařazení pracovních položek do fondu vláken.  
  
 [IManagedObject – rozhraní](imanagedobject-interface.md)  
 Poskytuje metody pro řízení spravovaného objektu.  
  
 IObjectHandle –  
 Poskytuje metodu pro rozbalení objektů Marshal-to-Value z dereference.  
  
 [ITypeName – rozhraní](itypename-interface.md)  
 Poskytuje metody pro získání informací o názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ITypeNameBuilder – rozhraní](itypenamebuilder-interface.md)  
 Poskytuje metody pro sestavení názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ITypeNameFactory – rozhraní](itypenamefactory-interface.md)  
 Poskytuje metody pro dekonstrukci názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 IValidator  
 Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework verze 1,0 a 1,1.  
  
 [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework 4.
