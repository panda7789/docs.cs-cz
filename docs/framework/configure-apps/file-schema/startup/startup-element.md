---
title: '&lt;Po spuštění&gt; – Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4d39dc28082fbed932a60228ac216f2f700c2e9f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43734704"
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="18531-102">&lt;Po spuštění&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="18531-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="18531-103">Určuje informace o spuštění modulu runtime jazyka common.</span><span class="sxs-lookup"><span data-stu-id="18531-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="18531-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="18531-104">\<configuration></span></span>  
<span data-ttu-id="18531-105">\<Po spuštění ></span><span class="sxs-lookup"><span data-stu-id="18531-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18531-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18531-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18531-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="18531-107">Attributes and Elements</span></span>  
 <span data-ttu-id="18531-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="18531-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18531-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="18531-109">Attributes</span></span>  
  
|<span data-ttu-id="18531-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="18531-110">Attribute</span></span>|<span data-ttu-id="18531-111">Popis</span><span class="sxs-lookup"><span data-stu-id="18531-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="18531-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="18531-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="18531-113">Určuje, jestli se má povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime, nebo použít [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] Zásady aktivace.</span><span class="sxs-lookup"><span data-stu-id="18531-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="18531-114">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="18531-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="18531-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="18531-115">Value</span></span>|<span data-ttu-id="18531-116">Popis</span><span class="sxs-lookup"><span data-stu-id="18531-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="18531-117">Povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime pro zvolený runtime, která je k vytvoření vazby techniky aktivace starší verzi modulu runtime (například [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) do modulu runtime, zvolit z konfiguračního souboru místo omezení je v modulu CLR verze 2.0.</span><span class="sxs-lookup"><span data-stu-id="18531-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="18531-118">Proto pokud je zvolená verze modulu CLR 4 nebo novější z konfiguračního souboru, sestavení ve smíšeném režimu vytvořených v dřívějších verzích rozhraní .NET Framework jsou načtené na zvolené verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="18531-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="18531-119">Pokud tuto hodnotu nastavíte brání CLR verze 1.1 nebo CLR verze 2.0 načtení do stejného procesu efektivně zákaz funkce vnitroprocesové vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="18531-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="18531-120">Použít výchozí zásady aktivace pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a později, což je povolit starší modul runtime techniky aktivace pro načtení modulu CLR verze 1.1 nebo 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="18531-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="18531-121">Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, není-li, kterými byly vytvořeny pomocí rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="18531-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="18531-122">Tato hodnota je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="18531-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18531-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="18531-123">Child Elements</span></span>  
  
|<span data-ttu-id="18531-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="18531-124">Element</span></span>|<span data-ttu-id="18531-125">Popis</span><span class="sxs-lookup"><span data-stu-id="18531-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="18531-126">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="18531-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="18531-127">Určuje, že aplikace podporuje pouze verze 1.0 modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="18531-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="18531-128">Používejte aplikace sestavené s modulem runtime verze 1.1 nebo vyšší  **\<supportedRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="18531-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="18531-129">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="18531-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="18531-130">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="18531-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="18531-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="18531-131">Parent Elements</span></span>  
  
|<span data-ttu-id="18531-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="18531-132">Element</span></span>|<span data-ttu-id="18531-133">Popis</span><span class="sxs-lookup"><span data-stu-id="18531-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18531-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18531-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18531-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18531-135">Remarks</span></span>  
 <span data-ttu-id="18531-136">**\<SupportedRuntime >** element by měl být použit všemi aplikacemi sestavenými pomocí verze 1.1 nebo novější modul runtime.</span><span class="sxs-lookup"><span data-stu-id="18531-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="18531-137">Aplikace sestavené s podporou pouze verze 1.0 modulu runtime musí použít  **\<requiredRuntime >** elementu.</span><span class="sxs-lookup"><span data-stu-id="18531-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="18531-138">Ignoruje při spuštění kódu pro aplikace hostované v aplikaci Internet Explorer  **\<spuštění >** elementu a jeho podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="18531-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="18531-139">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="18531-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="18531-140">Tento atribut je užitečné, pokud vaše aplikace používá starší verzi aktivační cesty, jako [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete, aby tyto cesty k aktivaci místo starší verzi modulu CLR verze 4 nebo pokud je vaše aplikace sestavován [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale má závislost na sestavení ve smíšeném režimu, vytvořené ve starší verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18531-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="18531-141">V těchto scénářích, nastavte atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="18531-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="18531-142">Nastavením atributu na `true` brání načtení do stejného procesu efektivně zákaz funkce vedle sebe v procesu CLR verze 1.1 nebo CLR verze 2.0 (viz [spuštění vedle sebe pro spolupráci s COM](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="18531-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="18531-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="18531-143">Example</span></span>  
 <span data-ttu-id="18531-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="18531-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="18531-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="18531-145">See Also</span></span>  
 [<span data-ttu-id="18531-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="18531-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="18531-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="18531-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="18531-148">\<PaveOver > Určení verze modulu Runtime, která k použití</span><span class="sxs-lookup"><span data-stu-id="18531-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="18531-149">Spuštění vedle sebe pro zprostředkovatele komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="18531-149">Side-by-Side Execution for COM Interop</span></span>](https://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="18531-150">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="18531-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
