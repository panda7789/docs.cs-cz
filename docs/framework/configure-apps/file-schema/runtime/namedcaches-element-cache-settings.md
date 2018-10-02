---
title: '&lt;Element namedCaches&gt; – Element (nastavení mezipaměti)'
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a74dfaf883ea23514c6bc4641d9d576f5baf10b4
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028296"
---
# <a name="ltnamedcachesgt-element-cache-settings"></a><span data-ttu-id="df8cf-102">&lt;Element namedCaches&gt; – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="df8cf-102">&lt;namedCaches&gt; Element (Cache Settings)</span></span>
<span data-ttu-id="df8cf-103">Určuje kolekci nastavení konfigurace pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instancí.</span><span class="sxs-lookup"><span data-stu-id="df8cf-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="df8cf-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> Vlastnost odkazuje na soubor konfiguračních nastavení z jedné nebo více `namedCaches` prvky konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="df8cf-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
 <span data-ttu-id="df8cf-105">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="df8cf-105">\<configuration></span></span>  
<span data-ttu-id="df8cf-106">\< System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="df8cf-106">\< system.runtime.caching></span></span>  
<span data-ttu-id="df8cf-107">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="df8cf-107">\<memoryCache></span></span>  
<span data-ttu-id="df8cf-108">\<namedcaches – ></span><span class="sxs-lookup"><span data-stu-id="df8cf-108">\<namedCaches></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8cf-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df8cf-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="df8cf-110">Typ</span><span class="sxs-lookup"><span data-stu-id="df8cf-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df8cf-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="df8cf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="df8cf-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="df8cf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df8cf-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="df8cf-113">Attributes</span></span>  
  
|<span data-ttu-id="df8cf-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="df8cf-114">Attribute</span></span>|<span data-ttu-id="df8cf-115">Popis</span><span class="sxs-lookup"><span data-stu-id="df8cf-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="df8cf-116">Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, který instance <xref:System.Runtime.Caching.MemoryCache> růst, aby.</span><span class="sxs-lookup"><span data-stu-id="df8cf-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="df8cf-117">Výchozí hodnota je 0, což znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="df8cf-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="df8cf-118">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="df8cf-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="df8cf-119">Celočíselná hodnota mezi 0 a 100 určující maximální procento paměti fyzicky nainstalované počítače, které mohou být spotřebovány mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="df8cf-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="df8cf-120">Výchozí hodnota je 0, což znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="df8cf-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="df8cf-121">Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="df8cf-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="df8cf-122">Tato hodnota se zadává ve formátu "hh: mm:".</span><span class="sxs-lookup"><span data-stu-id="df8cf-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df8cf-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="df8cf-123">Child Elements</span></span>  
  
|<span data-ttu-id="df8cf-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="df8cf-124">Element</span></span>|<span data-ttu-id="df8cf-125">Popis</span><span class="sxs-lookup"><span data-stu-id="df8cf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df8cf-126">\<add></span><span class="sxs-lookup"><span data-stu-id="df8cf-126">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|<span data-ttu-id="df8cf-127">Přidá pojmenované mezipaměti, aby `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="df8cf-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="df8cf-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="df8cf-128">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|<span data-ttu-id="df8cf-129">Vymaže `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="df8cf-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="df8cf-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="df8cf-130">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|<span data-ttu-id="df8cf-131">Odebere položku pojmenovanou mezipaměť z `namedCaches` kolekce pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="df8cf-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df8cf-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="df8cf-132">Parent Elements</span></span>  
  
|<span data-ttu-id="df8cf-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="df8cf-133">Element</span></span>|<span data-ttu-id="df8cf-134">Popis</span><span class="sxs-lookup"><span data-stu-id="df8cf-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="df8cf-135">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="df8cf-135">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="df8cf-136">Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="df8cf-136">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df8cf-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df8cf-137">Remarks</span></span>  
 <span data-ttu-id="df8cf-138">Konfigurační oddíl mezipaměti paměti souboru Web.config mohou obsahovat `add`, `remove`, a `clear` atributů pro `namedCaches` kolekce.</span><span class="sxs-lookup"><span data-stu-id="df8cf-138">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="df8cf-139">Každý `namedCaches` položka je jedinečně identifikovaný `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="df8cf-139">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="df8cf-140">Instance položky mezipaměti paměti můžete načíst pomocí odkazu na informace v konfiguračních souborech aplikace.</span><span class="sxs-lookup"><span data-stu-id="df8cf-140">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="df8cf-141">Ve výchozím nastavení pouze výchozí instanci mezipaměti má záznam v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="df8cf-141">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="df8cf-142">Výchozí instance mezipaměti je instanci, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df8cf-142">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="df8cf-143">Pokud nastavíte atribut name "Výchozí", element používá výchozí instanci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="df8cf-143">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="df8cf-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="df8cf-144">Example</span></span>  
 <span data-ttu-id="df8cf-145">Následující příklad ukazuje, jak nastavit název mezipaměti, výchozí název položky mezipaměti tak, že nastavíte `name` atribut "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="df8cf-145">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="df8cf-146">`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` je atribut nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="df8cf-146">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="df8cf-147">Nastavení těchto atributů na hodnotu nula znamená, že automatické přizpůsobení velikosti heuristiky z <xref:System.Runtime.Caching.MemoryCache> třída se používá.</span><span class="sxs-lookup"><span data-stu-id="df8cf-147">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="df8cf-148">Implementace mezipaměti porovná aktuální zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="df8cf-148">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="df8cf-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="df8cf-149">See Also</span></span>  
 [<span data-ttu-id="df8cf-150">\<memoryCache > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="df8cf-150">\<memoryCache> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)
