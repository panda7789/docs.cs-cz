---
title: Schéma nastavení běhového prostředí
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
ms.openlocfilehash: d5af9f3299b48d431b43566c11610d745167b60b
ms.sourcegitcommit: 0a798a7e9680e2d0a5a81a3eaa203870ea782883
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/03/2020
ms.locfileid: "74431061"
---
# <a name="run-time-settings-schema"></a>Schéma nastavení běhového prostředí

Běhové nastavení používá modul CLR (Common Language Runtime) ke konfiguraci aplikací, které cílí na .NET Framework.

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<runtime>Oddíl a jeho nadřazené a podřízené prvky

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy>](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<probing>](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<supportPortability>](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCHeapCount>](gcheapcount-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCLOHThreshold>](gclohthreshold-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCNoAffinitize>](gcnoaffinitize-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache>](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches>](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<add>](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<clear>](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<remove>](remove-element-for-namedcaches.md)

## <a name="alphabetical-list-of-runtime-elements"></a>Abecední seznam \<runtime> elementů

|Prvek|Description|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínačů používaných <xref:System.AppContext> třídou k poskytnutí mechanismu odhlášení pro nové funkce.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Instruuje modul runtime za účelem shromažďování statistik o všech doménách aplikace v procesu po dobu životního cyklu procesu.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|Obsahuje identifikační informace o sestavení.|
|[\<bindingRedirect>](bindingredirect-element.md)|Přesměruje jednu verzi sestavení k jiné.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Určuje, zda má být vynecháno ověřování silných názvů pro důvěryhodná sestavení.|
|[\<clear>](clear-element-for-namedcaches.md)|Vymaže `namedCaches` kolekci mezipaměti paměti.|
|[\<codeBase>](codebase-element.md)|Určuje, kde modul runtime může najít sestavení.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Určuje, že modul runtime má při provádění porovnávání řetězců používat starší chování řazení.|
|[\<dependentAssembly>](dependentassembly-element.md)|Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.|
|[\<developmentMode>](developmentmode-element.md)|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Určuje, jestli je zakázané ukládání neúspěšných vazeb do mezipaměti, což je výchozí chování v .NET Framework 2,0.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).|
|[\<etwEnable>](etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Určuje, zda modul runtime současně spustí uvolňování paměti.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Definuje spřažení mezi haldami GC a jednotlivými procesory.|
|[\<GCHeapCount>](gcheapcount-element.md)|Určuje počet hald/vláken, které se mají použít pro uvolňování paměti serveru.  |
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Určuje velikost prahové hodnoty, která způsobí, že objekty přejdou na haldu velkých objektů (LOH).|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Určuje, jestli se mají spřažení vlákna GC serveru pomocí procesorů.|
|[\<gcServer>](gcserver-element.md)|Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady vydavatele CAS (Code Access Security).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Určuje, zda jsou sestavení ze vzdálených zdrojů načítána jako plná důvěryhodnost.|
|[\<memoryCache>](memorycache-element-cache-settings.md)|Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Obsahuje kolekci konfiguračních nastavení `namedCache` instance.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá starší zásady zabezpečení přístupu kódu (CAS).|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.|
|[\<probing>](probing-element.md)|Určuje podadresáře, které modul runtime vyhledává při načítání sestavení.|
|[\<publisherPolicy>](publisherpolicy-element.md)|Určuje, zda modul runtime používá zásady vydavatele.|
|[\<qualifyAssembly>](qualifyassembly-element.md)|Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optimalizuje sondu pro satelitní sestavení.|
|[\<remove>](remove-element-for-namedcaches.md)|Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.|
|[\<runtime>](runtime-element.md)|Obsahuje informace o vazbách sestavení a chování uvolňování paměti.|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci výchozí mezipaměti objektů v paměti.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|Určuje, zda modul runtime používá pro hodnoty formátování starší verze <xref:System.TimeSpan> .|
|[\<useLegacyJit>](uselegacyjit-element.md)|Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime počítá kódy hash pro řetězce v jednotlivých doménách aplikace.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Požaduje, aby modul runtime při vytváření určitých vláken, která používá interně, místo výchozí velikosti zásobníku používal explicitní velikosti zásobníku.|

## <a name="see-also"></a>Viz také

- [Schéma konfiguračního souboru](../index.md)
- [Zakázání souběžného uvolňování paměti](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [Přesměrování verzí sestavení](../../redirect-assembly-versions.md)
