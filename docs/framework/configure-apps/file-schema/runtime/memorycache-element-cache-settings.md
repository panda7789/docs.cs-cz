---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 46f430f7cf112da40aa3b25bfb280c5014612eae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663621"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="2c4f9-102">\<memoryCache – Element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="2c4f9-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="2c4f9-103">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="2c4f9-104">Třída definuje element MemoryCache, který můžete použít ke konfiguraci mezipaměti. [](memorycache-element-cache-settings.md) <xref:System.Runtime.Caching.Configuration.MemoryCacheElement></span><span class="sxs-lookup"><span data-stu-id="2c4f9-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="2c4f9-105">V jedné aplikaci lze <xref:System.Runtime.Caching.MemoryCache> použít více instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="2c4f9-106">Každý `memoryCache` prvek v konfiguračním souboru může obsahovat nastavení pro pojmenovanou <xref:System.Runtime.Caching.MemoryCache> instanci.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
 <span data-ttu-id="2c4f9-107">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2c4f9-107">\<configuration></span></span>  
<span data-ttu-id="2c4f9-108">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="2c4f9-108">\<system.runtime.caching></span></span>  
<span data-ttu-id="2c4f9-109">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="2c4f9-109">\<memoryCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c4f9-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c4f9-110">Syntax</span></span>  
  
```xml  
<memoryCache>   
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>   
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="2c4f9-111">type</span><span class="sxs-lookup"><span data-stu-id="2c4f9-111">Type</span></span>  
 <span data-ttu-id="2c4f9-112"><xref:System.Runtime.Caching.MemoryCache>Deník.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c4f9-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c4f9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2c4f9-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c4f9-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c4f9-115">Attributes</span></span>  
  
|<span data-ttu-id="2c4f9-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c4f9-116">Attribute</span></span>|<span data-ttu-id="2c4f9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4f9-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="2c4f9-118">Maximální velikost paměti v megabajtech, kterou může instance <xref:System.Runtime.Caching.MemoryCache> objektu růst.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="2c4f9-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="2c4f9-120">Název konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="2c4f9-121">Procento fyzické paměti, které může mezipaměť použít.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="2c4f9-122">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="2c4f9-123">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="2c4f9-124">Hodnota je zadána ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="2c4f9-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c4f9-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c4f9-125">Child Elements</span></span>  
  
|<span data-ttu-id="2c4f9-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c4f9-126">Element</span></span>|<span data-ttu-id="2c4f9-127">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4f9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c4f9-128">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="2c4f9-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="2c4f9-129">Obsahuje kolekci konfiguračních nastavení `namedCache` instance.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2c4f9-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c4f9-130">Parent Elements</span></span>  
  
|<span data-ttu-id="2c4f9-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c4f9-131">Element</span></span>|<span data-ttu-id="2c4f9-132">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4f9-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c4f9-133">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="2c4f9-133">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="2c4f9-134">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-134">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c4f9-135">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c4f9-135">Remarks</span></span>  
 <span data-ttu-id="2c4f9-136">Třída je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy. <xref:System.Runtime.Caching.MemoryCache></span><span class="sxs-lookup"><span data-stu-id="2c4f9-136">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="2c4f9-137"><xref:System.Runtime.Caching.MemoryCache> Instance třídy mohou být dodány s informacemi o konfiguraci z konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-137">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="2c4f9-138">Konfigurační oddíl [MemoryCache](memorycache-element-cache-settings.md) obsahuje `namedCaches` kolekci konfigurací.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-138">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="2c4f9-139">Při inicializaci objektu mezipaměti založeného na paměti se nejprve pokusí najít `namedCaches` položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-139">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="2c4f9-140">Pokud je `namedCaches` položka nalezena, informace o pro dotazování a správu paměti se načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-140">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="2c4f9-141">Proces inicializace pak určí, zda byly všechny položky konfigurace přepsány, pomocí volitelné kolekce párů název/hodnota v informacích o konfiguraci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-141">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="2c4f9-142">Pokud předáte jednu z následujících hodnot v kolekci dvojice název/hodnota, přepíší tyto hodnoty informace získané z konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="2c4f9-142">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="2c4f9-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c4f9-143">Example</span></span>  
 <span data-ttu-id="2c4f9-144">Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objektu na výchozí název objektu mezipaměti `name` nastavením atributu na hodnotu "default".</span><span class="sxs-lookup"><span data-stu-id="2c4f9-144">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="2c4f9-145">`cacheMemoryLimitMegabytes` Atribut`physicalMemoryLimitPercentage` a atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-145">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="2c4f9-146">Nastavení těchto atributů na hodnotu nula znamená, <xref:System.Runtime.Caching.MemoryCache> že výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-146">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="2c4f9-147">Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="2c4f9-147">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2c4f9-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c4f9-148">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="2c4f9-149">\<System. Runtime. Caching > element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="2c4f9-149">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="2c4f9-150">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="2c4f9-150">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
