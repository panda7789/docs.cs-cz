---
title: <add> – element pro <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- add element for <namedCaches>
- <add> element for <namedCaches>
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
ms.openlocfilehash: c1345022b79df371ad9c89a39a0a8b625e26608c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154502"
---
# <a name="add-element-for-namedcaches"></a><span data-ttu-id="058ee-102">\<add> – element pro \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="058ee-102">\<add> Element for \<namedCaches></span></span>
<span data-ttu-id="058ee-103">Přidá `namedCache` položku do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-103">Adds a `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="058ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="058ee-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <add name="Default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="058ee-105">Typ</span><span class="sxs-lookup"><span data-stu-id="058ee-105">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="058ee-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="058ee-106">Attributes and Elements</span></span>  
 <span data-ttu-id="058ee-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="058ee-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="058ee-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="058ee-108">Attributes</span></span>  
  
|<span data-ttu-id="058ee-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="058ee-109">Attribute</span></span>|<span data-ttu-id="058ee-110">Popis</span><span class="sxs-lookup"><span data-stu-id="058ee-110">Description</span></span>|  
|-|-|  
|`CacheMemoryLimitMegabytes`|<span data-ttu-id="058ee-111">Celočíselná hodnota, která určuje maximální povolenou velikost (v megabajtech), kterou může instance a <xref:System.Runtime.Caching.MemoryCache> růst.</span><span class="sxs-lookup"><span data-stu-id="058ee-111">An integer value that specifies the maximum allowed size (in megabytes) that an instance of a <xref:System.Runtime.Caching.MemoryCache> can grow to.</span></span> <span data-ttu-id="058ee-112">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="058ee-112">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`Name`|<span data-ttu-id="058ee-113">Název mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-113">The name of the cache.</span></span>|  
|`PhysicalMemoryLimitPercentage`|<span data-ttu-id="058ee-114">Celočíselná hodnota mezi 0 a 100, která určuje maximální procento fyzicky instalované paměti počítače, kterou může mezipaměť spotřebovat.</span><span class="sxs-lookup"><span data-stu-id="058ee-114">An integer value between 0 and 100 that specifies the maximum percentage of physically installed computer memory that can be consumed by the cache.</span></span> <span data-ttu-id="058ee-115">Výchozí hodnota je 0, což znamená, že <xref:System.Runtime.Caching.MemoryCache> ve výchozím nastavení jsou používány heuristické automatické změny velikosti třídy.</span><span class="sxs-lookup"><span data-stu-id="058ee-115">The default value is 0, which means that the <xref:System.Runtime.Caching.MemoryCache> class's autosizing heuristics are used by default.</span></span>|  
|`PollingInterval`|<span data-ttu-id="058ee-116">Hodnota, která označuje časový interval, po kterém implementace mezipaměti porovnává aktuální zatížení paměti s omezeními na základě absolutního a procenta velikosti paměti, které jsou nastaveny pro instanci mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-116">A value that indicates the time interval after which the cache implementation compares the current memory load against the absolute and percentage-based memory limits that are set for the cache instance.</span></span> <span data-ttu-id="058ee-117">Tato hodnota je zadaná ve formátu "HH: MM: SS".</span><span class="sxs-lookup"><span data-stu-id="058ee-117">This value is entered in "HH:MM:SS" format.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="058ee-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="058ee-118">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="058ee-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="058ee-119">Parent Elements</span></span>  
  
|<span data-ttu-id="058ee-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="058ee-120">Element</span></span>|<span data-ttu-id="058ee-121">Description</span><span class="sxs-lookup"><span data-stu-id="058ee-121">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="058ee-122">Obsahuje kolekci konfiguračních nastavení pro pojmenované <xref:System.Runtime.Caching.MemoryCache> instance.</span><span class="sxs-lookup"><span data-stu-id="058ee-122">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="058ee-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="058ee-123">Remarks</span></span>  
 <span data-ttu-id="058ee-124">`add`Element přidá položku do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-124">The `add` element adds an entry to the `namedCaches` collection for a memory cache.</span></span> <span data-ttu-id="058ee-125">Element [clear](clear-element-for-namedcaches.md) lze použít před použitím `add` elementu, aby bylo jisté, že v kolekci nejsou žádné další pojmenované mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-125">You can use the [clear](clear-element-for-namedcaches.md) element before you use the `add` element to be certain that there are no other named caches in the collection.</span></span> <span data-ttu-id="058ee-126">Tento element lze použít v souboru Machine. config a v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="058ee-126">This element can be used in the machine.config file and in the Web.config file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="058ee-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="058ee-127">Example</span></span>  
 <span data-ttu-id="058ee-128">Následující příklad ukazuje, jak definovat nastavení pro výchozí `namedCache` položku do `namedCaches` kolekce mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="058ee-128">The following example shows how to define settings for the default `namedCache` entry to the `namedCaches` collection for a memory cache.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="058ee-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="058ee-129">See also</span></span>

- [<span data-ttu-id="058ee-130">\<namedCaches>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="058ee-130">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
