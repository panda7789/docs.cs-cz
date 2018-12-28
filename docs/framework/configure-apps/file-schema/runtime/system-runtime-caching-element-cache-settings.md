---
title: '&lt;System.Runtime.Caching –&gt; – Element (nastavení mezipaměti)'
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: daa08bb8a92a13941093a77f580318558dc14e9c
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610369"
---
# <a name="ltsystemruntimecachinggt-element-cache-settings"></a><span data-ttu-id="c6ef1-102">&lt;System.Runtime.Caching –&gt; – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="c6ef1-102">&lt;system.runtime.caching&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="c6ef1-103">Poskytuje konfiguraci pro výchozí v paměťově <xref:System.Runtime.Caching.ObjectCache> implementaci prostřednictvím `memoryCache` záznam v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="c6ef1-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c6ef1-104">\<configuration></span></span>  
<span data-ttu-id="c6ef1-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="c6ef1-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6ef1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6ef1-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6ef1-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6ef1-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c6ef1-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6ef1-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6ef1-109">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="c6ef1-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6ef1-110">Child Elements</span></span>  
  
|<span data-ttu-id="c6ef1-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6ef1-111">Element</span></span>|<span data-ttu-id="c6ef1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c6ef1-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6ef1-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="c6ef1-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="c6ef1-114">Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c6ef1-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6ef1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c6ef1-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6ef1-116">Element</span></span>|<span data-ttu-id="c6ef1-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c6ef1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6ef1-118">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="c6ef1-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c6ef1-119">Určuje kořenový element v každém konfiguračním souboru, který je používán common language runtime a [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-119">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6ef1-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6ef1-120">Remarks</span></span>  
 <span data-ttu-id="c6ef1-121">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti zařízení podobné těm v technologii ASP.NET, ale bez závislosti na `System.Web` sestavení.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="c6ef1-122">Další informace najdete v tématu [ukládání do mezipaměti v aplikacích .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="c6ef1-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6ef1-123">Výstupu do mezipaměti, funkce a typy v <xref:System.Runtime.Caching> jsou nové v oboru názvů [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c6ef1-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6ef1-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6ef1-124">Example</span></span>  
 <span data-ttu-id="c6ef1-125">Následující příklad ukazuje postup při konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="c6ef1-126">Tento příklad ukazuje, jak nakonfigurovat instanci `namedCaches` zadání mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="c6ef1-127">Název mezipaměti, je nastavena na výchozí název položky mezipaměti tak, že nastavíte `name` atribut "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="c6ef1-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="c6ef1-128">`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` je atribut nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="c6ef1-129">Nastavení těchto atributů 0 znamená, <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="c6ef1-130">Implementace mezipaměti by měla porovnání aktuálního zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="c6ef1-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6ef1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6ef1-131">See Also</span></span>  
- [<span data-ttu-id="c6ef1-132">\<memoryCache > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="c6ef1-132">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
