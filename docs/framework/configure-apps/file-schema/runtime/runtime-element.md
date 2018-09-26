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
ms.openlocfilehash: 0640b4c54b6f1429bce4947ec536352f240ca719
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47208643"
---
# <a name="ltruntimegt-element"></a>&lt;modul runtime&gt; – Element
Poskytuje informace, které slouží ke konfiguraci aplikací modulem common language runtime.  
  
 \<Konfigurace >  
\<modul runtime >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují podřízené prvky a nadřazené elementy.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|Určuje, že identita Windows vždy toky přes asynchronní body, bez ohledu na to, jak se provádí zosobnění.|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínačů používané <xref:System.AppContext> třídě poskytnout mechanismus výslovného nesouhlasu pro nové funkce.|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce domény aplikace ve výchozí doméně aplikace v procesu.|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce domény aplikace pro výchozí domény aplikace.|  
|[\<appdomainresourcemonitoring – >](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|Dá pokyn modulu runtime ke shromažďování statistik na všech doménách aplikace v procesu po dobu trvání procesu.|  
|[\<assemblybinding – >](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|Určuje, zda by měl obejít ověřování silných názvů pro důvěryhodného sestavení.|  
|[\<CompatSortNLSVersion >](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|Určuje, že má modul runtime při porovnávání řetězců použít starší verzi chování řazení.|  
|[\<developmentmode – >](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí DEVPATH.|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|Určuje, zda je zakázáno ukládání do mezipaměti selhání vazby, což je výchozí chování v rozhraní .NET Framework verze 2.0.|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|Určuje, zda je zásobníku úplného vlákna potvrzeny při spuštění vlákna.|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|Určuje, zda je výchozí chování, které je umožnit hostitelský modul runtime pro přepsání nastavení konfigurace pro doménu aplikace, zakázáno.|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|Určuje, zda analýzy metody data a času použít upravenou sadu pravidel k parsování řetězců kalendářních dat, které obsahují pouze den, měsíc, hodinu a označení dopoledne/odpoledne.|  
|[\<enforcefipspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|Určuje, jestli chcete vynutit požadavek konfigurace počítače, že kryptografické algoritmy musí být v souladu se informace o zpracování normy FIPS (Federal).|  
|[\<etwenable – >](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro common language runtime události.|  
|[\<forceperformancecounteruniquesharedmemoryreads – >](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, jestli má PerfCounter.dll CategoryOptions nastavení registru v rozhraní .NET Framework verze 1.1 aplikace k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|Určuje, zda modul common language runtime běží souběžně uvolňování paměti.|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|Určuje, zda uvolňování podporuje více skupin procesorů.|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|Určuje, zda modul common language runtime spustí uvolnění paměti serveru.|  
|[\<generatePublisherEvidence – >](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady aplikace publisher security (CAS) přístupu kódu.|  
|[\<legacycorruptedstateexceptionspolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovanému kódu zachytit narušení přístupu a ostatní výjimky v poškozeném stavu.|  
|[\<legacyimpersonationpolicy – >](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|Určuje, že identita Windows není téct přes asynchronní body, bez ohledu na nastavení toku pro kontext spuštění pro aktuální vlákno.|  
|[\<loadfromRemoteSources >](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|Určuje, zda jsou načteny při úplném vztahu důvěryhodnosti sestavení ze vzdáleného zdroje.|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá starší verzi kódu zásady zabezpečení přístupu (CAS).|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravy nesprávné volání nespravovaného kódu deklarace v době běhu, za cenu pomalejší přechody mezi spravováno a nespravovaný kód.|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá pro výpočet kódů hash pro pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> metody.|  
|[\<PreferComInsteadOfRemoting >](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime použije komunikace s objekty COM místo vzdálené komunikace přes hranice aplikačních domén.|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|Optimalizuje sondy pro satelitní sestavení.|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|Určuje, zda stínové kopírování sestavení použije výchozí chování při spouštění zavedený [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], nebo se vrátí do chování při spuštění z dřívějších verzích rozhraní .NET Framework.|  
|[\<supportPortability >](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích rozhraní .NET Framework zakázáním výchozího chování, které považuje za ekvivalent pro účely přenositelnosti aplikace sestavení.|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci pro výchozí mezipaměti objektů v paměti do mezipaměti.|  
|[< Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.|  
|[\<Throwunobservedtaskexceptions – >](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|Určuje, zda úloh neošetřené výjimky by měla ukončit spuštěnému procesu.|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|Určuje, zda modul runtime používá starší verzi formátování <xref:System.TimeSpan> hodnoty.|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|Určuje, zda modul common language runtime používá starší verzi 64bitového kompilátoru JIT kompilace just-in-time.|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime vypočítá hash kódy pro řetězce na základě domény aplikace.|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|Vyžaduje, aby modul runtime použil zásobníku explicitní velikost při vytváření příslušná vlákna, která používá interně, namísto výchozí velikost zásobníku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|  
  
## <a name="remarks"></a>Poznámky  
 Podřízené elementy v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru se používají modulem common language runtime ke konfiguraci, jak aplikaci spustí. Například [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element určuje, zda systému uvolňování paměti používá uvolnění paměti pracovní stanice nebo uvolnění paměti serveru, [ \< UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md) element určuje, zda modul common language runtime vypočítá hash kódy pro řetězce na každou aplikaci, nebo na základě domény na aplikaci a `AppContextSwitchOverrides` element umožňuje uživatelům knihovny vyjádřit výslovný souhlas nebo vyjádřit výslovný nesouhlas změněné funkce poskytované službou knihovny.  
  
 Prvky v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části jsou automaticky číst modul common language runtime při spuštění aplikace. Konfigurační soubor pro jiné než výchozí aplikační doménu můžete také definovat zadáním jeho název <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> vlastnost; jeho nastavení jsou přečtena automaticky při načtení domény aplikace. Jen zřídka, pokud někdy, měli byste třeba přímému čtení nastavení v [ \<runtime >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu v konfiguračním souboru aplikace.  
  
## <a name="see-also"></a>Viz také  
 [Schéma nastavení běhového prostředí](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Schéma konfiguračního souboru](../../../../../docs/framework/configure-apps/file-schema/index.md)
