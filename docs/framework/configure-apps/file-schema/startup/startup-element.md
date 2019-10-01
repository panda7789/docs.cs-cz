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
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699419"
---
# <a name="startup-element"></a><span data-ttu-id="ddfba-102">@no__t – element > 0startup</span><span class="sxs-lookup"><span data-stu-id="ddfba-102">\<startup> element</span></span>

<span data-ttu-id="ddfba-103">Určuje informace o spuštění společného jazykového modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ddfba-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="ddfba-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="ddfba-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="ddfba-105">&nbsp; @ no__t-1 **\<startup >**</span><span class="sxs-lookup"><span data-stu-id="ddfba-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="ddfba-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddfba-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ddfba-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ddfba-107">Attributes and elements</span></span>

 <span data-ttu-id="ddfba-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ddfba-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ddfba-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="ddfba-109">Attributes</span></span>

|<span data-ttu-id="ddfba-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="ddfba-110">Attribute</span></span>|<span data-ttu-id="ddfba-111">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfba-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="ddfba-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="ddfba-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="ddfba-113">Určuje, jestli se má povolit zásada aktivace modulu runtime .NET Framework 2,0 nebo jestli se mají používat zásady aktivace .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ddfba-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ddfba-114">useLegacyV2RuntimeActivationPolicy – atribut</span><span class="sxs-lookup"><span data-stu-id="ddfba-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="ddfba-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ddfba-115">Value</span></span>|<span data-ttu-id="ddfba-116">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfba-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="ddfba-117">Povolit zásady aktivace modulu runtime .NET Framework 2,0 pro zvolený modul runtime, který je vázán na modul runtime, který se vybere z konfiguračního souboru (například [funkce CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)), namísto capping v modulu CLR verze 2,0.</span><span class="sxs-lookup"><span data-stu-id="ddfba-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="ddfba-118">Proto pokud je CLR verze 4 nebo novější zvolen z konfiguračního souboru, jsou sestavení se smíšeným režimem vytvořená se staršími verzemi .NET Framework načtena se zvolenou verzí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ddfba-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="ddfba-119">Nastavením této hodnoty zabráníte načtení CLR verze 1,1 nebo CLR verze 2,0 do stejného procesu a efektivně tak zakážete souběžnou funkci v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="ddfba-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="ddfba-120">Použijte výchozí zásady aktivace pro .NET Framework 4 a novější, což znamená, že je možné do procesu načíst modul CLR verze 1,1 nebo 2,0.</span><span class="sxs-lookup"><span data-stu-id="ddfba-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="ddfba-121">Nastavení této hodnoty zabrání načtení sestavení se smíšeným režimem do .NET Framework 4 nebo novějším, pokud se nevytvořila s .NET Framework 4 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="ddfba-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="ddfba-122">Tato hodnota je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="ddfba-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ddfba-123">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="ddfba-123">Child elements</span></span>

|<span data-ttu-id="ddfba-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ddfba-124">Element</span></span>|<span data-ttu-id="ddfba-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfba-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ddfba-126">@no__t – 1requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddfba-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="ddfba-127">Určuje, že aplikace podporuje pouze verzi 1,0 modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="ddfba-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="ddfba-128">Aplikace sestavené pomocí modulu runtime verze 1,1 nebo novější by měly používat **> prvek \<supportedRuntime** .</span><span class="sxs-lookup"><span data-stu-id="ddfba-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="ddfba-129">@no__t – 1supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddfba-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="ddfba-130">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="ddfba-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ddfba-131">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="ddfba-131">Parent elements</span></span>

|<span data-ttu-id="ddfba-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="ddfba-132">Element</span></span>|<span data-ttu-id="ddfba-133">Popis</span><span class="sxs-lookup"><span data-stu-id="ddfba-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ddfba-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddfba-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ddfba-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddfba-135">Remarks</span></span>

 <span data-ttu-id="ddfba-136">Prvek **> \<supportedRuntime** by měl být používán všemi aplikacemi sestavenými pomocí verze 1,1 nebo novějšího modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="ddfba-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="ddfba-137">Aplikace sestavené pro podporu pouze verze 1,0 modulu runtime musí používat prvek **\<requiredRuntime >** .</span><span class="sxs-lookup"><span data-stu-id="ddfba-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="ddfba-138">Spouštěcí kód pro aplikaci hostovanou v aplikaci Microsoft Internet Explorer ignoruje prvek **\<startup >** a jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="ddfba-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="ddfba-139">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="ddfba-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="ddfba-140">Tento atribut je užitečný, pokud vaše aplikace používá starší aktivační cesty, jako je [funkce CorBindToRuntimeEx –](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), a vy chcete, aby tyto cesty aktivovaly verzi 4 CLR namísto dřívější verze, nebo pokud je vaše aplikace sestavená pomocí rozhraní .NET. Rozhraní 4, ale má závislost na sestavení se smíšeným režimem sestavené pomocí dřívější verze .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ddfba-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="ddfba-141">V těchto scénářích nastavte atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="ddfba-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="ddfba-142">Nastavení atributu na `true` zabraňuje modulu CLR verze 1,1 nebo CLR verze 2,0 v načtení do stejného procesu a efektivně tak vypíná souběžné funkce v rámci procesu (viz [Souběžné spouštění pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span><span class="sxs-lookup"><span data-stu-id="ddfba-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="ddfba-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddfba-143">Example</span></span>

 <span data-ttu-id="ddfba-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ddfba-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ddfba-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddfba-145">See also</span></span>

- [<span data-ttu-id="ddfba-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="ddfba-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ddfba-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ddfba-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ddfba-148">Postupy: Konfigurace aplikace pro podporu .NET Framework 4 nebo novějších verzí</span><span class="sxs-lookup"><span data-stu-id="ddfba-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="ddfba-149">[Souběžné spouštění pro zprostředkovatele komunikace s objekty COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ddfba-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="ddfba-150">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="ddfba-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
