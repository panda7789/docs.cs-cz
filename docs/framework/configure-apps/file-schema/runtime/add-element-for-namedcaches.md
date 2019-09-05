---
title: <add> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: 076d940e0c15cf48013480fef68b8fac42cf76e9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252889"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="91888-102">\<Přidat > element pro \<> namedCaches</span><span class="sxs-lookup"><span data-stu-id="91888-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="91888-103">`namedCache` Přidá položku`namedCaches` do kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="91888-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="91888-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="91888-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="91888-105">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="91888-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="91888-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="91888-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="91888-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedCaches >** ](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="91888-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="91888-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="91888-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91888-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91888-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="91888-110">type</span><span class="sxs-lookup"><span data-stu-id="91888-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91888-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="91888-111">Attributes and Elements</span></span>  
 <span data-ttu-id="91888-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="91888-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91888-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="91888-113">Attributes</span></span>  
  
|<span data-ttu-id="91888-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="91888-114">Attribute</span></span>|<span data-ttu-id="91888-115">Popis</span><span class="sxs-lookup"><span data-stu-id="91888-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="91888-116">Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), kterou může <xref:System.Runtime.Caching.MemoryCache> instance a růst.</span><span class="sxs-lookup"><span data-stu-id="91888-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="91888-117">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="91888-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="91888-118">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="91888-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="91888-119">Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="91888-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="91888-120">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="91888-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="91888-121">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="91888-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="91888-122">Tato hodnota je zadaná ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="91888-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91888-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="91888-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="91888-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="91888-124">Parent Elements</span></span>  
  
|<span data-ttu-id="91888-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="91888-125">Element</span></span>|<span data-ttu-id="91888-126">Popis</span><span class="sxs-lookup"><span data-stu-id="91888-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91888-127">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="91888-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="91888-128">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="91888-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91888-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91888-129">Remarks</span></span>  
 <span data-ttu-id="91888-130">Element přidá položku `namedCaches` do kolekce mezipaměti paměti. `add`</span><span class="sxs-lookup"><span data-stu-id="91888-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="91888-131">Element [clear](clear-element-for-namedcaches.md) lze použít před použitím `add` elementu, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="91888-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="91888-132">Tento element lze použít v souboru Machine. config a v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="91888-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91888-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="91888-133">Example</span></span>  
 <span data-ttu-id="91888-134">Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku `namedCaches` do kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="91888-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
```xml  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="91888-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91888-135">See also</span></span>

- [<span data-ttu-id="91888-136">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="91888-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
