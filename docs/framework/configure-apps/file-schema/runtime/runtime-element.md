---
title: '&lt;modul runtime&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: fb050a8d73c42094caf83ba00c5dfc2e4d472723
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748669"
---
# <a name="ltruntimegt-element"></a>&lt;modul runtime&gt; – Element
Poskytuje informace, které používá modul common language runtime ke konfiguraci aplikací.  
  
 \<Konfigurace >  
\<modul runtime >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují podřízené elementy a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Určuje, že Windows identity vždy přeteče asynchronní bodů, bez ohledu na to, jak byla provedena zosobnění.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínač používaný <xref:System.AppContext> třídy poskytují mechanismus vyjádření výslovného nesouhlasu pro nové funkce.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce domény aplikace pro výchozí doméně aplikace v procesu.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce domény aplikace pro výchozí doménu aplikace.|  
|[\<appdomainresourcemonitoring – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Dá pokyn modulu runtime ke shromažďování statistik na všechny domény aplikace v procesu po dobu trvání procesu.|  
|[\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Určuje, zda by měl obejít ověřování silných názvů pro důvěryhodné sestavení.|  
|[\<Compatsortnlsversion – >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Určuje, při porovnání řetězců měli použít modul runtime chování pro starší verze řazení.|  
|[\<developmentmode – >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Určuje, zda běhové prostředí vyhledává sestavení v zadaném proměnnou prostředí DEVPATH adresáře.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Určuje, jestli ukládání do mezipaměti selhání vazby, což je výchozí chování v rozhraní .NET Framework verze 2.0, je zakázaná.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Určuje, jestli je úplná vlákno zásobníku potvrzeny při spuštění vlákna.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Určuje, zda je výchozí chování, které je umožnit runtime hostitelů pro přepsání nastavení konfigurace pro doménu aplikace, zakázána.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Určuje, zda datum a čas analýza metody použít upravenou sadu pravidel analyzovat data řetězce, které obsahují pouze den, měsíc, hodinu a označení dop. / odp.|  
|[\<enforcefipspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Určuje, jestli vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu s na zpracování standardů FIPS (Federal Information).|  
|[\<etwenable – >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro běžné události modulu runtime jazyka.|  
|[\<forceperformancecounteruniquesharedmemoryreads – >](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, zda PerfCounter.dll používá nastavení registru CategoryOptions v rozhraní .NET Framework verze 1.1 aplikaci a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Určuje, zda modul common language runtime běží souběžně uvolňování paměti.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Určuje, jestli uvolňování paměti podporuje více skupin procesoru.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Určuje, zda modul common language runtime běží kolekce paměti na serveru.|  
|[\<generatePublisherEvidence >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady zabezpečení (CA) vydavatele přístupu kódu.|  
|[\<legacycorruptedstateexceptionspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovaného kódu k zachycení narušení přístupu a ostatní výjimky v poškozeném stavu.|  
|[\<legacyimpersonationpolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Určuje, že identitu systému Windows není toku napříč asynchronní bodů, bez ohledu na nastavení tok pro kontext provádění na aktuální vlákno.|  
|[\<loadfromremotesources – >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Určuje, zda jsou načteny jako úplný vztah důvěryhodnosti sestavení ze vzdáleného zdroje.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá zásady zabezpečení (CA) přístupu starší verze kódu.|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravy vyvolání nesprávný platformy deklarace v době běhu za cenu pomalejší přechodů mezi spravováno a nespravovaného kódu.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá k výpočtu kódů hash pro pevné velikosti paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metoda.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime použijí zprostředkovatel komunikace s objekty COM místo vzdálenou komunikaci napříč hranicemi domény aplikace.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Tato kontrola se optimalizuje pro satelitní sestavení.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Určuje, jestli stínové kopírování sestavení používá výchozí chování při spouštění počínaje [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spouštění starší verze rozhraní .NET Framework.|  
|[\<supportPortability – >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementace rozhraní .NET Framework zakázáním výchozí chování, která zpracovává sestavení jako ekvivalentní pro účely přenositelnost aplikace.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci pro mezipaměť v paměti objektu výchozí.|  
|[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Určuje, zda modul runtime distribuuje spravovaných vláken ve všech skupinách procesoru.|  
|[\<Throwunobservedtaskexceptions – >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Určuje, zda úloha neošetřené výjimky by měl ukončit spuštěných procesů.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Určuje, zda modul runtime používá starší verze formátování pro <xref:System.TimeSpan> hodnoty.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Určuje, zda modul common language runtime používá starší verze 64bitový kompilátor JIT pro kompilaci za běhu.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime vypočte hash – kódy pro řetězce na na základě domény aplikace.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Vyžaduje, aby použil modulu runtime velikosti explicitní zásobníku při vytváření určitých vláken, používá interně, namísto výchozí velikost zásobníku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Podřízené elementy v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru jsou používány modul common language runtime nakonfigurovat, jak je aplikace spuštěna. Například [ \<gcserver – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element určuje, zda má systém uvolňování používá uvolňování paměti pracovních stanic nebo kolekce paměti na serveru, [ \< Userandomizedstringhashalgorithm – >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) element určuje, zda modul common language runtime vypočte hash – kódy pro řetězec na jednotlivých aplikací, nebo na základě pro aplikační doménu a `AppContextSwitchOverrides` element umožňuje uživatelům knihovny Pokud chcete vyjádřit výslovný souhlas nebo vyjádření výslovného nesouhlasu změněné funkce poskytované službou knihovny.  
  
 Prvky v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části jsou automaticky číst modul common language runtime při spuštění aplikace. Můžete také definovat konfiguračního souboru pro doménu aplikace jiné než výchozí zadáním názvu do <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> vlastnost; jeho nastavení jsou přečtena automaticky při načtení domény aplikace. Zřídka, pokud někdy, měli byste potřeba přímo číst nastavení v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu v konfiguračním souboru aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
