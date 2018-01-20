---
title: "Schéma nastavení běhového prostředí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
caps.latest.revision: "49"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8318c3c0d4d4321f84b936949fdb2474b1d05b4
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="runtime-settings-schema"></a>Schéma nastavení běhového prostředí
Nastavení běhového prostředí jsou používány modul common language runtime lze nakonfigurovat aplikace cílených rozhraní .NET Framework.  
  
 [\<Konfigurace >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
 [\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)  
 [\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)  
 [\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
 [\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
 [\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)  
 [\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)  
 [\<assemblyIdentity >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)  
 [\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
 [\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)  
 [\<Zkušební fáze >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)  
 [\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)  
 [\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)  
 [\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)  
 [\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)  
 [\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)  
 [\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)  
 [\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)  
 [\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)  
 [\<enforcefipspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)  
 [\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)  
 [\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)  
 [\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
 [\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
 [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)  
 [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)  
 [\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)  
 [\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)  
 [\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)  
 [\<loadfromremotesources – >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)  
 [<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)  
 [<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)  
 [<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)  
 [\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)  
 [\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)  
 [\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)  
 [\<supportPortability – >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
 [\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)  
 [\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)  
 [\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)  
 [\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)  
 [<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)  
 [\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)  
 [<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
 [\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)  
 [\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)  
 [\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Přidá pojmenované mezipaměti, aby `namedCaches` kolekci pro mezipaměť.|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Určuje, že Windows identity vždy přeteče asynchronní bodů, bez ohledu na to, jak byla provedena zosobnění.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínač používaný <xref:System.AppContext> třídy poskytují mechanismus vyjádření výslovného nesouhlasu pro nové funkce.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce domény aplikace pro výchozí doméně aplikace v procesu.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce domény aplikace pro výchozí doménu aplikace.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Dá pokyn modulu runtime ke shromažďování statistik na všechny domény aplikace v procesu po dobu trvání procesu.|  
|[\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|[\<assemblyIdentity >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|Obsahuje identifikační informace o sestavení.|  
|[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|Přesměruje jednu verzi sestavení k jiné.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Určuje, zda by měl obejít ověřování silných názvů pro důvěryhodné sestavení.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekci pro mezipaměť.|  
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|Určuje, kde sestavení modulu runtime.|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Určuje, že modul runtime by měl používat starší řazení chování při provádění porovnávání řetězců|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Určuje, jestli ukládání do mezipaměti vazby selhání, což je výchozí chování v [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)], je zakázán.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Určuje, jestli je úplná vlákno zásobníku potvrzeny při spuštění vlákna.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Určuje, zda je výchozí chování, které je umožnit runtime hostitelů pro přepsání nastavení konfigurace pro doménu aplikace, zakázána.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Určuje, zda datum a čas analýza metody použít upravenou sadu pravidel analyzovat data řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.|  
|[\<enforcefipspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Určuje, jestli vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu s na zpracování standardů FIPS (Federal Information).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, zda PerfCounter.dll používá nastavení registru CategoryOptions v rozhraní .NET Framework verze 1.1 aplikaci a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Určuje, zda modul runtime běží souběžně uvolňování paměti.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Určuje, jestli uvolňování paměti podporuje více skupin procesoru.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Určuje, zda modul common language runtime běží kolekce paměti na serveru.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady zabezpečení (CA) vydavatele přístupu kódu.|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovaného kódu k zachycení narušení přístupu a ostatní výjimky v poškozeném stavu.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Určuje, že identitu systému Windows není toku napříč asynchronní bodů, bez ohledu na nastavení tok pro kontext provádění na aktuální vlákno.|  
|[\<loadfromremotesources – >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Určuje, zda jsou načteny jako úplný vztah důvěryhodnosti sestavení ze vzdáleného zdroje.|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definuje element, který slouží ke konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci nastavení konfigurace `namedCache` instance.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá zásady zabezpečení (CA) přístupu starší verze kódu.|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravy vyvolání nesprávný platformy deklarace v době běhu za cenu pomalejší přechodů mezi spravováno a nespravovaného kódu.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá k výpočtu kódů hash pro pevné velikosti paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda.|  
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime použijí zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci napříč hranicemi domény aplikace.|  
|[\<Zkušební fáze >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Určuje podadresáře, které modul runtime prohledá při načítání sestavení.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Určuje, zda modul runtime aplikuje zásady vydavatele.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Určuje úplný název sestavení, které by měl být dynamicky načíst, pokud je použít částečný název.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Tato kontrola se optimalizuje pro satelitní sestavení.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Odebere položku s názvem mezipaměti z `namedCaches` kolekci pro mezipaměť.|  
|[\<runtime>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Obsahuje informace o sestavení – vazby a chování uvolňování paměti.|  
|[\<shadowCopyTimeStampVerification>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Určuje, jestli stínové kopírování sestavení používá výchozí chování při spouštění počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spouštění starší verze rozhraní .NET Framework.|  
|[\<supportPortability – >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementace rozhraní .NET Framework zakázáním výchozí chování, která zpracovává sestavení jako ekvivalentní pro účely přenositelnost aplikace.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci pro mezipaměť v paměti objektu výchozí.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Určuje, zda úloha neošetřené výjimky by měl ukončit spuštěných procesů.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Určuje, zda modul runtime používá starší verze formátování pro <xref:System.TimeSpan> hodnoty.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Určuje, zda modul common language runtime používá starší verze 64bitový kompilátor JIT pro kompilaci za běhu.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime vypočte hash – kódy pro řetězce na na základě domény aplikace.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Vyžaduje, aby použil modulu runtime velikosti explicitní zásobníku při vytváření určitých vláken, používá interně, namísto výchozí velikost zásobníku.|  
  
## <a name="see-also"></a>Viz také  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Postupy: zakázat souběžná kolekce paměti](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)  
 [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
