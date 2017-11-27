---
title: "Rozhraní hostování CLR"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3efdf649d0039f2eb6b39d5cb17c839b90e97508
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces"></a>Rozhraní hostování CLR
Tato část popisuje rozhraní, která nespravované hostitelů můžete integrovat common language runtime (CLR) do svých aplikací. Informace se vztahují na rozhraní .NET Framework verze 2.0 a novější verze. Tato rozhraní povolte hostitele k řízení další aspekty modul runtime, než bylo možné v verze 1.0 a 1.1 a zadejte mnohem náročnější integrace modulu CLR a model spouštění hostitele.  
  
 V rozhraní .NET Framework verze 1.0 a 1.1 model hostování povoleno nespravované hostitele k načtení modulu CLR do procesu, nakonfigurovat některá nastavení a k přijímání oznámení událostí. Ale obecně platí, hostitele a modulu CLR byla spuštěna nezávisle v tomto procesu. V rozhraní .NET Framework verze 2.0 a novějších verzích nechte nové vrstvy abstrakce hostitele zadejte mnoho prostředků aktuálně poskytuje typy v sestavení Win32 a rozšířit sadu funkcí, které můžete nakonfigurovat hostitele.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Iactiononclrevent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Poskytne metodu, která provede zpětné volání pro registrované událost.  
  
 [Iapartmentcallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Poskytuje metody pro provádění zpětných volání v rámci typu apartment.  
  
 [Iappdomainbinding – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Poskytuje metody pro konfiguraci nastavení spuštění.  
  
 [Icatalogservices – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Poskytuje metody pro vytváření katalogu služeb. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)  
  
 [Iclrassemblyidentitymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Poskytuje metody, které podporují komunikaci mezi hostitelem a CLR o sestavení.  
  
 [Iclrassemblyreferencelist – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Spravuje seznam sestavení, která jsou načtena modulu CLR a ne hostitele.  
  
 [Iclrcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Poskytuje metody pro hostitele k získání přístupu k a nakonfigurovat různé aspekty modulu CLR.  
  
 [Iclrdebugmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Poskytuje metody, které umožní hostitele k sadu úloh přidružit identifikátor a popisný název.  
  
 [Iclrerrorreportingmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Poskytuje metody, které umožní hostiteli nakonfigurovat vlastní haldy výpisy pro zasílání zpráv o chybách.  
  
 [Iclrgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Poskytuje metody, které umožní hostitele k interakci s systém kolekce paměti modulu CLR.  
  
 [Iclrhostbindingpolicymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Poskytuje metody pro hostitele k vyhodnocení a komunikaci změny v informace o zásadách pro sestavení.  
  
 [Iclrhostprotectionmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umožňuje hostiteli blokovat konkrétní spravované třídy, metody, vlastnosti a pole ve spuštění v částečně důvěryhodným kódem.  
  
 [Iclriocompletionmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metody zpětného volání, která umožňuje hostiteli oznámit CLR stavu zadaný vstupně-výstupní požadavky.  
  
 [Iclrmemorynotificationcallback – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Umožňuje hostiteli podmínky přetížení paměti sestavy pomocí podobná Win32 přístup `CreateMemoryResourceNotification` funkce.  
  
 [Iclroneventmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Poskytuje metody, které umožní hostitele registrace a zrušení registrace zpětných volání pro události CLR.  
  
 [ICLRPolicyManager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Poskytuje metody, které umožní na hostiteli a poté zadejte akce zásad pro případ selhání a vypršení časových limitů.  
  
 [Iclrprobingassemblyenum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Poskytuje metody, které umožňují získat zkušební identity sestavení pomocí informace identity je sestavení, která je interní modul CLR, aniž by museli vytvářet nebo pochopit tuto identitu hostitele.  
  
 [Iclrreferenceassemblyenum – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Poskytuje metody, které umožní hostitele k manipulaci s sadu sestavení odkazuje souboru nebo datový proud pomocí sestavení identifikační údaje, které je interní modul CLR, aniž by museli vytvářet nebo pochopení těchto identit.  
  
 [Iclrruntimehost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Poskytuje podobné možnosti [icorruntimehost –](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), s další způsob, jak nastavit rozhraní Řízení hostitele.  
  
 [Iclrsyncmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Poskytuje metody pro hostitele k načtení informací o požadovaných úkolů a ke zjištění zablokování v jeho implementaci synchronizace.  
  
 [Iclrtask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Poskytuje metody, které umožní hostitele pro požadavky modulu CLR, nebo zajistit oznámení modulu CLR o související úlohy.  
  
 [Iclrtaskmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Poskytuje metody, které umožní na hostiteli a požadavku explicitně modulu CLR vytvořit nový úkol, získat aktuálně spuštěné úlohy a nastavit zeměpisné language a jazykovou verzi pro úlohu.  
  
 [Iclrvalidator – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.  
  
 [Icorconfiguration – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Poskytuje metody pro konfiguraci modulu CLR.  
  
 [Icorthreadpool – rozhraní](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Poskytuje metody pro přístup k fondu vláken.  
  
 [Idebuggerinfo – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Poskytuje metody pro získání informací o stavu služby ladění.  
  
 [Idebuggerthreadcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Poskytuje metody pro upozornění hostitele o blokování a odblokování vláken ladění služby.  
  
 [Igchost – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Poskytuje metody pro získání informací o systém kolekce paměti a řízení některých aspektů uvolňování paměti.  
  
 [Igchost2 – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Poskytuje [setgcstartuplimitsex –](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metoda, která umožňuje pro hostitele a nastavte velikost segmentu kolekce paměti a maximální velikost systém kolekce paměti generování nula hodnoty větší než `DWORD`.  
  
 [Igchostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Poskytne metodu, která umožňuje uvolňování paměti požadavku na hostiteli a změnit omezení virtuální paměti.  
  
 [Igcthreadcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Poskytuje metody pro účastní plánování vláken, které by jinak blokovaly pro uvolňování paměti.  
  
 [Ihostassemblymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Poskytuje metody, které umožní hostitele k určení sady sestavení, které se mají načíst modul CLR, nebo hostitele.  
  
 [Ihostassemblystore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Poskytuje metody, které umožní hostitele k načtení sestavení a moduly nezávisle na modulu CLR.  
  
 [Ihostautoevent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Poskytuje reprezentaci událost automatickým vynulováním implementované hostitele.  
  
 [Ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Poskytuje metody pro konfiguraci načítání sestavení a určení, kterou rozhraní hostitel podporuje.  
  
 [Ihostcrst – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Slouží jako reprezentace hostitele kritické oddílu pro dělení na vlákna.  
  
 [Ihostgcmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Poskytuje metody, které hostitele události v kolekci mechanismus paměti implementované modulu CLR.  
  
 [Ihostiocompletionmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Poskytuje metody, které umožňují modulu CLR pro interakci s porty dokončení vstupně-výstupních operací od hostitele.  
  
 [Ihostmalloc – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Poskytuje metody pro CLR do požádat podrobných přidělení haldy prostřednictvím hostitele.  
  
 [Ihostmanualevent – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Poskytuje implementaci hostitele reprezentace Ruční vynulování události.  
  
 [Ihostmemorymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Poskytuje metody pro CLR provádět požadavky na virtuální paměti prostřednictvím hostitele, místo použití standardní funkce Win32 virtuální paměti.  
  
 [Ihostpolicymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Poskytuje metody, které hostitele akce, které provádí modulu CLR pro zrušení, překročení časového limitu nebo chyby.  
  
 [Ihostsecuritycontext – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Umožňuje CLR Udržovat informace kontextu zabezpečení implementované hostitele.  
  
 [Ihostsecuritymanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Poskytuje metody, které umožňují přístup k a kontrolu nad kontext zabezpečení aktuálně prováděné vlákno.  
  
 [Ihostsemaphore – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Poskytuje reprezentaci semafor implementované hostitele.  
  
 [Ihostsyncmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Poskytuje metody pro CLR vytvořit synchronizace primitiv voláním hostitele, místo použití funkce synchronizace Win32.  
  
 [Ihosttask – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Poskytuje metody, které umožní CLR ke komunikaci s hostitelem ke správě úloh.  
  
 [Ihosttaskmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Poskytuje metody, které umožňují modulu CLR pro práci s úkoly prostřednictvím hostitele místo použití funkce dělení na vlákna nebo fiber standardní operační systém.  
  
 [Ihostthreadpoolmanager – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Poskytuje metody pro CLR ke konfiguraci fondu vláken a do fronty pracovních položek pro fond vláken.  
  
 [IManagedObject – rozhraní](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Poskytuje metody pro řízení spravovaného objektu.  
  
 Iobjecthandle "–"  
 Poskytuje metodu pro rozbalení zařazování hodnota objekty z indirection.  
  
 [Itypename – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Poskytuje metody pro získání informací o název typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)  
  
 [Itypenamebuilder – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Poskytuje metody pro vytváření název typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)  
  
 [Itypenamefactory – rozhraní](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Poskytuje metody pro deconstructing název typu. (Toto rozhraní podporuje infrastrukturu rozhraní .NET Framework a není určena pro použití přímo z vašeho kódu.)  
  
 IValidator "–"  
 Poskytuje metody pro ověřování přenosné spustitelné bitové kopie (PE) a vytváření sestav chyby ověření.  
  
## <a name="related-sections"></a>Související oddíly  
 [Zastaralé rozhraní a třídy typu coclass hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Obsahuje témata, která popisují rozhraní hostování zadaný v rozhraní .NET Framework verze 1.0 a 1.1.  
  
 [Rozhraní hostování CLR přidaná v rozhraní .NET Framework 4 a 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Obsahuje témata, která popisují rozhraní hostování součástí [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
