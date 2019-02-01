---
title: <startup> – element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: cc261097593150583072ab796df9de8edea5ca6e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55280199"
---
# <a name="startup-element"></a><span data-ttu-id="da1f6-102">\<Po spuštění > – element</span><span class="sxs-lookup"><span data-stu-id="da1f6-102">\<startup> element</span></span>

<span data-ttu-id="da1f6-103">Určuje informace o spuštění modulu runtime jazyka common.</span><span class="sxs-lookup"><span data-stu-id="da1f6-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="da1f6-104">\<configuration> \<startup></span><span class="sxs-lookup"><span data-stu-id="da1f6-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="da1f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da1f6-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="da1f6-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="da1f6-106">Attributes and elements</span></span>

 <span data-ttu-id="da1f6-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="da1f6-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="da1f6-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="da1f6-108">Attributes</span></span>

|<span data-ttu-id="da1f6-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="da1f6-109">Attribute</span></span>|<span data-ttu-id="da1f6-110">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f6-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="da1f6-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="da1f6-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="da1f6-112">Určuje, jestli se má povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime, nebo použít [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] Zásady aktivace.</span><span class="sxs-lookup"><span data-stu-id="da1f6-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="da1f6-113">atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="da1f6-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="da1f6-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="da1f6-114">Value</span></span>|<span data-ttu-id="da1f6-115">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f6-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="da1f6-116">Povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime pro zvolený runtime, která je k vytvoření vazby techniky aktivace starší verzi modulu runtime (například [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) do modulu runtime, zvolit z konfiguračního souboru místo omezení je v modulu CLR verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="da1f6-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="da1f6-117">Proto pokud je zvolená verze modulu CLR 4 nebo novější z konfiguračního souboru, sestavení ve smíšeném režimu vytvořených v dřívějších verzích rozhraní .NET Framework jsou načtené na zvolené verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="da1f6-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="da1f6-118">Pokud tuto hodnotu nastavíte brání CLR verze 1.1 nebo CLR verze 2.0 načtení do stejného procesu efektivně zákaz funkce vnitroprocesové vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="da1f6-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="da1f6-119">Použít výchozí zásady aktivace pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a později, což je povolit starší modul runtime techniky aktivace pro načtení modulu CLR verze 1.1 nebo 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="da1f6-119">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="da1f6-120">Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, není-li, kterými byly vytvořeny pomocí rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="da1f6-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="da1f6-121">Tato hodnota je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="da1f6-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="da1f6-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="da1f6-122">Child elements</span></span>

|<span data-ttu-id="da1f6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="da1f6-123">Element</span></span>|<span data-ttu-id="da1f6-124">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f6-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="da1f6-125">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="da1f6-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="da1f6-126">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="da1f6-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="da1f6-127">Používejte aplikace sestavené s modulem runtime verze 1.1 nebo vyšší  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="da1f6-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="da1f6-128">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="da1f6-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="da1f6-129">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="da1f6-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="da1f6-130">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="da1f6-130">Parent elements</span></span>

|<span data-ttu-id="da1f6-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="da1f6-131">Element</span></span>|<span data-ttu-id="da1f6-132">Popis</span><span class="sxs-lookup"><span data-stu-id="da1f6-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="da1f6-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da1f6-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="da1f6-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da1f6-134">Remarks</span></span>

 <span data-ttu-id="da1f6-135">**\<SupportedRuntime >** element by měl být použit všemi aplikacemi sestavenými pomocí verze 1.1 nebo novější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="da1f6-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="da1f6-136">Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="da1f6-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="da1f6-137">Ignoruje při spuštění kódu pro aplikace hostované v aplikaci Internet Explorer  **\<spuštění >** elementu a jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="da1f6-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="da1f6-138">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="da1f6-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="da1f6-139">Tento atribut je užitečné, pokud vaše aplikace používá starší verzi aktivační cesty, jako [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty k aktivaci místo starší verzi modulu CLR verze 4 nebo pokud je vaše aplikace sestavován [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale má závislost na sestavení ve smíšeném režimu, vytvořené ve starší verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da1f6-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="da1f6-140">V těchto scénářích, nastavte atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="da1f6-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="da1f6-141">Nastavením atributu na `true` brání načtení do stejného procesu efektivně zákaz funkce vedle sebe v procesu CLR verze 1.1 nebo CLR verze 2.0 (viz [spuštění vedle sebe pro spolupráci s COM](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="da1f6-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>

## <a name="example"></a><span data-ttu-id="da1f6-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="da1f6-142">Example</span></span>

 <span data-ttu-id="da1f6-143">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="da1f6-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="da1f6-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da1f6-144">See also</span></span>

- [<span data-ttu-id="da1f6-145">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="da1f6-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="da1f6-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="da1f6-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="da1f6-147">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="da1f6-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [<span data-ttu-id="da1f6-148">Spuštění vedle sebe pro zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="da1f6-148">Side-by-Side Execution for COM Interop</span></span>](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)
- [<span data-ttu-id="da1f6-149">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="da1f6-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)