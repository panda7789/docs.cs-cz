---
title: '&lt;Přidat&gt; Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d65dfd9a1560f2657f48b327277b64ab77014b47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743820"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="d3f98-102">&lt;Přidat&gt; Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="d3f98-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="d3f98-103">Přidá `namedCache` položku s `namedCaches` kolekci pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="d3f98-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="d3f98-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="d3f98-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="d3f98-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="d3f98-105">\<memoryCache></span></span>  
<span data-ttu-id="d3f98-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="d3f98-106">\<namedCaches></span></span>  
<span data-ttu-id="d3f98-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d3f98-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3f98-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3f98-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="d3f98-109">Typ</span><span class="sxs-lookup"><span data-stu-id="d3f98-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3f98-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3f98-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d3f98-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3f98-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3f98-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3f98-112">Attributes</span></span>  
  
|<span data-ttu-id="d3f98-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3f98-113">Attribute</span></span>|<span data-ttu-id="d3f98-114">Popis</span><span class="sxs-lookup"><span data-stu-id="d3f98-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="d3f98-115">Celočíselná hodnota, která určuje maximální povolená velikost (v megabajtech), instanci <xref:System.Runtime.Caching.MemoryCache> můžete dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="d3f98-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="d3f98-116">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky Automatická změna velikosti třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d3f98-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="d3f98-117">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d3f98-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="d3f98-118">Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalovaném počítači, která mohou být spotřebovávána mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d3f98-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="d3f98-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky Automatická změna velikosti třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="d3f98-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="d3f98-120">Hodnota, která určuje časový interval, po jejímž uplynutí implementace mezipaměti porovná aktuální zatížení paměti do paměti absolutní a na základě procenta omezení, které jsou nastavené pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d3f98-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="d3f98-121">Tato hodnota je uvedeno ve formátu hh: mm".</span><span class="sxs-lookup"><span data-stu-id="d3f98-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3f98-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3f98-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="d3f98-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3f98-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d3f98-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3f98-124">Element</span></span>|<span data-ttu-id="d3f98-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d3f98-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3f98-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="d3f98-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="d3f98-127">Obsahuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="d3f98-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3f98-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3f98-128">Remarks</span></span>  
 <span data-ttu-id="d3f98-129">`add` Element přidá položku do `namedCaches` kolekci pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="d3f98-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="d3f98-130">Můžete použít [vymazat](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element před použitím `add` elementu, který chcete být jisti, že neexistují žádné další s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d3f98-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="d3f98-131">Tento element lze použít v souboru machine.config a v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="d3f98-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3f98-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3f98-132">Example</span></span>  
 <span data-ttu-id="d3f98-133">Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku na `namedCaches` kolekci pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="d3f98-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3f98-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3f98-134">See Also</span></span>  
 [<span data-ttu-id="d3f98-135">\<namedCaches > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="d3f98-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
