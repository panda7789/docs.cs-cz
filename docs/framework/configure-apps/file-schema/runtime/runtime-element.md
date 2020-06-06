---
title: Element <runtime>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430454"
---
# <a name="runtime-element"></a>Element \<runtime>

Poskytuje informace používané modulem CLR (Common Language Runtime) ke konfiguraci aplikací.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a>Syntaxe

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>Atributy a elementy

V následujících částech jsou popsány podřízené prvky a nadřazené prvky.

### <a name="attributes"></a>Atributy

Žádné

### <a name="child-elements"></a>Podřízené elementy

|Prvek|Description|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|Definuje jeden nebo více přepínačů používaných <xref:System.AppContext> třídou k poskytnutí mechanismu odhlášení pro nové funkce.|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|Instruuje modul runtime za účelem shromažďování statistik o všech doménách aplikace v procesu po dobu životního cyklu procesu.|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|Obsahuje informace o přesměrování verze sestavení a umístění sestavení.|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|Určuje, zda má být vynecháno ověřování silných názvů pro důvěryhodná sestavení.|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Určuje, že modul runtime má při provádění porovnávání řetězců používat starší chování řazení.|
|[\<developmentMode>](developmentmode-element.md)|Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Určuje, jestli je zakázané ukládání neúspěšných vazeb do mezipaměti, což je výchozí chování ve .NET Framework verze 2,0.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).|
|[\<etwEnable>](etwenable-element.md)|Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).|
|[\<gcConcurrent>](gcconcurrent-element.md)|Určuje, zda modul CLR (Common Language Runtime) současně spustí uvolňování paměti.|
|[\<GCCpuGroup>](gccpugroup-element.md)|Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Definuje spřažení mezi haldami uvolňování paměti a jednotlivými procesory.|
|[\<GCHeapCount>](gcheapcount-element.md)|Určuje počet hald/vláken, které se mají použít pro uvolňování paměti serveru.|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Určuje velikost prahové hodnoty, která způsobí, že systém uvolňování paměti vloží objekty do haldy velkých objektů.|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Určuje, jestli se mají spřažení vlákna uvolňování paměti serveru s procesory.|
|[\<gcServer>](gcserver-element.md)|Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|Určuje, zda modul runtime používá zásady vydavatele CAS (Code Access Security).|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|Určuje, zda modul runtime umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|Určuje, zda jsou sestavení ze vzdálených zdrojů načítána jako plná důvěryhodnost.|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|Určuje, zda modul runtime používá starší zásady zabezpečení přístupu kódu (CAS).|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|Určuje, že modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.|
|[\<relativeBindForResources>](relativebindforresources-element.md)|Optimalizuje sondu pro satelitní sestavení.|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.|
|[\<supportPortability>](supportportability-element.md)|Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|Poskytuje informace o konfiguraci výchozí mezipaměti objektů v paměti.|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|Určuje, zda modul runtime používá pro hodnoty formátování starší verze <xref:System.TimeSpan> .|
|[\<useLegacyJit>](uselegacyjit-element.md)|Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|Určuje, zda modul runtime počítá kódy hash pro řetězce v jednotlivých doménách aplikace.|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|Požaduje, aby modul runtime při vytváření určitých vláken, která používá interně, místo výchozí velikosti zásobníku používal explicitní velikosti zásobníku.|

### <a name="parent-elements"></a>Nadřazené elementy

|Prvek|Description|
|-------------|-----------------|
|`configuration`|Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.|

## <a name="remarks"></a>Poznámky

Podřízené prvky v [\<runtime>](runtime-element.md) oddílu konfiguračního souboru jsou používány modulem CLR (Common Language Runtime) ke konfiguraci způsobu, jakým se aplikace spouští. Například [\<gcServer>](gcserver-element.md) prvek určuje, zda systém uvolňování paměti používá uvolňování paměti pracovní stanice nebo uvolňování paměti serveru, [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) prvek určuje, zda modul CLR vypočítá kódy hash pro řetězec v každé aplikaci nebo doméně pro aplikaci a `AppContextSwitchOverrides` prvek umožňuje uživatelům knihovny, aby se přihlásili nebo odhlásili od změněných funkcí poskytovaných knihovnou.

Prvky v [\<runtime>](runtime-element.md) sekci jsou automaticky čteny modulem CLR (Common Language Runtime) při spuštění aplikace. Můžete také definovat konfigurační soubor pro doménu aplikace, která není výchozí, zadáním jeho názvu <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> Vlastnosti. jeho nastavení je automaticky přečteno při načtení domény aplikace. V případě potřeby byste měli v případě nutnosti přímo číst nastavení v [\<runtime>](runtime-element.md) části konfiguračního souboru aplikace.

## <a name="see-also"></a>Viz také

- [Schéma nastavení modulu runtime](index.md)
- [Schéma konfiguračního souboru](../index.md)
