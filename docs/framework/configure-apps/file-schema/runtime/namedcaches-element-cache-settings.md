---
title: <namedCaches> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- namedCaches element
- caching [.NET Framework], configuration
- <namedCaches> element
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
ms.openlocfilehash: 4587234ad91fa3b1abbb376bd7ae517d5abea6c3
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252452"
---
# <a name="namedcaches-element-cache-settings"></a><span data-ttu-id="4245a-102">\<namedCaches – element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="4245a-102">\<namedCaches> Element (Cache Settings)</span></span>
<span data-ttu-id="4245a-103">Určuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="4245a-103">Specifies a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span> <span data-ttu-id="4245a-104">Vlastnost odkazuje na kolekci konfiguračních nastavení z jednoho nebo více `namedCaches` prvků konfiguračního souboru. <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A></span><span class="sxs-lookup"><span data-stu-id="4245a-104">The <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> property references the collection of configuration settings from one or more `namedCaches` elements of the configuration file.</span></span>  
  
<span data-ttu-id="4245a-105">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4245a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4245a-106">&nbsp;&nbsp;[ **\<System. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4245a-106">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="4245a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<memoryCache >** ](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="4245a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="4245a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<namedCaches >**</span><span class="sxs-lookup"><span data-stu-id="4245a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<namedCaches>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4245a-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4245a-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
  <add name="default"/>   
</namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="4245a-110">type</span><span class="sxs-lookup"><span data-stu-id="4245a-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4245a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4245a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4245a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4245a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4245a-113">Attributes</span></span>  
  
