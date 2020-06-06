---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153981"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="6faa6-102">\<memoryCache> – element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="6faa6-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="6faa6-103">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="6faa6-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="6faa6-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheElement>Třída definuje element [MemoryCache](memorycache-element-cache-settings.md) , který můžete použít ke konfiguraci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6faa6-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="6faa6-105"><xref:System.Runtime.Caching.MemoryCache>V jedné aplikaci lze použít více instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="6faa6-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="6faa6-106">Každý `memoryCache` prvek v konfiguračním souboru může obsahovat nastavení pro pojmenovanou <xref:System.Runtime.Caching.MemoryCache> instanci.</span><span class="sxs-lookup"><span data-stu-id="6faa6-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**  
  
## <a name="syntax"></a><span data-ttu-id="6faa6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6faa6-107">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="6faa6-108">Typ</span><span class="sxs-lookup"><span data-stu-id="6faa6-108">Type</span></span>  
 <span data-ttu-id="6faa6-109"><xref:System.Runtime.Caching.MemoryCache>Deník.</span><span class="sxs-lookup"><span data-stu-id="6faa6-109"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6faa6-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6faa6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6faa6-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6faa6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6faa6-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6faa6-112">Attributes</span></span>  
  
|<span data-ttu-id="6faa6-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6faa6-113">Attribute</span></span>|<span data-ttu-id="6faa6-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6faa6-114">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="6faa6-115">Maximální velikost paměti v megabajtech, kterou <xref:System.Runtime.Caching.MemoryCache> může instance objektu růst.</span><span class="sxs-lookup"><span data-stu-id="6faa6-115">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="6faa6-116">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.</span><span class="sxs-lookup"><span data-stu-id="6faa6-116">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="6faa6-117">Název konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6faa6-117">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="6faa6-118">Procento fyzické paměti, které může mezipaměť použít.</span><span class="sxs-lookup"><span data-stu-id="6faa6-118">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="6faa6-119">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou použity heuristické hodnoty třídy AutoSize.</span><span class="sxs-lookup"><span data-stu-id="6faa6-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="6faa6-120">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6faa6-120">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="6faa6-121">Hodnota je zadána ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="6faa6-121">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6faa6-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6faa6-122">Child Elements</span></span>  
  
|<span data-ttu-id="6faa6-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="6faa6-123">Element</span></span>|<span data-ttu-id="6faa6-124">Description</span><span class="sxs-lookup"><span data-stu-id="6faa6-124">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="6faa6-125">Obsahuje kolekci konfiguračních nastavení `namedCache` instance.</span><span class="sxs-lookup"><span data-stu-id="6faa6-125">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6faa6-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6faa6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="6faa6-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="6faa6-127">Element</span></span>|<span data-ttu-id="6faa6-128">Description</span><span class="sxs-lookup"><span data-stu-id="6faa6-128">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="6faa6-129">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="6faa6-129">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="6faa6-130">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6faa6-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6faa6-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6faa6-131">Remarks</span></span>  
 <span data-ttu-id="6faa6-132"><xref:System.Runtime.Caching.MemoryCache>Třída je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="6faa6-132">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="6faa6-133">Instance <xref:System.Runtime.Caching.MemoryCache> třídy mohou být dodány s informacemi o konfiguraci z konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="6faa6-133">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="6faa6-134">Konfigurační oddíl [MemoryCache](memorycache-element-cache-settings.md) obsahuje `namedCaches` kolekci konfigurací.</span><span class="sxs-lookup"><span data-stu-id="6faa6-134">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="6faa6-135">Při inicializaci objektu mezipaměti založeného na paměti se nejprve pokusí najít `namedCaches` položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="6faa6-135">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="6faa6-136">Pokud `namedCaches` je položka nalezena, informace o pro dotazování a správu paměti se načítají z konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="6faa6-136">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="6faa6-137">Proces inicializace pak určí, zda byly všechny položky konfigurace přepsány, pomocí volitelné kolekce párů název/hodnota v informacích o konfiguraci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6faa6-137">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="6faa6-138">Pokud předáte jednu z následujících hodnot v kolekci dvojice název/hodnota, přepíší tyto hodnoty informace získané z konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="6faa6-138">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="6faa6-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="6faa6-139">Example</span></span>  
 <span data-ttu-id="6faa6-140">Následující příklad ukazuje, jak nastavit název <xref:System.Runtime.Caching.MemoryCache> objektu na výchozí název objektu mezipaměti nastavením `name` atributu na hodnotu "default".</span><span class="sxs-lookup"><span data-stu-id="6faa6-140">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="6faa6-141">`cacheMemoryLimitMegabytes`Atribut a `physicalMemoryLimitPercentage` atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="6faa6-141">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="6faa6-142">Nastavení těchto atributů na hodnotu nula znamená, že <xref:System.Runtime.Caching.MemoryCache> výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="6faa6-142">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="6faa6-143">Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="6faa6-143">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6faa6-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="6faa6-144">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="6faa6-145">\<system.runtime.caching>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="6faa6-145">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="6faa6-146">\<namedCaches>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="6faa6-146">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
