---
title: Rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131972"
---
# <a name="clr-hosting-interfaces"></a>Rozhraní hostování CLR
Tato část popisuje rozhraní, která nespravované hostitele můžou použít k integraci modulu CLR (Common Language Runtime) do svých aplikací. Informace se týkají .NET Framework verze 2,0 a novějších verzí. Tato rozhraní umožňují hostiteli řídit mnoho dalších aspektů modulu runtime, než bylo možné ve verzích 1,0 a 1,1, a poskytovat mnohem užší integraci mezi CLR a prováděcím modelem hostitele.  
  
 V .NET Framework verze 1,0 a 1,1 hostující model povolil nespravovanému hostiteli, aby načetl CLR do procesu, aby nakonfiguroval určitá nastavení a přijímal oznámení události. Obecně platí, že hostitel a CLR běžely nezávisle na tomto procesu. V .NET Framework verze 2,0 a novějších mají nové vrstvy abstrakce poskytnout hostiteli mnoho prostředků aktuálně poskytovaných typy v sestavení Win32 a rozšíření sady funkcí, které může hostitel konfigurovat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Poskytuje metodu, která provádí zpětné volání pro registrovanou událost.  
  
 [IApartmentCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Poskytuje metody pro provádění zpětných volání v rámci objektu apartment.  
  
 [IAppDomainBinding – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Poskytuje metody pro nastavení konfigurace běhového běhu.  
  
 [ICatalogServices – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Poskytuje metody pro služby katalogu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestaveních.  
  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Spravuje seznam sestavení, která jsou načtena modulem CLR a nikoli hostitelem.  
  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Poskytuje metody pro hostitele k získání přístupu a konfiguraci různých aspektů, CLR.  
  
 [ICLRDebugManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli přidružit sadu úkolů s identifikátorem a popisným názvem.  
  
 [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Poskytuje metody, které hostiteli umožňují nakonfigurovat vlastní výpisy paměti haldy pro zasílání zpráv o chybách.  
  
 [ICLRGCManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli pracovat se systémem uvolňování paměti CLR.  
  
 [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Poskytuje metody pro hostitele k vyhodnocení a předávání změn v informacích o zásadách pro sestavení.  
  
 [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ze spouštění v částečně důvěryhodném kódu.  
  
 [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metodu zpětného volání, která umožňuje hostiteli informovat modul CLR o stavu specifikovaných vstupně-výstupních požadavků.  
  
 [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Umožňuje hostiteli hlásit podmínky pro tlak paměti pomocí přístupu podobného funkci Win32 `CreateMemoryResourceNotification`.  
  
 [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli registrovat a odregistrovat zpětná volání pro události CLR.  
  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli určit akce zásad, které mají být provedeny v případě selhání a časových limitů.  
  
 [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Poskytuje metody, které umožňují hostiteli získat identity sestavení pomocí informací o identitě sestavení, které jsou interní pro CLR, a to bez nutnosti vytvořit nebo porozumět této identitě.  
  
 [ICLRReferenceAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Poskytuje metody, které umožňují hostiteli manipulovat s množinou sestavení, na které odkazuje soubor nebo datový proud, pomocí dat identity sestavení, která jsou interní pro CLR, aniž by bylo nutné tyto identity vytvářet nebo porozumět.  
  
 [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Poskytuje možnosti podobné [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), s další metodou pro nastavení rozhraní pro řízení hostitele.  
  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Poskytuje metody pro hostitele k získání informací o požadovaných úlohách a k detekci zablokování v jeho implementaci synchronizace.  
  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Poskytuje metody, které umožňují hostiteli vytvářet požadavky CLR, nebo poskytovat oznámení modulu CLR o přidružené úloze.  
  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli explicitně požádat, aby CLR vytvořil nový úkol, získal aktuálně spuštěnou úlohu a pro úkol nastavil zeměpisný jazyk a jazykovou verzi.  
  
 [ICLRValidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
 [ICorConfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Poskytuje metody pro konfiguraci CLR.  
  
 [ICorThreadpool – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Poskytuje metody pro přístup ke fondu vláken.  
  
 [IDebuggerInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Poskytuje metody pro získání informací o stavu služeb ladění.  
  
 [IDebuggerThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.  
  
 [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Poskytuje metody pro získání informací o systému uvolňování paměti a pro řízení některých aspektů uvolňování paměti.  
  
 [IGCHost2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Poskytuje metodu [SetGCStartupLimitsEx –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , která umožňuje hostiteli nastavit velikost segmentu uvolňování paměti a maximální velikost generace systému uvolňování paměti na hodnotu větší než `DWORD`.  
  
 [IGCHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Poskytuje metodu, která umožňuje systému uvolňování paměti požádat hostitele o změnu omezení virtuální paměti.  
  
 [IGCThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Poskytuje metody pro účast v plánování vláken, která by jinak byla zablokována pro uvolňování paměti.  
  
 [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Poskytuje metody, které umožňují hostiteli určit sady sestavení, které by měly být načteny modulem CLR nebo hostitelem.  
  
 [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Poskytuje metody, které umožňují hostiteli načíst sestavení a moduly nezávisle na modulu CLR.  
  
 [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Poskytuje reprezentaci události automatického resetování implementované hostitelem.  
  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Poskytuje metody pro konfiguraci načítání sestavení a pro určení, která hostující rozhraní hostitel podporuje.  
  
 [IHostCrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Slouží jako reprezentace kritické části pro vlákno.  
  
 [IHostGCManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Poskytuje metody, které upozorňují na hostitele událostí v mechanizmu uvolňování paměti implementované modulem CLR.  
  
 [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Poskytuje metody, které umožňují CLR pracovat s porty dokončovacího vstupu a výstupu poskytnutými hostitelem.  
  
 [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Poskytuje metody pro modul CLR pro vyžádat detailní přidělení z haldy prostřednictvím hostitele.  
  
 [IHostManualEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Poskytuje implementaci reprezentace události ručního resetování hostitele.  
  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Poskytuje metody pro CLR k vytváření požadavků virtuální paměti prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.  
  
 [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Poskytuje metody, které upozorňují na hostitele akcí, které CLR provede v případě přerušení, vypršení časového limitu nebo selhání.  
  
 [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Umožňuje modulu CLR zachovat informace o kontextu zabezpečení implementované hostitelem.  
  
 [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Poskytuje metody, které umožňují přístup a řízení nad, kontext zabezpečení aktuálně prováděného vlákna.  
  
 [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Poskytuje reprezentace semaforu implementovaného hostitelem.  
  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Poskytuje metody pro modul CLR k vytváření synchronizačních primitiv voláním hostitele namísto použití synchronizačních funkcí Win32.  
  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Poskytuje metody, které umožňují, aby CLR komunikoval s hostitelem a spravoval úlohy.  
  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Poskytuje metody, které umožňují CLR pracovat s úlohami přes hostitele namísto použití standardních vláken operačního systému nebo funkcí Fiber.  
  
 [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Poskytuje metody pro CLR ke konfiguraci fondu vláken a k zařazení pracovních položek do fondu vláken.  
  
 [IManagedObject – rozhraní](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Poskytuje metody pro řízení spravovaného objektu.  
  
 IObjectHandle –  
 Poskytuje metodu pro rozbalení objektů Marshal-to-Value z dereference.  
  
 [ITypeName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Poskytuje metody pro získání informací o názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ITypeNameBuilder – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Poskytuje metody pro sestavení názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 [ITypeNameFactory – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Poskytuje metody pro dekonstrukci názvu typu. (Toto rozhraní podporuje infrastrukturu .NET Framework a není určeno pro použití přímo v kódu.)  
  
 IValidator  
 Poskytuje metody pro ověřování přenosných spustitelných souborů (PE) a chyb ověřování sestav.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework verze 1,0 a 1,1.  
  
 [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Obsahuje témata, která popisují rozhraní hostování poskytované v .NET Framework 4.
