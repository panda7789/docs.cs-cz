---
title: '&lt;gcServer&gt; Element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46aae3ad287c2626123cf3f513fc72bc1acdd06e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltgcservergt-element"></a><span data-ttu-id="fdf14-102">&lt;gcServer&gt; Element</span><span class="sxs-lookup"><span data-stu-id="fdf14-102">&lt;gcServer&gt; Element</span></span>
<span data-ttu-id="fdf14-103">Určuje, zda modul common language runtime běží kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="fdf14-103">Specifies whether the common language runtime runs server garbage collection.</span></span>  
  
 <span data-ttu-id="fdf14-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fdf14-104">\<configuration></span></span>  
<span data-ttu-id="fdf14-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="fdf14-105">\<runtime></span></span>  
<span data-ttu-id="fdf14-106">\<gcServer></span><span class="sxs-lookup"><span data-stu-id="fdf14-106">\<gcServer></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdf14-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fdf14-107">Syntax</span></span>  
  
```xml  
<gcServer    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdf14-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fdf14-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fdf14-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fdf14-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdf14-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fdf14-110">Attributes</span></span>  
  
|<span data-ttu-id="fdf14-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fdf14-111">Attribute</span></span>|<span data-ttu-id="fdf14-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf14-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fdf14-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fdf14-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fdf14-114">Určuje, zda modul runtime běží kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="fdf14-114">Specifies whether the runtime runs server garbage collection.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fdf14-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="fdf14-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fdf14-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fdf14-116">Value</span></span>|<span data-ttu-id="fdf14-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf14-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fdf14-118">Kolekce paměti na serveru nelze spustit.</span><span class="sxs-lookup"><span data-stu-id="fdf14-118">Does not run server garbage collection.</span></span> <span data-ttu-id="fdf14-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="fdf14-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="fdf14-120">Kolekce paměti na serveru běží.</span><span class="sxs-lookup"><span data-stu-id="fdf14-120">Runs server garbage collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdf14-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fdf14-121">Child Elements</span></span>  
 <span data-ttu-id="fdf14-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="fdf14-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fdf14-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fdf14-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fdf14-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="fdf14-124">Element</span></span>|<span data-ttu-id="fdf14-125">Popis</span><span class="sxs-lookup"><span data-stu-id="fdf14-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fdf14-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fdf14-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fdf14-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fdf14-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdf14-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdf14-128">Remarks</span></span>  
 <span data-ttu-id="fdf14-129">Modul CLR (CLR) podporuje dva typy uvolňování paměti: uvolnění paměti pro pracovní stanice, která je k dispozici na všech systémech, a kolekce paměti na serveru, která je k dispozici v systémech s více procesory.</span><span class="sxs-lookup"><span data-stu-id="fdf14-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="fdf14-130">Můžete použít `<gcServer>` provede elementu k řízení typu uvolňování paměti modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="fdf14-130">You use the `<gcServer>` element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="fdf14-131">Použití <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> vlastnosti k určení, zda je kolekce paměti na serveru povoleno.</span><span class="sxs-lookup"><span data-stu-id="fdf14-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>  
  
 <span data-ttu-id="fdf14-132">Pro počítače, jeden procesor by měla být uvolňování výchozí pracovní stanice nejrychlejší možnost.</span><span class="sxs-lookup"><span data-stu-id="fdf14-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="fdf14-133">Pracovní stanice nebo server lze použít pro počítače se dvěma procesory.</span><span class="sxs-lookup"><span data-stu-id="fdf14-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="fdf14-134">Kolekce paměti na serveru by měl být nejrychlejší možnost pro více než dva procesory.</span><span class="sxs-lookup"><span data-stu-id="fdf14-134">Server garbage collection should be the fastest option for more than two processors.</span></span>  
  
 <span data-ttu-id="fdf14-135">Tento element může použít pouze v konfiguračním souboru aplikace; je ignorován, pokud je v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="fdf14-135">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdf14-136">V rozhraní .NET Framework 4 a dřívějších verzích souběžné uvolňování paměti není k dispozici při uvolňování paměti serveru je povoleno.</span><span class="sxs-lookup"><span data-stu-id="fdf14-136">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="fdf14-137">Od verze [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], je souběžné uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="fdf14-137">Starting with the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], server garbage collection is concurrent.</span></span> <span data-ttu-id="fdf14-138">Chcete-li použít server nesouběžného uvolňování paměti, nastavte `<gcServer>` element `true` a [ \<gcconcurrent – > element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) k `false`.</span><span class="sxs-lookup"><span data-stu-id="fdf14-138">To use non-concurrent server garbage collection, set the `<gcServer>` element to `true` and the [\<gcConcurrent> element](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) to `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdf14-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdf14-139">Example</span></span>  
 <span data-ttu-id="fdf14-140">Následující příklad povolí kolekce paměti na serveru.</span><span class="sxs-lookup"><span data-stu-id="fdf14-140">The following example enables server garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcServer enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fdf14-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdf14-141">See Also</span></span>  
 <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="fdf14-142">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="fdf14-142">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="fdf14-143">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fdf14-143">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="fdf14-144">Postupy: zakázat souběžná kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="fdf14-144">How to: Disable Concurrent Garbage Collection</span></span>](http://msdn.microsoft.com/library/ba2c6c67-5778-497c-9fac-5f793b5500c7)
