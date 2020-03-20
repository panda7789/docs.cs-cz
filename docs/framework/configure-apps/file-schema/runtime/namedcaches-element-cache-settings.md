---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153955"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="493bb-102">\<namedCaches> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="493bb-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="493bb-103">Určuje kolekci nastavení konfigurace pro <xref:System.Runtime.Caching.MemoryCache> pojmenované instance.</span><span class="sxs-lookup"><span data-stu-id="493bb-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="493bb-104">Vlastnost <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> odkazuje na kolekci nastavení konfigurace `namedCaches` z jednoho nebo více prvků konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="493bb-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="493bb-105">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="493bb-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="493bb-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="493bb-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="493bb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="493bb-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="493bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<pojmenováno Caches>**</span><span class="sxs-lookup"><span data-stu-id="493bb-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="493bb-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="493bb-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="493bb-110">Typ</span><span class="sxs-lookup"><span data-stu-id="493bb-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="493bb-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="493bb-111">Attributes and Elements</span></span>  
 <span data-ttu-id="493bb-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="493bb-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="493bb-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="493bb-113">Attributes</span></span>  
  
|<span data-ttu-id="493bb-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="493bb-114">Attribute</span></span>|<span data-ttu-id="493bb-115">Popis</span><span class="sxs-lookup"><span data-stu-id="493bb-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="493bb-116">Celá hodnota, která určuje maximální přípustnou velikost v megabajtech, na <xref:System.Runtime.Caching.MemoryCache> kterou může instanci instanci zvětšit.</span><span class="sxs-lookup"><span data-stu-id="493bb-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="493bb-117">Výchozí hodnota je 0, což znamená, že autosizing <xref:System.Runtime.Caching.MemoryCache> heuristiky třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="493bb-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="493bb-118">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="493bb-119">Celá hodnota mezi 0 a 100, která určuje maximální procento fyzicky nainstalované paměti počítače, které mohou být spotřebovány mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="493bb-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="493bb-120">Výchozí hodnota je 0, což znamená, že autosizing <xref:System.Runtime.Caching.MemoryCache> heuristiky třídy se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="493bb-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="493bb-121">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="493bb-122">Tato hodnota je zadána ve formátu HH:MM:SS.</span><span class="sxs-lookup"><span data-stu-id="493bb-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="493bb-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="493bb-123">Child Elements</span></span>  
  
|<span data-ttu-id="493bb-124">Element</span><span class="sxs-lookup"><span data-stu-id="493bb-124">Element</span></span>|<span data-ttu-id="493bb-125">Popis</span><span class="sxs-lookup"><span data-stu-id="493bb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="493bb-126">\<přidat></span><span class="sxs-lookup"><span data-stu-id="493bb-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="493bb-127">Přidá pojmenovanou `namedCaches` mezipaměť do kolekce mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="493bb-128">\<jasné></span><span class="sxs-lookup"><span data-stu-id="493bb-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="493bb-129">Vymaže kolekci `namedCaches` mezipaměti mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="493bb-130">\<odebrat></span><span class="sxs-lookup"><span data-stu-id="493bb-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="493bb-131">Odebere pojmenovanou položku mezipaměti `namedCaches` z kolekce mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="493bb-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="493bb-132">Parent Elements</span></span>  
  
|<span data-ttu-id="493bb-133">Element</span><span class="sxs-lookup"><span data-stu-id="493bb-133">Element</span></span>|<span data-ttu-id="493bb-134">Popis</span><span class="sxs-lookup"><span data-stu-id="493bb-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="493bb-135">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="493bb-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="493bb-136">Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="493bb-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="493bb-137">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="493bb-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="493bb-138">Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě.</span><span class="sxs-lookup"><span data-stu-id="493bb-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="493bb-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="493bb-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="493bb-140">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="493bb-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="493bb-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="493bb-141">Remarks</span></span>  
 <span data-ttu-id="493bb-142">Oddíl konfigurace mezipaměti souboru Web.config `add` `remove`může `clear` obsahovat , `namedCaches` a atributy kolekce.</span><span class="sxs-lookup"><span data-stu-id="493bb-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="493bb-143">Každá `namedCaches` položka je jednoznačně `name` identifikována atributem.</span><span class="sxs-lookup"><span data-stu-id="493bb-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="493bb-144">Instance položek mezipaměti mezipaměti můžete načíst odkazováním na informace v konfiguračních souborech aplikace.</span><span class="sxs-lookup"><span data-stu-id="493bb-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="493bb-145">Ve výchozím nastavení má v konfiguračním souboru položku pouze výchozí instance mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="493bb-146">Výchozí instance mezipaměti je instance, <xref:System.Runtime.Caching.MemoryCache.Default%2A> která je vrácena z vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="493bb-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="493bb-147">Pokud nastavíte atribut name na "default", prvek použije výchozí instanci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="493bb-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="493bb-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="493bb-148">Example</span></span>  
 <span data-ttu-id="493bb-149">Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název `name` položky mezipaměti nastavením atributu na "výchozí".</span><span class="sxs-lookup"><span data-stu-id="493bb-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="493bb-150">Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryPercentage` atribut jsou nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="493bb-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="493bb-151">Nastavení těchto atributů na nulu znamená, že se <xref:System.Runtime.Caching.MemoryCache> používají autosizing heuristiky třídy.</span><span class="sxs-lookup"><span data-stu-id="493bb-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="493bb-152">Implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="493bb-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="493bb-153">Viz také</span><span class="sxs-lookup"><span data-stu-id="493bb-153">See also</span></span>

- [<span data-ttu-id="493bb-154">\<memoryCache> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="493bb-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
