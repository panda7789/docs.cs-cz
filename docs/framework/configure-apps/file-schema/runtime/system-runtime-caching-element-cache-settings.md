---
title: "&lt;System.Runtime.Caching –&gt; – Element (nastavení mezipaměti)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 83964d3a6e07267eaa946fa306301bc6d0d16e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="a0e16-102">&lt;System.Runtime.Caching –&gt; – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="a0e16-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="a0e16-103">Poskytuje konfigurace pro výchozí v paměťově <xref:System.Runtime.Caching.ObjectCache> implementace prostřednictvím `memoryCache` položka v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a0e16-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="a0e16-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a0e16-104">\<configuration></span></span>  
<span data-ttu-id="a0e16-105">\<System.Runtime.Caching – ></span><span class="sxs-lookup"><span data-stu-id="a0e16-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e16-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e16-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0e16-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a0e16-107">Attributes and Elements</span></span>  
 <span data-ttu-id="a0e16-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a0e16-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0e16-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="a0e16-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="a0e16-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a0e16-110">Child Elements</span></span>  
  
|<span data-ttu-id="a0e16-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0e16-111">Element</span></span>|<span data-ttu-id="a0e16-112">Popis</span><span class="sxs-lookup"><span data-stu-id="a0e16-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0e16-113">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="a0e16-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="a0e16-114">Definuje element, který slouží ke konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0e16-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0e16-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a0e16-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a0e16-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="a0e16-116">Element</span></span>|<span data-ttu-id="a0e16-117">Popis</span><span class="sxs-lookup"><span data-stu-id="a0e16-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0e16-118">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a0e16-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="a0e16-119">Určuje kořenový element v každém konfiguračním souboru, který je používán modul common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0e16-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0e16-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0e16-120">Remarks</span></span>  
 <span data-ttu-id="a0e16-121">Třídy v tomto oboru názvů poskytují způsob, jak použít zařízení pro ukládání do mezipaměti jako ty, technologie ASP.NET, ale bez závislosti na `System.Web` sestavení.</span><span class="sxs-lookup"><span data-stu-id="a0e16-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="a0e16-122">Další informace najdete v tématu [ukládání do mezipaměti v aplikacích .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="a0e16-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0e16-123">Výstupní mezipaměti typy v a funkce <xref:System.Runtime.Caching> obor názvů jsou v nové [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0e16-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0e16-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0e16-124">Example</span></span>  
 <span data-ttu-id="a0e16-125">Následující příklad ukazuje, jak nakonfigurovat mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="a0e16-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="a0e16-126">Tento příklad ukazuje, jak nakonfigurovat instanci `namedCaches` položka pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="a0e16-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="a0e16-127">Název mezipaměti se nastaví na výchozí název položky mezipaměti nastavením `name` atribut "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="a0e16-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="a0e16-128">`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` atribut nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="a0e16-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="a0e16-129">Nastavení těchto atributů na nulu, znamená to, který <xref:System.Runtime.Caching.MemoryCache> Automatická změna velikosti heuristiky se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="a0e16-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="a0e16-130">Implementace mezipaměti musí porovnat aktuálního zatížení paměti do paměti absolutní a na základě procenta omezení každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="a0e16-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0e16-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0e16-131">See Also</span></span>  
 [<span data-ttu-id="a0e16-132">\<memoryCache > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="a0e16-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
