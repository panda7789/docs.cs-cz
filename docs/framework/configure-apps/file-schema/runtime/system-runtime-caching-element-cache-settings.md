---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153851"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="22f1f-102">\<system.runtime.caching> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="22f1f-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="22f1f-103">Poskytuje konfiguraci pro výchozí <xref:System.Runtime.Caching.ObjectCache> implementaci `memoryCache` v paměti prostřednictvím položky v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="22f1f-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="22f1f-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="22f1f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22f1f-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span><span class="sxs-lookup"><span data-stu-id="22f1f-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22f1f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22f1f-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22f1f-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22f1f-107">Attributes and Elements</span></span>

<span data-ttu-id="22f1f-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22f1f-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22f1f-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="22f1f-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="22f1f-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22f1f-110">Child Elements</span></span>

|<span data-ttu-id="22f1f-111">Element</span><span class="sxs-lookup"><span data-stu-id="22f1f-111">Element</span></span>|<span data-ttu-id="22f1f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="22f1f-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f1f-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="22f1f-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="22f1f-114">Definuje prvek, který se používá ke konfiguraci <xref:System.Runtime.Caching.MemoryCache> mezipaměti, která je založena na třídě.</span><span class="sxs-lookup"><span data-stu-id="22f1f-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22f1f-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22f1f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="22f1f-116">Element</span><span class="sxs-lookup"><span data-stu-id="22f1f-116">Element</span></span>|<span data-ttu-id="22f1f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="22f1f-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="22f1f-118">\<>konfigurace</span><span class="sxs-lookup"><span data-stu-id="22f1f-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="22f1f-119">Určuje kořenový prvek v každém konfiguračním souboru, který používá aplikace COMMON Language runtime a .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="22f1f-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22f1f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22f1f-120">Remarks</span></span>

<span data-ttu-id="22f1f-121">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti `System.Web` zařízení, jako jsou v ASP.NET, ale bez závislosti na sestavení.</span><span class="sxs-lookup"><span data-stu-id="22f1f-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="22f1f-122">Další informace naleznete [v tématu Ukládání do mezipaměti v aplikacích rozhraní .NET Framework](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="22f1f-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22f1f-123">Funkce ukládání do mezipaměti výstupu <xref:System.Runtime.Caching> a typy v oboru názvů jsou nové v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="22f1f-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22f1f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="22f1f-124">Example</span></span>

<span data-ttu-id="22f1f-125">Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="22f1f-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="22f1f-126">Příklad ukazuje, jak nakonfigurovat `namedCaches` instanci položky pro mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="22f1f-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="22f1f-127">Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením atributu `name` "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="22f1f-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="22f1f-128">Atribut `cacheMemoryLimitMegabytes` a `physicalMemoryPercentage` atribut jsou nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="22f1f-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="22f1f-129">Nastavení těchto atributů na <xref:System.Runtime.Caching.MemoryCache> nulu znamená, že autosizing heuristiky jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="22f1f-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="22f1f-130">Implementace mezipaměti by měla porovnávat aktuální zatížení paměti s absolutními a procentuálními limity paměti každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="22f1f-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="22f1f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="22f1f-131">See also</span></span>

- [<span data-ttu-id="22f1f-132">\<memoryCache> Element (Nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="22f1f-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
