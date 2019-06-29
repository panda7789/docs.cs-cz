---
title: <system.runtime.caching> – element (nastavení mezipaměti)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbb977e05fa54b726b0cd584d287dc00c8ced995
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423257"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="96cc3-102">\<System.Runtime.Caching > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="96cc3-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="96cc3-103">Poskytuje konfiguraci pro výchozí v paměťově <xref:System.Runtime.Caching.ObjectCache> implementaci prostřednictvím `memoryCache` záznam v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="96cc3-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
 <span data-ttu-id="96cc3-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="96cc3-104">\<configuration></span></span>  
<span data-ttu-id="96cc3-105">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="96cc3-105">\<system.runtime.caching></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cc3-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96cc3-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96cc3-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="96cc3-107">Attributes and Elements</span></span>

<span data-ttu-id="96cc3-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="96cc3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96cc3-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="96cc3-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="96cc3-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="96cc3-110">Child Elements</span></span>

|<span data-ttu-id="96cc3-111">Prvek</span><span class="sxs-lookup"><span data-stu-id="96cc3-111">Element</span></span>|<span data-ttu-id="96cc3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="96cc3-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cc3-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="96cc3-113">\<memoryCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<span data-ttu-id="96cc3-114">Definuje element, který se používá ke konfiguraci, která je založená na mezipaměti <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="96cc3-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96cc3-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="96cc3-115">Parent Elements</span></span>  
  
|<span data-ttu-id="96cc3-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="96cc3-116">Element</span></span>|<span data-ttu-id="96cc3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="96cc3-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cc3-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="96cc3-118">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="96cc3-119">Určuje kořenový element v každém konfiguračním souboru, který je používán common language runtime a aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96cc3-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96cc3-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="96cc3-120">Remarks</span></span>

<span data-ttu-id="96cc3-121">Třídy v tomto oboru názvů poskytují způsob, jak používat ukládání do mezipaměti zařízení podobné těm v technologii ASP.NET, ale bez závislosti na `System.Web` sestavení.</span><span class="sxs-lookup"><span data-stu-id="96cc3-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="96cc3-122">Další informace najdete v tématu [ukládání do mezipaměti v aplikacích .NET Framework](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="96cc3-122">For more information, see [Caching in .NET Framework Applications](../../../../../docs/framework/performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96cc3-123">Výstupu do mezipaměti, funkce a typy v <xref:System.Runtime.Caching> obor názvů jsou nové v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="96cc3-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96cc3-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="96cc3-124">Example</span></span>

<span data-ttu-id="96cc3-125">Následující příklad ukazuje postup při konfiguraci mezipaměti, který je založen na <xref:System.Runtime.Caching.MemoryCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="96cc3-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="96cc3-126">Tento příklad ukazuje, jak nakonfigurovat instanci `namedCaches` zadání mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="96cc3-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="96cc3-127">Název mezipaměti, je nastavena na výchozí název položky mezipaměti tak, že nastavíte `name` atribut "Výchozí".</span><span class="sxs-lookup"><span data-stu-id="96cc3-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="96cc3-128">`cacheMemoryLimitMegabytes` Atribut a `physicalMemoryPercentage` je atribut nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="96cc3-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="96cc3-129">Nastavení těchto atributů 0 znamená, <xref:System.Runtime.Caching.MemoryCache> heuristiky automatické přizpůsobení velikosti se používají ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="96cc3-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="96cc3-130">Implementace mezipaměti by měla porovnání aktuálního zatížení paměti proti absolutní a založený na procentech paměťová omezení každé dvě minuty.</span><span class="sxs-lookup"><span data-stu-id="96cc3-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96cc3-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96cc3-131">See also</span></span>

- [<span data-ttu-id="96cc3-132">\<memoryCache > – Element (nastavení mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="96cc3-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
