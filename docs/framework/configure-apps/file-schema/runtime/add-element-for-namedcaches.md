---
title: <add> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: fd6668a551663470a97b07ff131710dbe92a91f5
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659029"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="3255c-102">\<Přidat > element pro \<> namedCaches</span><span class="sxs-lookup"><span data-stu-id="3255c-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="3255c-103">`namedCache` Přidá položku`namedCaches` do kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="3255c-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="3255c-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="3255c-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="3255c-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="3255c-105">\<memoryCache></span></span>  
<span data-ttu-id="3255c-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="3255c-106">\<namedCaches></span></span>  
<span data-ttu-id="3255c-107">\<add></span><span class="sxs-lookup"><span data-stu-id="3255c-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3255c-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3255c-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="3255c-109">type</span><span class="sxs-lookup"><span data-stu-id="3255c-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3255c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3255c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3255c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3255c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3255c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="3255c-112">Attributes</span></span>  
  
|<span data-ttu-id="3255c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="3255c-113">Attribute</span></span>|<span data-ttu-id="3255c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="3255c-114">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="3255c-115">Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), kterou může <xref:System.Runtime.Caching.MemoryCache> instance a růst.</span><span class="sxs-lookup"><span data-stu-id="3255c-115">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="3255c-116">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="3255c-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="3255c-117">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3255c-117">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="3255c-118">Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="3255c-118">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="3255c-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="3255c-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="3255c-120">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3255c-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="3255c-121">Tato hodnota je zadaná ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="3255c-121">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3255c-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3255c-122">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="3255c-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3255c-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3255c-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3255c-124">Element</span></span>|<span data-ttu-id="3255c-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3255c-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3255c-126">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="3255c-126">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="3255c-127">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="3255c-127">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3255c-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3255c-128">Remarks</span></span>  
 <span data-ttu-id="3255c-129">Element přidá položku `namedCaches` do kolekce mezipaměti paměti. `add`</span><span class="sxs-lookup"><span data-stu-id="3255c-129">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="3255c-130">Element [clear](clear-element-for-namedcaches.md) lze použít před použitím `add` elementu, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3255c-130">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="3255c-131">Tento element lze použít v souboru Machine. config a v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="3255c-131">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3255c-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="3255c-132">Example</span></span>  
 <span data-ttu-id="3255c-133">Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku `namedCaches` do kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="3255c-133">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3255c-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3255c-134">See also</span></span>

- [<span data-ttu-id="3255c-135">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="3255c-135">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
