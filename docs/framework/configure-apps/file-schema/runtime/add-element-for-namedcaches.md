---
title: '&lt;Přidat&gt; – Element pro &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 695ee744bdf2226f0647c4cdf142a2dca4e97a4a
ms.sourcegitcommit: daa8788af67ac2d1cecd24f9f3409babb2f978c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2018
ms.locfileid: "47863322"
---
# <a name="ltaddgt-element-for-ltnamedcachesgt"></a><span data-ttu-id="ef457-102">&lt;Přidat&gt; – Element pro &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="ef457-102">&lt;add&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="ef457-103">Přidá `namedCache` položku a `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="ef457-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="ef457-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="ef457-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="ef457-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="ef457-105">\<memoryCache></span></span>  
<span data-ttu-id="ef457-106">\<namedcaches – ></span><span class="sxs-lookup"><span data-stu-id="ef457-106">\<namedCaches></span></span>  
<span data-ttu-id="ef457-107">\<add></span><span class="sxs-lookup"><span data-stu-id="ef457-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef457-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef457-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="ef457-109">Typ</span><span class="sxs-lookup"><span data-stu-id="ef457-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef457-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ef457-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ef457-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ef457-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef457-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="ef457-112">Attributes</span></span>  
  
|<span data-ttu-id="ef457-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="ef457-113">Attribute</span></span>|<span data-ttu-id="ef457-114">Popis</span><span class="sxs-lookup"><span data-stu-id="ef457-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="ef457-115">Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), která instance <xref:System.Runtime.Caching.MemoryCache> růst, aby.</span><span class="sxs-lookup"><span data-stu-id="ef457-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="ef457-116">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ef457-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="ef457-117">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ef457-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="ef457-118">Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalované počítače, které mohou být spotřebovány mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ef457-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="ef457-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="ef457-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="ef457-120">Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="ef457-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="ef457-121">Tato hodnota se zadává ve formátu "hh: mm:".</span><span class="sxs-lookup"><span data-stu-id="ef457-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef457-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ef457-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="ef457-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ef457-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ef457-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ef457-124">Element</span></span>|<span data-ttu-id="ef457-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ef457-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef457-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="ef457-126">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="ef457-127">Obsahuje kolekci prvků konfigurace nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="ef457-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef457-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef457-128">Remarks</span></span>  
 <span data-ttu-id="ef457-129">`add` Element přidá záznam, tím `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="ef457-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="ef457-130">Můžete použít [vymazat](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) prvek před použitím `add` element je potřeba mít jistotu, že neexistují žádné jiné s názvem mezipaměti v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ef457-130">You can use the [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="ef457-131">Tento element lze použít v souboru machine.config a v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="ef457-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef457-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef457-132">Example</span></span>  
 <span data-ttu-id="ef457-133">Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku a `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="ef457-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ef457-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef457-134">See Also</span></span>  
 [<span data-ttu-id="ef457-135">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="ef457-135">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
