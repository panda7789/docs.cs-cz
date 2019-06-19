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
ms.openlocfilehash: 022f0efbbb2e6e9a4ac9d3d7ddcc1fb1022cdbee
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169778"
---
# <a name="startup-element"></a><span data-ttu-id="d9f45-102">\<Po spuštění > – element</span><span class="sxs-lookup"><span data-stu-id="d9f45-102">\<startup> element</span></span>

<span data-ttu-id="d9f45-103">Určuje informace o spuštění modulu runtime jazyka common.</span><span class="sxs-lookup"><span data-stu-id="d9f45-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="d9f45-104">\<configuration> \<startup></span><span class="sxs-lookup"><span data-stu-id="d9f45-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="d9f45-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9f45-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d9f45-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d9f45-106">Attributes and elements</span></span>

 <span data-ttu-id="d9f45-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9f45-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d9f45-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d9f45-108">Attributes</span></span>

|<span data-ttu-id="d9f45-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d9f45-109">Attribute</span></span>|<span data-ttu-id="d9f45-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d9f45-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="d9f45-111">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="d9f45-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="d9f45-112">Určuje, zda chcete povolit zásady aktivace modulu runtime rozhraní .NET Framework 2.0 nebo použít zásady aktivace rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d9f45-112">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d9f45-113">atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d9f45-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="d9f45-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d9f45-114">Value</span></span>|<span data-ttu-id="d9f45-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d9f45-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="d9f45-116">Povolit zásady aktivace modulu runtime rozhraní .NET Framework 2.0 pro zvolený runtime, která je k vytvoření vazby techniky aktivace starší verzi modulu runtime (například [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) vybere z konfiguračního souboru modulu runtime z omezení je v modulu CLR verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="d9f45-116">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="d9f45-117">Proto pokud je zvolená verze modulu CLR 4 nebo novější z konfiguračního souboru, sestavení ve smíšeném režimu vytvořených v dřívějších verzích rozhraní .NET Framework jsou načtené na zvolené verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="d9f45-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="d9f45-118">Pokud tuto hodnotu nastavíte brání CLR verze 1.1 nebo CLR verze 2.0 načtení do stejného procesu efektivně zákaz funkce vnitroprocesové vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="d9f45-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="d9f45-119">Pomocí aktivace výchozí zásady pro rozhraní .NET Framework 4 a novější, což je povolit starší modul runtime techniky aktivace pro načtení modulu CLR verze 1.1 nebo 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="d9f45-119">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="d9f45-120">Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, není-li, kterými byly vytvořeny pomocí rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="d9f45-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="d9f45-121">Tato hodnota je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="d9f45-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d9f45-122">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d9f45-122">Child elements</span></span>

|<span data-ttu-id="d9f45-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9f45-123">Element</span></span>|<span data-ttu-id="d9f45-124">Popis</span><span class="sxs-lookup"><span data-stu-id="d9f45-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d9f45-125">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="d9f45-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="d9f45-126">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="d9f45-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="d9f45-127">Používejte aplikace sestavené s modulem runtime verze 1.1 nebo vyšší  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="d9f45-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="d9f45-128">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="d9f45-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="d9f45-129">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="d9f45-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d9f45-130">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d9f45-130">Parent elements</span></span>

|<span data-ttu-id="d9f45-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="d9f45-131">Element</span></span>|<span data-ttu-id="d9f45-132">Popis</span><span class="sxs-lookup"><span data-stu-id="d9f45-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d9f45-133">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9f45-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d9f45-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9f45-134">Remarks</span></span>

 <span data-ttu-id="d9f45-135">**\<SupportedRuntime >** element by měl být použit všemi aplikacemi sestavenými pomocí verze 1.1 nebo novější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="d9f45-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="d9f45-136">Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="d9f45-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="d9f45-137">Ignoruje při spuštění kódu pro aplikace hostované v aplikaci Internet Explorer  **\<spuštění >** elementu a jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="d9f45-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="d9f45-138">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="d9f45-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="d9f45-139">Tento atribut je užitečné, pokud vaše aplikace používá starší verzi aktivační cesty, jako [CorBindToRuntimeEx – funkce](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty k aktivaci místo starší verzi modulu CLR verze 4 nebo pokud je vaše aplikace sestavován rozhraní .NET Framework 4, ale obsahuje závislost na sestavení ve smíšeném režimu, vytvořené ve starší verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d9f45-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="d9f45-140">V těchto scénářích, nastavte atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="d9f45-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="d9f45-141">Nastavením atributu na `true` brání načtení do stejného procesu efektivně zákaz funkce vedle sebe v procesu CLR verze 1.1 nebo CLR verze 2.0 (viz [spuštění vedle sebe pro spolupráci s COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="d9f45-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="d9f45-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9f45-142">Example</span></span>

 <span data-ttu-id="d9f45-143">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="d9f45-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d9f45-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9f45-144">See also</span></span>

- [<span data-ttu-id="d9f45-145">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="d9f45-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d9f45-146">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d9f45-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d9f45-147">Postupy: Konfigurace aplikace pro podporu rozhraní .NET Framework 4 nebo novější verze</span><span class="sxs-lookup"><span data-stu-id="d9f45-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="d9f45-148">[Spuštění vedle sebe pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d9f45-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="d9f45-149">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="d9f45-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
