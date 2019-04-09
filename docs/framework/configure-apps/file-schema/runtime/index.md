---
title: Schéma nastavení běhového prostředí
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21c24040f7d093aa72738957316a4219539510c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59076936"
---
# <a name="runtime-settings-schema"></a>Schéma nastavení běhového prostředí
Nastavení modulu runtime se používají modulem common language runtime ke konfiguraci aplikací využívajících rozhraní .NET Framework.  

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<Runtime > části a její nadřazené a podřízené prvky
  
[\<Konfigurace >](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
&nbsp;&nbsp;[\<modul runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<zjišťování >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment >](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Vymazat >](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)  
&nbsp;&nbsp;\<\runtime>  
\<\configuration >

## <a name="alphabetical-list-of-runtime-elements"></a>Abecední seznam \<runtime > elementy

|Prvek|Popis|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|Přidá pojmenované mezipaměti, aby `namedCaches` kolekce pro mezipaměť.|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínačů používané <xref:System.AppContext> třídě poskytnout mechanismus výslovného nesouhlasu pro nové funkce.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce domény aplikace pro výchozí domény aplikace.|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Dá pokyn modulu runtime ke shromažďování statistik na všech doménách aplikace v procesu po dobu trvání procesu.|  
|[\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|[\<assemblyIdentity>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblyidentity-element-for-runtime.md)|Obsahuje identifikační informace o sestavení.|  
|[\<bindingRedirect>](../../../../../docs/framework/configure-apps/file-schema/runtime/bindingredirect-element.md)|Přesměruje jednu verzi sestavení k jiné.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Určuje, zda by měl obejít ověřování silných názvů pro důvěryhodného sestavení.|  
|[\<clear>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekce pro mezipaměť.|  
|[\<codeBase>](../../../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md)|Určuje, kde najít sestavení modulu runtime.|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Určuje, že by měl modul runtime při porovnávání řetězců použít starší verzi chování řazení|  
|[\<dependentAssembly >](../../../../../docs/framework/configure-apps/file-schema/runtime/dependentassembly-element.md)|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Určuje, jestli ukládání do mezipaměti vazby selhání, což je výchozí chování [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)], je zakázaná.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Určuje, zda je zásobníku úplného vlákna potvrzeny při spuštění vlákna.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Určuje, zda je výchozí chování, které je umožnit hostitelský modul runtime pro přepsání nastavení konfigurace pro doménu aplikace, zakázáno.|  
|[\<EnableAmPmParseAdjustment >](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Určuje, zda analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Určuje, jestli chcete vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu se informace o zpracování normy FIPS (Federal).|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro common language runtime události.|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, jestli má PerfCounter.dll CategoryOptions nastavení registru v rozhraní .NET Framework verze 1.1 aplikace k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Určuje, zda modul runtime souběžně spustí uvolňování paměti.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Určuje, zda uvolňování podporuje více skupin procesorů.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Určuje, zda modul common language runtime spustí uvolnění paměti serveru.|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady aplikace publisher security (CAS) přístupu kódu.|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovanému kódu zachytit narušení přístupu a ostatní výjimky v poškozeném stavu.|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Určuje, že identita Windows není téct přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění pro aktuální vlákno.|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Určuje, zda jsou načteny při úplném vztahu důvěryhodnosti sestavení ze vzdáleného zdroje.|  
|[\<memoryCache>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.|  
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Obsahuje kolekci prvků konfigurace nastavení `namedCache` instance.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá starší verzi kódu zásady zabezpečení přístupu (CAS).|  
|[< netfx40_pinvokestackresilience – >](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravy nesprávné volání nespravovaného kódu deklarace v době běhu, za cenu pomalejší přechody mezi spravováno a nespravovaný kód.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá pro výpočet kódů hash pro pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|  
|[\<PreferComInsteadOfManagedRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime použije komunikace s objekty COM místo vzdálené komunikace přes hranice aplikačních domén.|  
|[\<zjišťování >](../../../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md)|Určuje podadresářů, které modul runtime prohledá při načítání sestavení.|  
|[\<publisherPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/publisherpolicy-element.md)|Určuje, zda modul runtime použije zásady vydavatele.|  
|[\<qualifyAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/qualifyassembly-element.md)|Určuje úplný název sestavení, které se mají dynamicky načíst při použití částečný název.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optimalizuje sondy pro satelitní sestavení.|  
|[\<remove>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|Odebere položku pojmenovanou mezipaměť z `namedCaches` kolekce pro mezipaměť.|  
|[\<modul runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Obsahuje informace o sestavení, vazby a chování uvolňování paměti.|  
|[\<shadowCopyTimeStampVerification>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Určuje, zda stínové kopírování sestavení použije výchozí chování při spouštění zavedený [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spuštění z dřívějších verzích rozhraní .NET Framework.|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích rozhraní .NET Framework zakázáním výchozího chování, které považuje za ekvivalent pro účely přenositelnosti aplikace sestavení.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci pro výchozí mezipaměti objektů v paměti do mezipaměti.|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěnému procesu.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|Určuje, zda modul runtime používá starší verzi formátování <xref:System.TimeSpan> hodnoty.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Určuje, zda modul common language runtime používá starší verzi 64bitového kompilátoru JIT kompilace just-in-time.|  
|[\<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime vypočítá hash kódy pro řetězce na základě domény aplikace.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Vyžaduje, aby modul runtime použil zásobníku explicitní velikost při vytváření příslušná vlákna, která používá interně, namísto výchozí velikost zásobníku.|  
  
## <a name="see-also"></a>Viz také:

- [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Chcete-li zakázat souběžné uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Přesměrování verzí sestavení](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)
