---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 9ed3c290c3d4836eb783348b559cab46a38b2063
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592677"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="f1772-102">\<memoryCache > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="f1772-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="f1772-103">Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1772-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="f1772-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement> Definuje třídu [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element, který můžete použít ke konfiguraci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f1772-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="f1772-105">Více instancí <xref:System.Runtime.Caching.MemoryCache> třídy lze v jedné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f1772-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="f1772-106">Každý `memoryCache` element v konfiguračním souboru může obsahovat nastavení pro pojmenovaná <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="f1772-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="f1772-107">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="f1772-107">\<configuration></span></span>  
<span data-ttu-id="f1772-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="f1772-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="f1772-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="f1772-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1772-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f1772-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="f1772-111">Type</span><span class="sxs-lookup"><span data-stu-id="f1772-111">Type</span></span>  
 <span data-ttu-id="f1772-112"><xref:System.Runtime.Caching.MemoryCache> Třída.</span><span class="sxs-lookup"><span data-stu-id="f1772-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1772-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f1772-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f1772-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f1772-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1772-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="f1772-115">Attributes</span></span>  
  
|<span data-ttu-id="f1772-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="f1772-116">Attribute</span></span>|<span data-ttu-id="f1772-117">Popis</span><span class="sxs-lookup"><span data-stu-id="f1772-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="f1772-118">Do maximální velikosti paměti, v megabajtech, který instance <xref:System.Runtime.Caching.MemoryCache> objekt růst, aby.</span><span class="sxs-lookup"><span data-stu-id="f1772-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="f1772-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristické metody automaticky přizpůsobit velikost třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1772-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="f1772-120">Název konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f1772-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="f1772-121">Procento fyzické paměti, je možné do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f1772-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="f1772-122">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> heuristické metody automaticky přizpůsobit velikost třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1772-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="f1772-123">Hodnota, která určuje časový interval, po jejímž uplynutí implementaci mezipaměti porovná aktuální zatížení paměti do paměti absolutní a založený na procentech omezení, které jsou nastavené pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="f1772-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="f1772-124">Hodnota je zadáno ve formátu "hh: mm:".</span><span class="sxs-lookup"><span data-stu-id="f1772-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1772-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f1772-125">Child Elements</span></span>  
  
|<span data-ttu-id="f1772-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1772-126">Element</span></span>|<span data-ttu-id="f1772-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f1772-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1772-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="f1772-128">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="f1772-129">Obsahuje kolekci prvků konfigurace nastavení `namedCache` instance.</span><span class="sxs-lookup"><span data-stu-id="f1772-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1772-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f1772-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f1772-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="f1772-131">Element</span></span>|<span data-ttu-id="f1772-132">Popis</span><span class="sxs-lookup"><span data-stu-id="f1772-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1772-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="f1772-133">\<system.runtime.caching></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="f1772-134">Obsahuje typy, které umožňují v aplikacích, které jsou součástí implementace ukládání výstupu do mezipaměti [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1772-134">Contains types that let you implement output caching in applications that are built into the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1772-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1772-135">Remarks</span></span>  
 <span data-ttu-id="f1772-136"><xref:System.Runtime.Caching.MemoryCache> Je konkrétní implementaci abstraktní třída <xref:System.Runtime.Caching.ObjectCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="f1772-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="f1772-137">Instance <xref:System.Runtime.Caching.MemoryCache> třídy může být zadán s informace o konfiguraci z konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1772-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="f1772-138">[MemoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) oddíl konfigurace obsahuje `namedCaches` kolekce konfigurací.</span><span class="sxs-lookup"><span data-stu-id="f1772-138">The [memoryCache](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="f1772-139">Při inicializaci mezipaměti na základě paměti objektu, nejprve se pokusí najít `namedCaches` položku, která odpovídá názvu parametru, který je předán konstruktoru mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="f1772-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="f1772-140">Pokud `namedCaches` položka nenajde, dotazování a správu paměti informace se načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="f1772-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="f1772-141">Proces inicializace pak určuje, zda byly přepsat všechny položky konfigurace, pomocí volitelné kolekci dvojic název/hodnota informací o konfiguraci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f1772-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="f1772-142">Pokud předáte některou z následujících hodnot v kolekci dvojice název/hodnota, tyto hodnoty přepsání informacemi získanými z konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="f1772-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="f1772-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="f1772-143">Example</span></span>  
 <span data-ttu-id="f1772-144">Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objekt má výchozí název objektu mezipaměti tak, že nastavíte `name` atribut "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="f1772-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="f1772-145">`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryLimitPercentage` je atribut nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="f1772-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="f1772-146">Nastavení těchto atributů 0 znamená, <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1772-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="f1772-147">Implementace mezipaměti by měla porovnání aktuálního zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="f1772-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1772-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1772-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="f1772-149">\<System.Runtime.Caching > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="f1772-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="f1772-150">\<namedcaches – > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="f1772-150">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
