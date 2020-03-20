---
title: <memoryCache> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <memoryCache> element
- caching [.NET Framework], configuration
- memoryCache element
ms.assetid: 182a622f-f7cf-472d-9d0b-451d2fd94525
ms.openlocfilehash: 94c21e0408b7616bf0c8a24267b72bfa7cc3aaa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153981"
---
# <a name="memorycache-element-cache-settings"></a><span data-ttu-id="8d976-102">\<memoryCache> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="8d976-102">\<memoryCache> Element (Cache Settings)</span></span>
<span data-ttu-id="8d976-103">Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě.</span><span class="sxs-lookup"><span data-stu-id="8d976-103">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="8d976-104">Třída <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> definuje element [memoryCache,](memorycache-element-cache-settings.md) který můžete použít ke konfiguraci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheElement> class defines a [memoryCache](memorycache-element-cache-settings.md) element that you can use to configure the cache.</span></span> <span data-ttu-id="8d976-105">Více instancí <xref:System.Runtime.Caching.MemoryCache> třídy lze použít v jedné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d976-105">Multiple instances of the <xref:System.Runtime.Caching.MemoryCache> class can be used in a single application.</span></span> <span data-ttu-id="8d976-106">Každý `memoryCache` prvek v konfiguračním <xref:System.Runtime.Caching.MemoryCache> souboru může obsahovat nastavení pojmenované instance.</span><span class="sxs-lookup"><span data-stu-id="8d976-106">Each `memoryCache` element in the configuration file can contain settings for a named <xref:System.Runtime.Caching.MemoryCache> instance.</span></span>  
  
<span data-ttu-id="8d976-107">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d976-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d976-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d976-108">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="8d976-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span><span class="sxs-lookup"><span data-stu-id="8d976-109">&nbsp;&nbsp;&nbsp;&nbsp;**\<memoryCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d976-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d976-110">Syntax</span></span>  
  
```xml  
<memoryCache>
    <namedCaches>  
        <!-- child elements -->  
    </namedCaches>
</memoryCache>  
```  
  
## <a name="type"></a><span data-ttu-id="8d976-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8d976-111">Type</span></span>  
 <span data-ttu-id="8d976-112"><xref:System.Runtime.Caching.MemoryCache>Třída.</span><span class="sxs-lookup"><span data-stu-id="8d976-112"><xref:System.Runtime.Caching.MemoryCache> class.</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d976-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d976-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8d976-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d976-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d976-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d976-115">Attributes</span></span>  
  
|<span data-ttu-id="8d976-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="8d976-116">Attribute</span></span>|<span data-ttu-id="8d976-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8d976-117">Description</span></span>|  
|---------------|-----------------|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="8d976-118">Maximální velikost paměti v megabajtech, do které <xref:System.Runtime.Caching.MemoryCache> může být instance objektu narůstat.</span><span class="sxs-lookup"><span data-stu-id="8d976-118">The maximum memory size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> object can grow to.</span></span> <span data-ttu-id="8d976-119">Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají heuristiky automatické velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="8d976-119">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="8d976-120">Název konfigurace mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-120">The name of the cache configuration.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="8d976-121">Procento fyzické paměti, které lze použít v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-121">The percentage of physical memory that can be used by the cache.</span></span> <span data-ttu-id="8d976-122">Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají heuristiky automatické velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="8d976-122">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosize heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="8d976-123">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-123">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="8d976-124">Hodnota je zadána ve formátu HH:MM:SS.</span><span class="sxs-lookup"><span data-stu-id="8d976-124">The value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d976-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d976-125">Child Elements</span></span>  
  
|<span data-ttu-id="8d976-126">Element</span><span class="sxs-lookup"><span data-stu-id="8d976-126">Element</span></span>|<span data-ttu-id="8d976-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8d976-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d976-128">\<pojmenováno Caches></span><span class="sxs-lookup"><span data-stu-id="8d976-128">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="8d976-129">Obsahuje kolekci nastavení konfigurace `namedCache` pro instanci.</span><span class="sxs-lookup"><span data-stu-id="8d976-129">Contains a collection of configuration settings for the `namedCache` instance.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d976-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d976-130">Parent Elements</span></span>  
  
