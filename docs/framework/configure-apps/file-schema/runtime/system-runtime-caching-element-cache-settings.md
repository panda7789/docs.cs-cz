---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67ead643afd34b4c3422d85e6f7876879de477ba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927233"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="278a4-102">\<System. Runtime. Caching > element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="278a4-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="278a4-103">Poskytuje konfiguraci pro výchozí implementaci v paměti <xref:System.Runtime.Caching.ObjectCache> `memoryCache` prostřednictvím záznamu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="278a4-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="278a4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="278a4-104">\<configuration></span></span>  
<span data-ttu-id="278a4-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="278a4-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278a4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="278a4-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="278a4-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="278a4-107">Attributes and Elements</span></span>

<span data-ttu-id="278a4-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="278a4-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="278a4-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="278a4-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="278a4-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="278a4-110">Child Elements</span></span>

|<span data-ttu-id="278a4-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="278a4-111">Element</span></span>|<span data-ttu-id="278a4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="278a4-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278a4-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="278a4-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="278a4-114">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="278a4-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="278a4-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="278a4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="278a4-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="278a4-116">Element</span></span>|<span data-ttu-id="278a4-117">Popis</span><span class="sxs-lookup"><span data-stu-id="278a4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="278a4-118">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="278a4-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="278a4-119">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="278a4-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="278a4-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="278a4-120">Remarks</span></span>

<span data-ttu-id="278a4-121">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti, jako jsou ty v ASP.NET, ale bez závislosti `System.Web` na sestavení.</span><span class="sxs-lookup"><span data-stu-id="278a4-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="278a4-122">Další informace najdete v tématu [ukládání do mezipaměti v .NET Frameworkch aplikacích](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="278a4-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="278a4-123">Funkce ukládání výstupu do mezipaměti a typy v <xref:System.Runtime.Caching> oboru názvů jsou v .NET Framework 4 nové.</span><span class="sxs-lookup"><span data-stu-id="278a4-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="278a4-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="278a4-124">Example</span></span>

<span data-ttu-id="278a4-125">Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="278a4-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="278a4-126">V tomto příkladu se dozvíte, jak nakonfigurovat instanci `namedCaches` položky pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="278a4-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="278a4-127">Název mezipaměti je nastaven na výchozí název `name` položky mezipaměti nastavením atributu na výchozí.</span><span class="sxs-lookup"><span data-stu-id="278a4-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="278a4-128">`cacheMemoryLimitMegabytes` Atribut`physicalMemoryPercentage` a atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="278a4-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="278a4-129">Nastavení těchto atributů na hodnotu nula znamená, <xref:System.Runtime.Caching.MemoryCache> že výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="278a4-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="278a4-130">Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="278a4-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="278a4-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="278a4-131">See also</span></span>

- [<span data-ttu-id="278a4-132">\<memoryCache – Element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="278a4-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
