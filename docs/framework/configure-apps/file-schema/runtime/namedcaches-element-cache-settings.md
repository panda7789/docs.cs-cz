---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: e0640ca18d386141f3c03135019eb4fe959b5bf8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153955"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="69463-102">\<namedCaches> – element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="69463-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="69463-103">Určuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="69463-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="69463-104"><xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A>Vlastnost odkazuje na kolekci konfiguračních nastavení z jednoho nebo více `namedCaches` prvků konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="69463-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**  
  
## <a name="syntax"></a><span data-ttu-id="69463-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69463-105">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="69463-106">Typ</span><span class="sxs-lookup"><span data-stu-id="69463-106">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69463-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69463-107">Attributes and Elements</span></span>  
 <span data-ttu-id="69463-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69463-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69463-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="69463-109">Attributes</span></span>  
  
|<span data-ttu-id="69463-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="69463-110">Attribute</span></span>|<span data-ttu-id="69463-111">Popis</span><span class="sxs-lookup"><span data-stu-id="69463-111">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="69463-112">Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, kterou může instance a <xref:System.Runtime.Caching.MemoryCache> růst.</span><span class="sxs-lookup"><span data-stu-id="69463-112">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="69463-113">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristiky autovelikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="69463-113">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="69463-114">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="69463-114">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="69463-115">Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="69463-115">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="69463-116">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristiky autovelikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="69463-116">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="69463-117">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="69463-117">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="69463-118">Tato hodnota je zadaná ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="69463-118">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69463-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69463-119">Child Elements</span></span>  
  
|<span data-ttu-id="69463-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="69463-120">Element</span></span>|<span data-ttu-id="69463-121">Description</span><span class="sxs-lookup"><span data-stu-id="69463-121">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-namedcaches.md)|<span data-ttu-id="69463-122">Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="69463-122">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[\<clear>](clear-element-for-namedcaches.md)|<span data-ttu-id="69463-123">Vymaže `namedCaches` kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="69463-123">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[\<remove>](remove-element-for-namedcaches.md)|<span data-ttu-id="69463-124">Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.</span><span class="sxs-lookup"><span data-stu-id="69463-124">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69463-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69463-125">Parent Elements</span></span>  
  
|<span data-ttu-id="69463-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="69463-126">Element</span></span>|<span data-ttu-id="69463-127">Description</span><span class="sxs-lookup"><span data-stu-id="69463-127">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="69463-128">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="69463-128">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="69463-129">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="69463-129">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="69463-130">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="69463-130">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69463-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69463-131">Remarks</span></span>  
 <span data-ttu-id="69463-132">Oddíl konfigurace mezipaměti paměti v souboru Web. config může obsahovat `add` `remove` atributy, a `clear` pro `namedCaches` kolekci.</span><span class="sxs-lookup"><span data-stu-id="69463-132">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="69463-133">Každá `namedCaches` položka je jednoznačně identifikována `name` atributem.</span><span class="sxs-lookup"><span data-stu-id="69463-133">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="69463-134">Můžete načíst instance položek mezipaměti paměti odkazem na informace v konfiguračních souborech aplikace.</span><span class="sxs-lookup"><span data-stu-id="69463-134">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="69463-135">Ve výchozím nastavení obsahuje pouze výchozí instance mezipaměti záznam v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="69463-135">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="69463-136">Výchozí instance mezipaměti je instance, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69463-136">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="69463-137">Pokud nastavíte atribut Name na výchozí, bude element používat výchozí instanci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="69463-137">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69463-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="69463-138">Example</span></span>  
 <span data-ttu-id="69463-139">Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název položky mezipaměti nastavením `name` atributu na "default".</span><span class="sxs-lookup"><span data-stu-id="69463-139">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="69463-140">`cacheMemoryLimitMegabytes`Atribut a `physicalMemoryPercentage` atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="69463-140">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="69463-141">Nastavení těchto atributů na hodnotu nula znamená, že se používají heuristické automatické změny velikosti <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="69463-141">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="69463-142">Implementace mezipaměti porovnává aktuální zatížení paměti s použitím absolutních a procentuálních limitů paměti založených na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="69463-142">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="69463-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="69463-143">See also</span></span>

- [<span data-ttu-id="69463-144">\<memoryCache>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="69463-144">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
