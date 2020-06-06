---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: df4887c8801dcf8af06b3826673a03cbc7dbc9b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153851"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="34964-102">\<system.runtime.caching> – element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="34964-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="34964-103">Poskytuje konfiguraci pro výchozí implementaci v paměti <xref:System.Runtime.Caching.ObjectCache> prostřednictvím `memoryCache` záznamu v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="34964-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.caching>**  
  
## <a name="syntax"></a><span data-ttu-id="34964-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34964-104">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34964-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34964-105">Attributes and Elements</span></span>

<span data-ttu-id="34964-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34964-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34964-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="34964-107">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="34964-108">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="34964-108">Child Elements</span></span>

|<span data-ttu-id="34964-109">Prvek</span><span class="sxs-lookup"><span data-stu-id="34964-109">Element</span></span>|<span data-ttu-id="34964-110">Description</span><span class="sxs-lookup"><span data-stu-id="34964-110">Description</span></span>|  
|-------------|-----------------|  
|[\<memoryCache>](memorycache-element-cache-settings.md)|<span data-ttu-id="34964-111">Definuje prvek, který se používá ke konfiguraci mezipaměti založené na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="34964-111">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="34964-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="34964-112">Parent Elements</span></span>  
  
|<span data-ttu-id="34964-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="34964-113">Element</span></span>|<span data-ttu-id="34964-114">Description</span><span class="sxs-lookup"><span data-stu-id="34964-114">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="34964-115">Určuje kořenový element v každém konfiguračním souboru, který je používán modulem CLR (Common Language Runtime) a .NET Framework aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="34964-115">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34964-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34964-116">Remarks</span></span>

<span data-ttu-id="34964-117">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti, jako jsou ty v ASP.NET, ale bez závislosti na `System.Web` sestavení.</span><span class="sxs-lookup"><span data-stu-id="34964-117">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="34964-118">Další informace najdete v tématu [ukládání do mezipaměti v .NET Frameworkch aplikacích](../../../performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="34964-118">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34964-119">Funkce ukládání výstupu do mezipaměti a typy v <xref:System.Runtime.Caching> oboru názvů jsou v .NET Framework 4 nové.</span><span class="sxs-lookup"><span data-stu-id="34964-119">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34964-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="34964-120">Example</span></span>

<span data-ttu-id="34964-121">Následující příklad ukazuje, jak nakonfigurovat mezipaměť, která je založena na <xref:System.Runtime.Caching.MemoryCache> třídě.</span><span class="sxs-lookup"><span data-stu-id="34964-121">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="34964-122">V tomto příkladu se dozvíte, jak nakonfigurovat instanci `namedCaches` položky pro paměťovou mezipaměť.</span><span class="sxs-lookup"><span data-stu-id="34964-122">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="34964-123">Název mezipaměti je nastaven na výchozí název položky mezipaměti nastavením `name` atributu na výchozí.</span><span class="sxs-lookup"><span data-stu-id="34964-123">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="34964-124">`cacheMemoryLimitMegabytes`Atribut a `physicalMemoryPercentage` atribut jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="34964-124">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="34964-125">Nastavení těchto atributů na hodnotu nula znamená, že <xref:System.Runtime.Caching.MemoryCache> výchozí hodnoty pro automatické změny velikosti jsou používány ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="34964-125">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="34964-126">Implementace mezipaměti by měla porovnat aktuální zatížení paměti s absolutními a procentuálními hodnotami paměti založenými na procentech každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="34964-126">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34964-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="34964-127">See also</span></span>

- [<span data-ttu-id="34964-128">\<memoryCache>– Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="34964-128">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