|<span data-ttu-id="8d976-131">Element</span><span class="sxs-lookup"><span data-stu-id="8d976-131">Element</span></span>|<span data-ttu-id="8d976-132">Popis</span><span class="sxs-lookup"><span data-stu-id="8d976-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d976-133">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="8d976-133">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="8d976-134">Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d976-134">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="8d976-135">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="8d976-135">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="8d976-136">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8d976-136">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d976-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d976-137">Remarks</span></span>  
 <span data-ttu-id="8d976-138">Třída <xref:System.Runtime.Caching.MemoryCache> je konkrétní implementace abstraktní <xref:System.Runtime.Caching.ObjectCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="8d976-138">The <xref:System.Runtime.Caching.MemoryCache> class is a concrete implementation of the abstract <xref:System.Runtime.Caching.ObjectCache> class.</span></span> <span data-ttu-id="8d976-139">Instance <xref:System.Runtime.Caching.MemoryCache> třídy mohou být dodávány s informacemi o konfiguraci z konfiguračních souborů aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d976-139">Instances of the <xref:System.Runtime.Caching.MemoryCache> class can be supplied with configuration information from application configuration files.</span></span> <span data-ttu-id="8d976-140">Oddíl konfigurace [memoryCache](memorycache-element-cache-settings.md) `namedCaches` obsahuje kolekci konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8d976-140">The [memoryCache](memorycache-element-cache-settings.md) configuration section contains a `namedCaches` configuration collection.</span></span>  
  
 <span data-ttu-id="8d976-141">Při inicializování objektu mezipaměti založeného `namedCaches` na paměti se nejprve pokusí najít položku, která odpovídá názvu v parametru, který je předán konstruktoru mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-141">When a memory-based cache object is initialized, it first tries to find a `namedCaches` entry that matches the name in the parameter that is passed to the memory cache constructor.</span></span> <span data-ttu-id="8d976-142">Pokud `namedCaches` je nalezena položka, jsou z konfiguračního souboru načteny informace o dotazování a správě paměti.</span><span class="sxs-lookup"><span data-stu-id="8d976-142">If a `namedCaches` entry is found, the polling and memory-management information are retrieved from the configuration file.</span></span>  
  
 <span data-ttu-id="8d976-143">Proces inicializace pak určuje, zda byly všechny položky konfigurace přepsány pomocí volitelné kolekce dvojic názvů a hodnot informací o konfiguraci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8d976-143">The initialization process then determines whether any configuration entries were overridden, by using the optional collection of name/value pairs of configuration information in the constructor.</span></span> <span data-ttu-id="8d976-144">Pokud v kolekci dvojice název/hodnota předáte některou z následujících hodnot, tyto hodnoty přepíší informace získané z konfiguračního souboru:</span><span class="sxs-lookup"><span data-stu-id="8d976-144">If you pass any one of the following values in the name/value pair collection, these values override information obtained from the configuration file:</span></span>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.CacheMemoryLimitMegabytes%2A>  
  
- <xref:System.Runtime.Caching.Configuration.MemoryCacheElement.PhysicalMemoryLimitPercentage%2A>  
  
- <xref:System.Runtime.Caching.MemoryCache.PollingInterval%2A>  
  
## <a name="example"></a><span data-ttu-id="8d976-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d976-145">Example</span></span>  
 <span data-ttu-id="8d976-146">Následující příklad ukazuje, jak nastavit <xref:System.Runtime.Caching.MemoryCache> název objektu na výchozí název `name` objektu mezipaměti nastavením atributu "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="8d976-146">The following example shows how to set the name of the <xref:System.Runtime.Caching.MemoryCache> object to the default cache object name by setting the `name` attribute to "Default".</span></span>  
  
 <span data-ttu-id="8d976-147">Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryLimitPercentage` atribut jsou nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="8d976-147">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryLimitPercentage` attribute are set to zero.</span></span> <span data-ttu-id="8d976-148">Nastavení těchto atributů na <xref:System.Runtime.Caching.MemoryCache> nulu znamená, že autosizing heuristiky jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8d976-148">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="8d976-149">Implementace mezipaměti by měla porovnávat aktuální zatížení paměti s absolutními a procentuálními limity paměti každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="8d976-149">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d976-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d976-150">See also</span></span>

- <xref:System.Runtime.Caching.MemoryCache>
- [<span data-ttu-id="8d976-151">\<system.runtime.caching> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="8d976-151">\<system.runtime.caching> Element (Cache Settings)</span></span>](system-runtime-caching-element-cache-settings.md)
- [<span data-ttu-id="8d976-152">\<namedCaches> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="8d976-152">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
