---
title: '&lt;spuštění&gt; – Element'
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
ms.openlocfilehash: 60699f0335bb35589341558800cfd64503d0aa0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748420"
---
# <a name="ltstartupgt-element"></a><span data-ttu-id="83c93-102">&lt;spuštění&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="83c93-102">&lt;startup&gt; Element</span></span>
<span data-ttu-id="83c93-103">Určuje common language runtime spuštění informace.</span><span class="sxs-lookup"><span data-stu-id="83c93-103">Specifies common language runtime startup information.</span></span>  
  
 <span data-ttu-id="83c93-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="83c93-104">\<configuration></span></span>  
<span data-ttu-id="83c93-105">\<spuštění ></span><span class="sxs-lookup"><span data-stu-id="83c93-105">\<startup></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c93-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83c93-106">Syntax</span></span>  
  
```xml  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83c93-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83c93-107">Attributes and Elements</span></span>  
 <span data-ttu-id="83c93-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83c93-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83c93-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="83c93-109">Attributes</span></span>  
  
|<span data-ttu-id="83c93-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="83c93-110">Attribute</span></span>|<span data-ttu-id="83c93-111">Popis</span><span class="sxs-lookup"><span data-stu-id="83c93-111">Description</span></span>|  
|---------------|-----------------|  
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="83c93-112">Nepovinný atribut.</span><span class="sxs-lookup"><span data-stu-id="83c93-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="83c93-113">Určuje, jestli se má povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime, nebo chcete použít [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] aktivace zásad.</span><span class="sxs-lookup"><span data-stu-id="83c93-113">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|  
  
## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="83c93-114">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="83c93-114">useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
  
|<span data-ttu-id="83c93-115">Hodnota</span><span class="sxs-lookup"><span data-stu-id="83c93-115">Value</span></span>|<span data-ttu-id="83c93-116">Popis</span><span class="sxs-lookup"><span data-stu-id="83c93-116">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="83c93-117">Povolit [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] Zásady aktivace modulu runtime pro vybraný modul runtime, který je pro vazbu techniky aktivace starší verze runtime (například [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) do výběru z konfiguračního souboru místo runtime omezení je na verze modulu CLR 2.0.</span><span class="sxs-lookup"><span data-stu-id="83c93-117">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="83c93-118">Proto pokud CLR verze 4 nebo novější je zvoleno z konfiguračního souboru, ve smíšeném režimu sestavení vytvořených ve starších verzích rozhraní .NET Framework se načetly na zvolené verzi CLR.</span><span class="sxs-lookup"><span data-stu-id="83c93-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="83c93-119">Nastavení této hodnoty zabraňuje CLR verze 1.1 nebo verze modulu CLR 2.0 načtení do stejně účinně zakázat funkci vedle sebe v procesu.</span><span class="sxs-lookup"><span data-stu-id="83c93-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|  
|`false`|<span data-ttu-id="83c93-120">Použít výchozí zásady aktivace pro [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] a novější, který je umožnit starší verze modulu runtime aktivace techniky načíst CLR verze 1.1 nebo 2.0 do procesu.</span><span class="sxs-lookup"><span data-stu-id="83c93-120">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="83c93-121">Nastavení této hodnoty brání ve smíšeném režimu sestavení z načítání do rozhraní .NET Framework 4 nebo novější, pokud jejich byly vytvořené pomocí rozhraní .NET Framework 4 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="83c93-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="83c93-122">Tato hodnota je výchozí.</span><span class="sxs-lookup"><span data-stu-id="83c93-122">This value is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83c93-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83c93-123">Child Elements</span></span>  
  
|<span data-ttu-id="83c93-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="83c93-124">Element</span></span>|<span data-ttu-id="83c93-125">Popis</span><span class="sxs-lookup"><span data-stu-id="83c93-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="83c93-126">\<requiredRuntime ></span><span class="sxs-lookup"><span data-stu-id="83c93-126">\<requiredRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|<span data-ttu-id="83c93-127">Určuje, jestli aplikace podporuje pouze verzi 1.0 modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="83c93-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="83c93-128">Aplikace vytvořené s nástroji runtime verze 1.1 nebo novější by měly používat  **\<supportedRuntime >** element.</span><span class="sxs-lookup"><span data-stu-id="83c93-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|  
|[<span data-ttu-id="83c93-129">\<supportedRuntime ></span><span class="sxs-lookup"><span data-stu-id="83c93-129">\<supportedRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|<span data-ttu-id="83c93-130">Určuje, kterou verzi modulu Common Language Runtime (CLR) aplikace podporuje.</span><span class="sxs-lookup"><span data-stu-id="83c93-130">Specifies which versions of the common language runtime the application supports.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="83c93-131">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83c93-131">Parent Elements</span></span>  
  
|<span data-ttu-id="83c93-132">Prvek</span><span class="sxs-lookup"><span data-stu-id="83c93-132">Element</span></span>|<span data-ttu-id="83c93-133">Popis</span><span class="sxs-lookup"><span data-stu-id="83c93-133">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="83c93-134">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83c93-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83c93-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83c93-135">Remarks</span></span>  
 <span data-ttu-id="83c93-136">**\<SupportedRuntime >** element má být používána všechny aplikace vytvořené pomocí verze 1.1 nebo novější modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="83c93-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="83c93-137">Musíte použít aplikace založené na podporu pouze verze 1.0 modulu runtime  **\<requiredRuntime >** element.</span><span class="sxs-lookup"><span data-stu-id="83c93-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>  
  
 <span data-ttu-id="83c93-138">Kód spuštění aplikace hostované v aplikaci Internet Explorer ignoruje  **\<spuštění >** elementu a jeho podřízené elementy.</span><span class="sxs-lookup"><span data-stu-id="83c93-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>  
  
## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="83c93-139">Atribut useLegacyV2RuntimeActivationPolicy</span><span class="sxs-lookup"><span data-stu-id="83c93-139">The useLegacyV2RuntimeActivationPolicy Attribute</span></span>  
 <span data-ttu-id="83c93-140">Tento atribut je užitečné, pokud vaše aplikace používá starší verze aktivace cesty, jako [CorBindToRuntimeEx – funkce](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), a chcete tyto cesty k aktivaci 4 verzi modulu CLR místo starší verze, nebo pokud je vaše aplikace vytvořené s nástroji [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] ale obsahuje závislost na ve smíšeném režimu sestavení vytvořené s dřívější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="83c93-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="83c93-141">V těchto scénářích, nastavte atribut na `true`.</span><span class="sxs-lookup"><span data-stu-id="83c93-141">In those scenarios, set the attribute to `true`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83c93-142">Nastavení atributu na `true` CLR verze 1.1 nebo verze modulu CLR 2.0 brání načtení do stejně účinně zakázat funkci vedle sebe v procesu (najdete v části [spuštění vedle sebe zprostředkovatel komunikace s objekty COM](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span><span class="sxs-lookup"><span data-stu-id="83c93-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83c93-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="83c93-143">Example</span></span>  
 <span data-ttu-id="83c93-144">Následující příklad ukazuje, jak určit verzi modulu runtime v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="83c93-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="83c93-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="83c93-145">See Also</span></span>  
 [<span data-ttu-id="83c93-146">Schéma nastavení spouštění</span><span class="sxs-lookup"><span data-stu-id="83c93-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="83c93-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="83c93-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="83c93-148">\<PaveOver > Zadání kterou verzi modulu Runtime pro použití</span><span class="sxs-lookup"><span data-stu-id="83c93-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](http://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)  
 [<span data-ttu-id="83c93-149">Spuštění vedle sebe zprostředkovatel komunikace s objekty COM</span><span class="sxs-lookup"><span data-stu-id="83c93-149">Side-by-Side Execution for COM Interop</span></span>](http://msdn.microsoft.com/library/4302318c-3586-49bf-8620-b9a39cdf4a32)  
 [<span data-ttu-id="83c93-150">Vnitroprocesové souběžné provádění</span><span class="sxs-lookup"><span data-stu-id="83c93-150">In-Process Side-by-Side Execution</span></span>](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)
