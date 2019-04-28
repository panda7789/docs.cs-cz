---
title: Element <UseSmallInternalThreadStacks>
ms.date: 03/30/2017
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9833d768b84faaf6e1dcf8c9cb8b00b92adc3d1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673983"
---
# <a name="usesmallinternalthreadstacks-element"></a><span data-ttu-id="d83c6-102">\<Usesmallinternalthreadstacks – > – Element</span><span class="sxs-lookup"><span data-stu-id="d83c6-102">\<UseSmallInternalThreadStacks> Element</span></span>
<span data-ttu-id="d83c6-103">Požadavky, že modul CLR (CLR) snížit velikost paměti, používat tak, že zadáte zásobníku explicitní velikost při vytváření příslušná vlákna, které se používá interně, místo použití výchozí velikost zásobníku pro tato vlákna.</span><span class="sxs-lookup"><span data-stu-id="d83c6-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="d83c6-104">\<Konfigurace > – Element</span><span class="sxs-lookup"><span data-stu-id="d83c6-104">\<configuration> Element</span></span>  
<span data-ttu-id="d83c6-105">\<modul runtime > – Element</span><span class="sxs-lookup"><span data-stu-id="d83c6-105">\<runtime> Element</span></span>  
<span data-ttu-id="d83c6-106">\<Usesmallinternalthreadstacks – > – Element</span><span class="sxs-lookup"><span data-stu-id="d83c6-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d83c6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d83c6-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d83c6-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d83c6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d83c6-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d83c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d83c6-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d83c6-110">Attributes</span></span>  
  
|<span data-ttu-id="d83c6-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d83c6-111">Attribute</span></span>|<span data-ttu-id="d83c6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d83c6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d83c6-113">Povoleno</span><span class="sxs-lookup"><span data-stu-id="d83c6-113">enabled</span></span>|<span data-ttu-id="d83c6-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d83c6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="d83c6-115">Určuje, zda požadavek, aby velikosti zásobníku explicitní použití CLR místo výchozí velikost zásobníku při vytváření příslušná vlákna, které se používá interně.</span><span class="sxs-lookup"><span data-stu-id="d83c6-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="d83c6-116">Explicitní zásobníku velikosti jsou menší než výchozí velikost zásobníku 1 MB.</span><span class="sxs-lookup"><span data-stu-id="d83c6-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="d83c6-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="d83c6-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="d83c6-118">Value</span><span class="sxs-lookup"><span data-stu-id="d83c6-118">Value</span></span>|<span data-ttu-id="d83c6-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d83c6-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d83c6-120">true</span><span class="sxs-lookup"><span data-stu-id="d83c6-120">true</span></span>|<span data-ttu-id="d83c6-121">Žádost o velikosti explicitní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d83c6-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="d83c6-122">false</span><span class="sxs-lookup"><span data-stu-id="d83c6-122">false</span></span>|<span data-ttu-id="d83c6-123">Použijte výchozí velikost zásobníku.</span><span class="sxs-lookup"><span data-stu-id="d83c6-123">Use the default stack size.</span></span> <span data-ttu-id="d83c6-124">Toto je výchozí nastavení pro [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d83c6-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d83c6-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d83c6-125">Child Elements</span></span>  
 <span data-ttu-id="d83c6-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="d83c6-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d83c6-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d83c6-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d83c6-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="d83c6-128">Element</span></span>|<span data-ttu-id="d83c6-129">Popis</span><span class="sxs-lookup"><span data-stu-id="d83c6-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d83c6-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d83c6-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="d83c6-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d83c6-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d83c6-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d83c6-132">Remarks</span></span>  
 <span data-ttu-id="d83c6-133">Tento prvek konfigurace slouží k vyžádání použití nižší virtuální paměti v procesu, protože velikosti explicitní vlákno, které používá modul CLR pro interní podprocesů, pokud požadavek zachovaný, jsou menší než výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="d83c6-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d83c6-134">Tento prvek konfigurace je požadavek na modul CLR, nikoli nezbytný požadavek.</span><span class="sxs-lookup"><span data-stu-id="d83c6-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="d83c6-135">V [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], požadavek zachovaný pouze pro x86 architektury.</span><span class="sxs-lookup"><span data-stu-id="d83c6-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="d83c6-136">Tento element může být ignorovány zcela v budoucích verzích CLR nebo nahrazuje velikosti explicitní zásobníku, které se vždycky použijí pro interní vybraná vlákna.</span><span class="sxs-lookup"><span data-stu-id="d83c6-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="d83c6-137">Určení, že tento prvek konfigurace obchoduje spolehlivost pro menší využití virtuální paměti Pokud CLR respektuje požadavek, protože menší velikosti zásobníku může potenciálně zásobníku pravděpodobně přetečení.</span><span class="sxs-lookup"><span data-stu-id="d83c6-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d83c6-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="d83c6-138">Example</span></span>  
 <span data-ttu-id="d83c6-139">Následující příklad ukazuje, jak požádat o zásobníku explicitní použití CLR velikosti pro určité vlákna, která se používá interně.</span><span class="sxs-lookup"><span data-stu-id="d83c6-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d83c6-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d83c6-140">See also</span></span>

- [<span data-ttu-id="d83c6-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d83c6-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="d83c6-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d83c6-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
