---
title: Rozhraní hostování CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789659"
---
# <a name="clr-hosting-interfaces"></a>Rozhraní hostování CLR
Tato část popisuje rozhraní, která nespravovaných hostitelů můžete použít k integraci common language runtime (CLR) do svých aplikací. Informace se vztahují na rozhraní .NET Framework verze 2.0 a novějších verzích. Tato rozhraní umožňují hostitele tak, aby řízení více aspektů modul runtime, než bylo možné ve verzích 1.0 a 1.1 a poskytují mnohem užší integraci modulu CLR a spouštěcí model hostitele.  
  
 Model hostingu v rozhraní .NET Framework verze 1.0 a 1.1, povolené nespravovaný hostitel načíst modul CLR do procesu, nakonfigurovat některá nastavení a získat oznámení události. Ale obecně platí, hostitele a CLR spustili nezávisle na sobě v tomto procesu. V rozhraní .NET Framework verze 2.0 a novějších verzích nových úrovní abstrakce umožní hostovat poskytují mnoho prostředků, které jsou aktuálně k dispozici typy v sestavení Win32 a rozšířit sadu funkcí, které můžete nakonfigurovat hostitele.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [IActionOnCLREvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Poskytuje metodu, která provede zpětné volání pro registrované události.  
  
 [IApartmentCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Poskytuje metody pro provádění zpětných volání v rámci typu apartment.  
  
 [IAppDomainBinding – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Poskytuje metody pro konfiguraci nastavení za běhu.  
  
 [ICatalogServices – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Poskytuje metody pro vytváření katalogu služeb. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)  
  
 [ICLRAssemblyIdentityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestavení.  
  
 [ICLRAssemblyReferenceList – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Spravuje seznam sestavení, která jsou načtena pomocí modulu CLR a ne hostiteli.  
  
 [ICLRControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Poskytuje metody pro hostitele k získání přístupu k a konfigurovat různé funkce modulu CLR.  
  
 [ICLRDebugManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Poskytuje metody, které umožní hostitele do sady úloh přidružit identifikátor a popisný název.  
  
 [ICLRErrorReportingManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Poskytuje metody, které umožní hostitele tak, aby konfigurace výpisů paměti haldy vlastní pro hlášení chyb.  
  
 [ICLRGCManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Poskytuje metody, které umožní hostitele k interakci se systémem kolekce uvolnění paměti modulu CLR.  
  
 [ICLRHostBindingPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Poskytuje metody pro hostitele k vyhodnocení a Oznamovat změny v informace o zásadách pro sestavení.  
  
 [ICLRHostProtectionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole spouštění v částečně důvěryhodným kódem.  
  
 [ICLRIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metodu zpětného volání, která umožňuje hostiteli oznámit CLR stav zadaného vstupně-výstupní požadavky.  
  
 [ICLRMemoryNotificationCallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí metodiky podobný Win32 `CreateMemoryResourceNotification` funkce.  
  
 [ICLROnEventManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Poskytuje metody, které umožní hostitele tak, aby vytvářet a rušit registraci zpětná volání pro události CLR.  
  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Poskytuje metody, které umožní hostitele k určení akce zásad, které mají být provedeny v případě selhání a vypršení časového limitu.  
  
 [ICLRProbingAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Poskytuje metody, které umožní získat zkušební identity sestavení s použitím identity informací o sestavení, který je interní modul CLR, aniž by bylo nutné vytvořit nebo pochopit tuto identitu hostitele.  
  
 [ICLRReferenceAssemblyEnum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Poskytuje metody, které umožní hostitele k manipulaci s sadu sestavení odkazuje na soubor nebo datový proud pomocí data identitu sestavení, která je interní modul CLR, aniž by bylo nutné vytvořit nebo pochopit tyto identity.  
  
 [ICLRRuntimeHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Poskytuje funkce podobné [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), s další způsob, jak nastavit ovládací prvek rozhraní hostitele.  
  
 [ICLRSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Poskytuje metody pro hostitele a získat informace o požadované úlohy zjišťování případů zablokování v rámci příslušné implementace synchronizace.  
  
 [ICLRTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Poskytuje metody, které umožní hostitele k podání žádostí o modulu CLR, nebo k poskytování oznámení o přidružené úloze modulu CLR.  
  
 [ICLRTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Poskytuje metody, které umožní hostitele tak, aby explicitně vyžádat CLR vytvoří nový úkol, získat právě prováděnou úlohu a nastavit geografické jazyk a jazykovou verzi pro úlohu.  
  
 [ICLRValidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.  
  
 [ICorConfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Poskytuje metody pro konfiguraci modulu CLR.  
  
 [ICorThreadpool – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Poskytuje metody pro přístup k fondu vláken.  
  
 [IDebuggerInfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Poskytuje metody pro získání informací o stavu služeb ladění.  
  
 [IDebuggerThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken pomocí služeb ladění.  
  
 [IGCHost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Poskytuje metody pro získání informací o systému uvolňování paměti kolekce a pro řízení některé aspekty uvolňování paměti.  
  
 [IGCHost2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodu, která umožňuje hostiteli nastavte velikost segmentu kolekce uvolnění paměti a maximální velikost systému uvolňování paměti kolekce generace nula na hodnoty vyšší než `DWORD`.  
  
 [IGCHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Poskytuje metodu, která umožňuje uvolňování paměti požádat o hostiteli, chcete-li změnit omezení virtuální paměti.  
  
 [IGCThreadControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Poskytuje metody pro účast při plánování vláken, která by se jinak zablokovaly pro uvolnění paměti.  
  
 [IHostAssemblyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Poskytuje metody, které umožní hostitele zadat sadu sestavení, které se mají načíst modul CLR nebo hostitele.  
  
 [IHostAssemblyStore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Poskytuje metody, které umožní hostitele k načtení sestavení a modulů nezávisle na modulu CLR.  
  
 [IHostAutoEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Poskytuje reprezentaci událost automatickým vynulováním implementovaná tímto hostitelem.  
  
 [IHostControl – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Poskytuje metody pro konfiguraci načítání sestavení a k určení, kterou rozhraní hostitel podporuje.  
  
 [IHostCrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Slouží jako hostitele reprezentace kritický oddíl pro dělení na vlákna.  
  
 [IHostGCManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Poskytuje metody, které upozornil hostitele události v mechanismu kolekce uvolnění paměti implementován modulem CLR.  
  
 [IHostIoCompletionManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Poskytuje metody, které umožní modulu CLR pro interakci s poskytované hostitelem portů dokončení vstupně-výstupních operací.  
  
 [IHostMalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Poskytuje metody pro modul CLR pro žádosti o jemně odstupňovaných přidělení haldy přes hostitele.  
  
 [IHostManualEvent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Poskytuje implementaci hostitele reprezentace Ruční vynulování události.  
  
 [IHostMemoryManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Poskytuje metody pro modul CLR k podání žádostí o virtuální paměti prostřednictvím hostitele, namísto použití standardních funkcí virtuální paměti systému Win32.  
  
 [IHostPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Poskytuje metody, které upozornění na hostiteli akce, které modul CLR provede v případě klíčových přeruší, vypršení časového limitu nebo selhání.  
  
 [IHostSecurityContext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Umožňuje udržovat informace kontextu zabezpečení implementované hostitele modulu CLR.  
  
 [IHostSecurityManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Poskytuje metody, které umožňují přístup a kontrolu nad kontextu zabezpečení aktuálně spuštěné vlákno.  
  
 [IHostSemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Poskytuje reprezentaci semafor implementovaná tímto hostitelem.  
  
 [IHostSyncManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Poskytuje metody pro modul CLR k vytvoření synchronizací primitiv voláním hostitele, namísto použití funkce synchronizace Win32.  
  
 [IHostTask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Poskytuje metody, které umožní modulu CLR pro komunikaci s hostitelem ke správě úloh.  
  
 [IHostTaskManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Poskytuje metody, které umožní modulu CLR pro práci s úkoly prostřednictvím hostitele namísto použití funkce dělení na vlákna nebo vlákénka standardním operačním systému.  
  
 [IHostThreadPoolManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Poskytuje metody pro CLR ke konfiguraci fondu vláken a zařadit do fronty pracovních položek s fondem vláken.  
  
 [IManagedObject – rozhraní](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Poskytuje metody pro řízení spravovaného objektu.  
  
 Iobjecthandle "–"  
 Poskytuje metodu pro rozbalení objekty zařazování podle hodnot z dereference.  
  
 [ITypeName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Poskytuje metody pro získání informací o název typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)  
  
 [ITypeNameBuilder – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Poskytuje metody pro vytvoření názvu typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)  
  
 [ITypeNameFactory – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Poskytuje metody pro dekonstrukce název typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo v kódu.)  
  
 IValidator "–"  
 Poskytuje metody pro ověřování přenosné spustitelné (PE) bitové kopie a oznamování chyb ověřování.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralá rozhraní a třídy typu Coclass pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Obsahuje témata, která popisují rozhraní hostování zadaný v rozhraní .NET Framework verze 1.0 a 1.1.  
  
 [Rozhraní pro hostování CLR přidaná do .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Obsahuje témata, která popisují rozhraní hostování podle [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
