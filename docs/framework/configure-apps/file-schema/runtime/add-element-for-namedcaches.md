---
title: Element <add> pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154502"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="53e9c-102">\<přidání prvku \<> pro> namedCaches</span><span class="sxs-lookup"><span data-stu-id="53e9c-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="53e9c-103">Přidá `namedCache` položku `namedCaches` do kolekce pro mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="53e9c-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="53e9c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="53e9c-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="53e9c-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="53e9c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="53e9c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="53e9c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<pojmenováno Caches>**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="53e9c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="53e9c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**</span><span class="sxs-lookup"><span data-stu-id="53e9c-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53e9c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e9c-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="53e9c-110">Typ</span><span class="sxs-lookup"><span data-stu-id="53e9c-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53e9c-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53e9c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="53e9c-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53e9c-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53e9c-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="53e9c-113">Attributes</span></span>  
  
|<span data-ttu-id="53e9c-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="53e9c-114">Attribute</span></span>|<span data-ttu-id="53e9c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="53e9c-115">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="53e9c-116">Celá hodnota, která určuje maximální povolenou velikost (v megabajtech), <xref:System.Runtime.Caching.MemoryCache> na kterou může instanci instanci zvětšit.</span><span class="sxs-lookup"><span data-stu-id="53e9c-116">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="53e9c-117">Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají autosizing heuristiky třídy.</span><span class="sxs-lookup"><span data-stu-id="53e9c-117">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="53e9c-118">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-118">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="53e9c-119">Celá hodnota mezi 0 a 100, která určuje maximální procento fyzicky nainstalované paměti počítače, které mohou být spotřebovány mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="53e9c-119">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="53e9c-120">Výchozí hodnota je 0, což <xref:System.Runtime.Caching.MemoryCache> znamená, že ve výchozím nastavení se používají autosizing heuristiky třídy.</span><span class="sxs-lookup"><span data-stu-id="53e9c-120">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="53e9c-121">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s absolutní a procentuální limity paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-121">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="53e9c-122">Tato hodnota je zadána ve formátu HH:MM:SS.</span><span class="sxs-lookup"><span data-stu-id="53e9c-122">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53e9c-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53e9c-123">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="53e9c-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53e9c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="53e9c-125">Element</span><span class="sxs-lookup"><span data-stu-id="53e9c-125">Element</span></span>|<span data-ttu-id="53e9c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="53e9c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53e9c-127">\<pojmenováno Caches></span><span class="sxs-lookup"><span data-stu-id="53e9c-127">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="53e9c-128">Obsahuje kolekci nastavení konfigurace <xref:System.Runtime.Caching.MemoryCache> pro pojmenované instance.</span><span class="sxs-lookup"><span data-stu-id="53e9c-128">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53e9c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53e9c-129">Remarks</span></span>  
 <span data-ttu-id="53e9c-130">Prvek `add` přidá položku `namedCaches` do kolekce pro mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-130">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="53e9c-131">Před použitím `add` prvku můžete použít prvek [clear,](clear-element-for-namedcaches.md) abyste si byli jisti, že v kolekci nejsou žádné jiné pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-131">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="53e9c-132">Tento prvek lze použít v souboru machine.config a v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="53e9c-132">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53e9c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="53e9c-133">Example</span></span>  
 <span data-ttu-id="53e9c-134">Následující příklad ukazuje, jak definovat `namedCache` nastavení pro `namedCaches` výchozí položku do kolekce pro mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="53e9c-134">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53e9c-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="53e9c-135">See also</span></span>

- [<span data-ttu-id="53e9c-136">\<namedCaches> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="53e9c-136">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
