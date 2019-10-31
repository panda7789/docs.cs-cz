---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115507"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="5fc22-102">\<element System. Runtime. Caching > elementu (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="5fc22-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="5fc22-103">Poskytuje konfiguraci pro výchozí implementaci <xref:System.Runtime.Caching.ObjectCache> v paměti prostřednictvím položky `memoryCache` v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="5fc22-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="5fc22-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="5fc22-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5fc22-105">&nbsp;&nbsp; **\<System. Runtime. caching >**</span><span class="sxs-lookup"><span data-stu-id="5fc22-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fc22-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fc22-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fc22-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5fc22-107">Attributes and Elements</span></span>

<span data-ttu-id="5fc22-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5fc22-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fc22-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="5fc22-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="5fc22-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5fc22-110">Child Elements</span></span>

|<span data-ttu-id="5fc22-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fc22-111">Element</span></span>|<span data-ttu-id="5fc22-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5fc22-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fc22-113">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="5fc22-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="5fc22-114">Definuje prvek, který se používá ke konfiguraci mezipaměti, která je založena na třídě <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="5fc22-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5fc22-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5fc22-115">Parent Elements</span></span>  
  
|<span data-ttu-id="5fc22-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="5fc22-116">Element</span></span>|<span data-ttu-id="5fc22-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5fc22-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5fc22-118">Konfigurace \<</span><span class="sxs-lookup"><span data-stu-id="5fc22-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="5fc22-119">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5fc22-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fc22-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fc22-120">Remarks</span></span>

<span data-ttu-id="5fc22-121">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti jako v ASP.NET, ale bez závislosti na sestavení `System.Web`.</span><span class="sxs-lookup"><span data-stu-id="5fc22-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="5fc22-122">Další informace najdete v tématu [ukládání do mezipaměti v .NET Frameworkch aplikacích](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="5fc22-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fc22-123">Funkce ukládání výstupu do mezipaměti a typy v oboru názvů <xref:System.Runtime.Caching> jsou v .NET Framework 4 nové.</span><span class="sxs-lookup"><span data-stu-id="5fc22-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fc22-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fc22-124">Example</span></span>

<span data-ttu-id="5fc22-125">Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na třídě <xref:System.Runtime.Caching.MemoryCache>.</span><span class="sxs-lookup"><span data-stu-id="5fc22-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="5fc22-126">Příklad ukazuje, jak nakonfigurovat instanci položky `namedCaches` pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="5fc22-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="5fc22-127">Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením atributu `name` na výchozí.</span><span class="sxs-lookup"><span data-stu-id="5fc22-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="5fc22-128">Atribut `cacheMemoryLimitMegabytes` a atribut `physicalMemoryPercentage` jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="5fc22-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="5fc22-129">Nastavení těchto atributů na hodnotu nula znamená, že ve výchozím nastavení se používají heuristiky <xref:System.Runtime.Caching.MemoryCache> automatické velikosti.</span><span class="sxs-lookup"><span data-stu-id="5fc22-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="5fc22-130">Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="5fc22-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5fc22-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fc22-131">See also</span></span>

- [<span data-ttu-id="5fc22-132">\<element > memoryCache (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="5fc22-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
