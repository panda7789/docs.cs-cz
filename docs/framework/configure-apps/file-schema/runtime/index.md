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
# <a name="run-time-settings-schema"></a><span data-ttu-id="15d6f-102">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="15d6f-102">Run-time settings schema</span></span>

<span data-ttu-id="15d6f-103">Běhové nastavení používá modul CLR (Common Language Runtime) ke konfiguraci aplikací, které cílí na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15d6f-103">Run-time settings are used by the common language runtime to configure applications that target the .NET Framework.</span></span>

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a><span data-ttu-id="15d6f-104">\<runtime>Oddíl a jeho nadřazené a podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="15d6f-104">The \<runtime> section and its parent and child elements</span></span>

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

## <a name="alphabetical-list-of-runtime-elements"></a><span data-ttu-id="15d6f-105">Abecední seznam \<runtime> elementů</span><span class="sxs-lookup"><span data-stu-id="15d6f-105">Alphabetical list of \<runtime> elements</span></span>

|<span data-ttu-id="15d6f-106">Prvek</span><span class="sxs-lookup"><span data-stu-id="15d6f-106">Element</span></span>|<span data-ttu-id="15d6f-107">Description</span><span class="sxs-lookup"><span data-stu-id="15d6f-107">Description</span></span>|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="15d6f-108">Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-108">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="15d6f-109">Určuje, že identita Windows má vždycky tok napříč asynchronními body bez ohledu na to, jak byla provedena zosobnění.</span><span class="sxs-lookup"><span data-stu-id="15d6f-109">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="15d6f-110">Definuje jeden nebo více přepínačů používaných <xref:System.AppContext> třídou k poskytnutí mechanismu odhlášení pro nové funkce.</span><span class="sxs-lookup"><span data-stu-id="15d6f-110">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="15d6f-111">Určuje sestavení, které poskytuje správce aplikační domény pro výchozí doménu aplikace v procesu.</span><span class="sxs-lookup"><span data-stu-id="15d6f-111">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="15d6f-112">Určuje typ, který slouží jako správce aplikační domény pro výchozí doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d6f-112">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="15d6f-113">Instruuje modul runtime za účelem shromažďování statistik o všech doménách aplikace v procesu po dobu životního cyklu procesu.</span><span class="sxs-lookup"><span data-stu-id="15d6f-113">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="15d6f-114">Obsahuje informace o přesměrování verze sestavení a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-114">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|<span data-ttu-id="15d6f-115">Obsahuje identifikační informace o sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-115">Contains identifying information about an assembly.</span></span>|
|[\<bindingRedirect>](bindingredirect-element.md)|<span data-ttu-id="15d6f-116">Přesměruje jednu verzi sestavení k jiné.</span><span class="sxs-lookup"><span data-stu-id="15d6f-116">Redirects one assembly version to another.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="15d6f-117">Určuje, zda má být vynecháno ověřování silných názvů pro důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-117">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="15d6f-118">Vymaže `namedCaches` kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-118">Clears the `namedCaches` collection for a memory cache.</span></span>|
|[\<codeBase>](codebase-element.md)|<span data-ttu-id="15d6f-119">Určuje, kde modul runtime může najít sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-119">Specifies where the runtime can find an assembly.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="15d6f-120">Určuje, že modul runtime má při provádění porovnávání řetězců používat starší chování řazení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-120">Specifies that the runtime should use legacy sorting behavior when performing string comparisons</span></span>|
|[\<dependentAssembly>](dependentassembly-element.md)|<span data-ttu-id="15d6f-121">Zapouzdřuje pro jednotlivá sestavení zásady vazeb a umístění sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-121">Encapsulates binding policy and assembly location for each assembly.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="15d6f-122">Určuje, zda modul runtime vyhledává sestavení v adresářích určených proměnnou prostředí mechanismu DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="15d6f-122">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="15d6f-123">Určuje, jestli je zakázané ukládání neúspěšných vazeb do mezipaměti, což je výchozí chování v .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="15d6f-123">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="15d6f-124">Určuje, zda je plný zásobník vláken potvrzen při spuštění vlákna.</span><span class="sxs-lookup"><span data-stu-id="15d6f-124">Specifies whether the full thread stack is committed when a thread starts.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="15d6f-125">Určuje, zda výchozí chování, které umožňuje hostiteli modulu runtime přepsat nastavení konfigurace pro doménu aplikace, je zakázáno.</span><span class="sxs-lookup"><span data-stu-id="15d6f-125">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="15d6f-126">Určuje, zda metody analýzy data a času používají upravenou sadu pravidel k analýze řetězců data, které obsahují pouze označení den, měsíc, hodina a AM/PM.</span><span class="sxs-lookup"><span data-stu-id="15d6f-126">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="15d6f-127">Určuje, jestli se má vymáhat požadavek na konfiguraci počítače, který kryptografické algoritmy musí dodržovat Standard FIPS (Federal Information Processing Standards).</span><span class="sxs-lookup"><span data-stu-id="15d6f-127">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="15d6f-128">Určuje, jestli se má povolit trasování událostí pro Windows (ETW) pro události modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="15d6f-128">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="15d6f-129">Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.</span><span class="sxs-lookup"><span data-stu-id="15d6f-129">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="15d6f-130">Na 64bitových platformách povoluje pole, jejichž celková velikost je větší než 2 gigabajty (GB).</span><span class="sxs-lookup"><span data-stu-id="15d6f-130">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="15d6f-131">Určuje, zda modul runtime současně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-131">Specifies whether the runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="15d6f-132">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="15d6f-132">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="15d6f-133">Definuje spřažení mezi haldami GC a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="15d6f-133">Defines the affinity between GC heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="15d6f-134">Určuje počet hald/vláken, které se mají použít pro uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="15d6f-134">Specifies the number of heaps/threads to use for server garbage collection.</span></span>  |
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="15d6f-135">Určuje velikost prahové hodnoty, která způsobí, že objekty přejdou na haldu velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="15d6f-135">Specifies the threshold size that causes objects to go on the large object heap (LOH).</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="15d6f-136">Určuje, jestli se mají spřažení vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="15d6f-136">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="15d6f-137">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="15d6f-137">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="15d6f-138">Určuje, zda modul runtime používá zásady vydavatele CAS (Code Access Security).</span><span class="sxs-lookup"><span data-stu-id="15d6f-138">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="15d6f-139">Určuje, zda modul runtime umožňuje spravovanému kódu zachytit porušení přístupu a jiné poškozené výjimky stavu.</span><span class="sxs-lookup"><span data-stu-id="15d6f-139">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="15d6f-140">Určuje, že identita systému Windows není v rámci asynchronních bodů předávána bez ohledu na nastavení toku pro kontext spuštění v aktuálním vlákně.</span><span class="sxs-lookup"><span data-stu-id="15d6f-140">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="15d6f-141">Určuje, zda jsou sestavení ze vzdálených zdrojů načítána jako plná důvěryhodnost.</span><span class="sxs-lookup"><span data-stu-id="15d6f-141">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="15d6f-142">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="15d6f-142">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="15d6f-143">Obsahuje kolekci konfiguračních nastavení `namedCache` instance.</span><span class="sxs-lookup"><span data-stu-id="15d6f-143">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="15d6f-144">Určuje, zda modul runtime používá starší zásady zabezpečení přístupu kódu (CAS).</span><span class="sxs-lookup"><span data-stu-id="15d6f-144">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="15d6f-145">Určuje, zda modul runtime automaticky opravuje nesprávné deklarace volání platformy za běhu, a to za cenu pomalejších přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="15d6f-145">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="15d6f-146">Určuje, zda modul runtime používá k výpočtu kódů hash pro metodu pevnou velikost paměti <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="15d6f-146">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="15d6f-147">Určuje, že modul runtime bude používat zprostředkovatele komunikace s objekty COM namísto vzdálené komunikace napříč hranicemi aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="15d6f-147">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<probing>](probing-element.md)|<span data-ttu-id="15d6f-148">Určuje podadresáře, které modul runtime vyhledává při načítání sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-148">Specifies subdirectories that the runtime searches when loading assemblies.</span></span>|
|[\<publisherPolicy>](publisherpolicy-element.md)|<span data-ttu-id="15d6f-149">Určuje, zda modul runtime používá zásady vydavatele.</span><span class="sxs-lookup"><span data-stu-id="15d6f-149">Specifies whether the runtime applies publisher policy.</span></span>|
|[\<qualifyAssembly>](qualifyassembly-element.md)|<span data-ttu-id="15d6f-150">Určuje úplný název sestavení, které by mělo být dynamicky načteno při použití částečného názvu.</span><span class="sxs-lookup"><span data-stu-id="15d6f-150">Specifies the full name of the assembly that should be dynamically loaded when a partial name is used.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="15d6f-151">Optimalizuje sondu pro satelitní sestavení.</span><span class="sxs-lookup"><span data-stu-id="15d6f-151">Optimizes the probe for satellite assemblies.</span></span>|
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="15d6f-152">Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-152">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|
|[\<runtime>](runtime-element.md)|<span data-ttu-id="15d6f-153">Obsahuje informace o vazbách sestavení a chování uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-153">Contains information about assembly binding and the behavior of garbage collection.</span></span>|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="15d6f-154">Určuje, zda stínové kopírování používá výchozí chování při spuštění, které bylo zavedeno ve .NET Framework 4, nebo se vrátí k chování při spuštění starších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="15d6f-154">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="15d6f-155">Určuje, že aplikace může odkazovat na stejné sestavení ve dvou různých implementacích .NET Framework tím, že zakáže výchozí chování, které zpracovává sestavení jako ekvivalent pro účely přenositelnosti aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d6f-155">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="15d6f-156">Poskytuje informace o konfiguraci výchozí mezipaměti objektů v paměti.</span><span class="sxs-lookup"><span data-stu-id="15d6f-156">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="15d6f-157">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="15d6f-157">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="15d6f-158">Určuje, zda výjimky neošetřených úloh mají ukončit běžící proces.</span><span class="sxs-lookup"><span data-stu-id="15d6f-158">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|<span data-ttu-id="15d6f-159">Určuje, zda modul runtime používá pro hodnoty formátování starší verze <xref:System.TimeSpan> .</span><span class="sxs-lookup"><span data-stu-id="15d6f-159">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="15d6f-160">Určuje, zda modul CLR (Common Language Runtime) používá starší 64 kompilátor JIT pro kompilaci za běhu.</span><span class="sxs-lookup"><span data-stu-id="15d6f-160">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="15d6f-161">Určuje, zda modul runtime počítá kódy hash pro řetězce v jednotlivých doménách aplikace.</span><span class="sxs-lookup"><span data-stu-id="15d6f-161">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="15d6f-162">Požaduje, aby modul runtime při vytváření určitých vláken, která používá interně, místo výchozí velikosti zásobníku používal explicitní velikosti zásobníku.</span><span class="sxs-lookup"><span data-stu-id="15d6f-162">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

## <a name="see-also"></a><span data-ttu-id="15d6f-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="15d6f-163">See also</span></span>

- [<span data-ttu-id="15d6f-164">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="15d6f-164">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="15d6f-165">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="15d6f-165">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="15d6f-166">Přesměrování verzí sestavení</span><span class="sxs-lookup"><span data-stu-id="15d6f-166">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