|<span data-ttu-id="4245a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="4245a-114">Attribute</span></span>|<span data-ttu-id="4245a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheMemoryLimitMegabytes`|<span data-ttu-id="4245a-116">Celočíselná hodnota, která určuje maximální povolenou velikost v megabajtech, kterou může instance a <xref:System.Runtime.Caching.MemoryCache> růst.</span><span class="sxs-lookup"><span data-stu-id="4245a-116">An integer value that specifies the maximum allowable size, in megabytes, that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="4245a-117">Výchozí hodnota je 0, což znamená, že ve výchozím nastavení jsou používány heuristiky <xref:System.Runtime.Caching.MemoryCache> autovelikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="4245a-117">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`name`|<span data-ttu-id="4245a-118">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-118">The name of the cache.</span></span>|  
|`physicalMemoryLimitPercentage`|<span data-ttu-id="4245a-119">Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="4245a-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="4245a-120">Výchozí hodnota je 0, což znamená, že ve výchozím nastavení jsou používány heuristiky <xref:System.Runtime.Caching.MemoryCache> autovelikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="4245a-120">The default value is 0, which means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used by default.</span></span>|  
|`pollingInterval`|<span data-ttu-id="4245a-121">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="4245a-122">Tato hodnota je zadaná ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="4245a-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4245a-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-123">Child Elements</span></span>  
  
|<span data-ttu-id="4245a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="4245a-124">Element</span></span>|<span data-ttu-id="4245a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4245a-126">\<add></span><span class="sxs-lookup"><span data-stu-id="4245a-126">\<add></span></span>](add-element-for-namedcaches.md)|<span data-ttu-id="4245a-127">Přidá pojmenovanou mezipaměť do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-127">Adds a named cache to the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="4245a-128">\<clear></span><span class="sxs-lookup"><span data-stu-id="4245a-128">\<clear></span></span>](clear-element-for-namedcaches.md)|<span data-ttu-id="4245a-129">`namedCaches` Vymaže kolekci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-129">Clears the `namedCaches` collection for a memory cache.</span></span>|  
|[<span data-ttu-id="4245a-130">\<remove></span><span class="sxs-lookup"><span data-stu-id="4245a-130">\<remove></span></span>](remove-element-for-namedcaches.md)|<span data-ttu-id="4245a-131">Odebere pojmenovanou položku mezipaměti z `namedCaches` kolekce pro mezipaměť paměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-131">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4245a-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4245a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="4245a-133">Prvek</span><span class="sxs-lookup"><span data-stu-id="4245a-133">Element</span></span>|<span data-ttu-id="4245a-134">Popis</span><span class="sxs-lookup"><span data-stu-id="4245a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4245a-135">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="4245a-135">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="4245a-136">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="4245a-136">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
|[<span data-ttu-id="4245a-137">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="4245a-137">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="4245a-138">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="4245a-138">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
|[<span data-ttu-id="4245a-139">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="4245a-139">\<system.runtime.caching></span></span>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="4245a-140">Obsahuje typy, které umožňují implementovat ukládání výstupu do mezipaměti v aplikacích, které jsou integrovány do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4245a-140">Contains types that let you implement output caching in applications that are built into the .NET Framework.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4245a-141">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4245a-141">Remarks</span></span>  
 <span data-ttu-id="4245a-142">Oddíl konfigurace mezipaměti paměti v souboru Web. `add`config může obsahovat atributy, `remove`a `clear` pro `namedCaches` kolekci.</span><span class="sxs-lookup"><span data-stu-id="4245a-142">The memory cache configuration section of the Web.config file can contain `add`, `remove`, and `clear` attributes for the `namedCaches` collection.</span></span> <span data-ttu-id="4245a-143">Každá `namedCaches` položka je jednoznačně identifikována `name` atributem.</span><span class="sxs-lookup"><span data-stu-id="4245a-143">Each `namedCaches` entry is uniquely identified by the `name` attribute.</span></span>  
  
 <span data-ttu-id="4245a-144">Můžete načíst instance položek mezipaměti paměti odkazem na informace v konfiguračních souborech aplikace.</span><span class="sxs-lookup"><span data-stu-id="4245a-144">You can retrieve instances of memory cache entries by referencing the information in the application configuration files.</span></span> <span data-ttu-id="4245a-145">Ve výchozím nastavení obsahuje pouze výchozí instance mezipaměti záznam v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="4245a-145">By default, only the default cache instance has an entry in the configuration file.</span></span> <span data-ttu-id="4245a-146">Výchozí instance mezipaměti je instance, která je vrácena z <xref:System.Runtime.Caching.MemoryCache.Default%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4245a-146">The default cache instance is the instance that is returned from the <xref:System.Runtime.Caching.MemoryCache.Default%2A> property.</span></span>  
  
 <span data-ttu-id="4245a-147">Pokud nastavíte atribut Name na výchozí, bude element používat výchozí instanci mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="4245a-147">If you set the name attribute to "default", the element uses the default memory cache instance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4245a-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="4245a-148">Example</span></span>  
 <span data-ttu-id="4245a-149">Následující příklad ukazuje, jak nastavit název mezipaměti na výchozí název položky mezipaměti nastavením `name` atributu na "default".</span><span class="sxs-lookup"><span data-stu-id="4245a-149">The following example shows how to set the name of the cache to the default cache entry name by setting the `name` attribute to "default".</span></span>  
  
 <span data-ttu-id="4245a-150">`cacheMemoryLimitMegabytes` Atribut`physicalMemoryPercentage` a atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="4245a-150">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="4245a-151">Nastavení těchto atributů na hodnotu nula znamená, že se používají heuristické <xref:System.Runtime.Caching.MemoryCache> automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="4245a-151">Setting these attributes to zero means that the autosizing heuristics of the <xref:System.Runtime.Caching.MemoryCache> class are used.</span></span> <span data-ttu-id="4245a-152">Implementace mezipaměti porovnává aktuální zatížení paměti s použitím absolutních a procentuálních limitů paměti založených na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="4245a-152">The cache implementation compares the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4245a-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4245a-153">See also</span></span>

- [<span data-ttu-id="4245a-154">\<memoryCache – Element > (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="4245a-154">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
