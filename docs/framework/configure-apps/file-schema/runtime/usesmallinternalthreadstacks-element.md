---
title: "&lt;Usesmallinternalthreadstacks –&gt; – Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UseSmallInternalThreadStacks element
- <UseSmallInternalThreadStacks> element
ms.assetid: 1e3f6ec0-1cac-4e1c-9c81-17d948ae5874
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2558423b412333a4d6ac9f650ad8ff3dab449d74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltusesmallinternalthreadstacksgt-element"></a><span data-ttu-id="1df8b-102">&lt;Usesmallinternalthreadstacks –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="1df8b-102">&lt;UseSmallInternalThreadStacks&gt; Element</span></span>
<span data-ttu-id="1df8b-103">Požadavky, modul CLR (CLR) snížit velikost paměti, použijte zadáním velikosti explicitní zásobníku při vytváření určitých vláken, která se používá interně, místo použití výchozí velikost zásobníku pro tyto vlákna.</span><span class="sxs-lookup"><span data-stu-id="1df8b-103">Requests that the common language runtime (CLR) reduce memory use by specifying explicit stack sizes when it creates certain threads that it uses internally, instead of using the default stack size for those threads.</span></span>  
  
 <span data-ttu-id="1df8b-104">\<Konfigurace > elementu</span><span class="sxs-lookup"><span data-stu-id="1df8b-104">\<configuration> Element</span></span>  
<span data-ttu-id="1df8b-105">\<modul runtime > elementu</span><span class="sxs-lookup"><span data-stu-id="1df8b-105">\<runtime> Element</span></span>  
<span data-ttu-id="1df8b-106">\<Usesmallinternalthreadstacks – > elementu</span><span class="sxs-lookup"><span data-stu-id="1df8b-106">\<UseSmallInternalThreadStacks> Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1df8b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1df8b-107">Syntax</span></span>  
  
```xml  
<UseSmallInternalThreadStacks enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1df8b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1df8b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1df8b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1df8b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1df8b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="1df8b-110">Attributes</span></span>  
  
|<span data-ttu-id="1df8b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="1df8b-111">Attribute</span></span>|<span data-ttu-id="1df8b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="1df8b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1df8b-113">povoleno</span><span class="sxs-lookup"><span data-stu-id="1df8b-113">enabled</span></span>|<span data-ttu-id="1df8b-114">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1df8b-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="1df8b-115">Určuje, zda požadavek, aby velikosti CLR použijte explicitní zásobníku místo výchozí velikost zásobníku při vytváření určitých vláken, která se používá interně.</span><span class="sxs-lookup"><span data-stu-id="1df8b-115">Specifies whether to request that the CLR use explicit stack sizes instead of the default stack size when it creates certain threads that it uses internally.</span></span> <span data-ttu-id="1df8b-116">Explicitní zásobníku velikosti jsou menší než výchozí velikost zásobníku 1 MB.</span><span class="sxs-lookup"><span data-stu-id="1df8b-116">The explicit stack sizes are smaller than the default stack size of 1 MB.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="1df8b-117">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="1df8b-117">enabled Attribute</span></span>  
  
|<span data-ttu-id="1df8b-118">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1df8b-118">Value</span></span>|<span data-ttu-id="1df8b-119">Popis</span><span class="sxs-lookup"><span data-stu-id="1df8b-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1df8b-120">true</span><span class="sxs-lookup"><span data-stu-id="1df8b-120">true</span></span>|<span data-ttu-id="1df8b-121">Požádat o velikosti explicitní zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1df8b-121">Request explicit stack sizes.</span></span>|  
|<span data-ttu-id="1df8b-122">false</span><span class="sxs-lookup"><span data-stu-id="1df8b-122">false</span></span>|<span data-ttu-id="1df8b-123">Použijte výchozí velikost zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1df8b-123">Use the default stack size.</span></span> <span data-ttu-id="1df8b-124">Toto je výchozí nastavení pro [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1df8b-124">This is the default for the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1df8b-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1df8b-125">Child Elements</span></span>  
 <span data-ttu-id="1df8b-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="1df8b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1df8b-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1df8b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="1df8b-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="1df8b-128">Element</span></span>|<span data-ttu-id="1df8b-129">Popis</span><span class="sxs-lookup"><span data-stu-id="1df8b-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="1df8b-130">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1df8b-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="1df8b-131">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1df8b-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1df8b-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1df8b-132">Remarks</span></span>  
 <span data-ttu-id="1df8b-133">Tento element konfigurace slouží k vyžádání použití snížené virtuální paměti v procesu, protože velikosti explicitní vlákno, které modulu CLR používá pro interní podprocesů, pokud je dodržení požadavku, jsou menší než výchozí velikost.</span><span class="sxs-lookup"><span data-stu-id="1df8b-133">This configuration element is used to request reduced virtual memory use in a process, because the explicit thread sizes that the CLR uses for its internal threads, if the request is honored, are smaller than the default size.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1df8b-134">Tento element konfigurace je požadavek na modulu CLR, nikoli absolutní požadavek.</span><span class="sxs-lookup"><span data-stu-id="1df8b-134">This configuration element is a request to the CLR rather than an absolute requirement.</span></span> <span data-ttu-id="1df8b-135">V [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], žádost je dodržení pouze pro x86 architektura.</span><span class="sxs-lookup"><span data-stu-id="1df8b-135">In the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the request is honored only for the x86 architecture.</span></span> <span data-ttu-id="1df8b-136">Tento element může ignorován zcela v budoucích verzích modulu CLR nebo nahrazena explicitní zásobníku velikosti, které se vždycky použijí pro vybrané interní vlákna.</span><span class="sxs-lookup"><span data-stu-id="1df8b-136">This element might be ignored completely in future versions of the CLR, or replaced by explicit stack sizes that are always used for selected internal threads.</span></span>  
  
 <span data-ttu-id="1df8b-137">Určení, že tento element konfigurace obchoduje spolehlivost pro menší využití virtuální paměti Pokud modulu CLR ctí požadavek, protože menší velikost zásobníku může potenciálně zásobníku přesahuje více pravděpodobně.</span><span class="sxs-lookup"><span data-stu-id="1df8b-137">Specifying this configuration element trades reliability for smaller virtual memory use if the CLR honors the request, because smaller stack sizes could potentially make stack overflows more likely.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1df8b-138">Příklad</span><span class="sxs-lookup"><span data-stu-id="1df8b-138">Example</span></span>  
 <span data-ttu-id="1df8b-139">Následující příklad ukazuje, jak požádat o explicitní zásobníku použití CLR velikosti pro konkrétní vláken, která se používá interně.</span><span class="sxs-lookup"><span data-stu-id="1df8b-139">The following example shows how to request that the CLR use explicit stack sizes for certain threads that it uses internally.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <UseSmallInternalThreadStacks enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1df8b-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="1df8b-140">See Also</span></span>  
 [<span data-ttu-id="1df8b-141">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="1df8b-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="1df8b-142">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1df8b-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
