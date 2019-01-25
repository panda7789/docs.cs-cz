---
title: '&lt;gcConcurrent&gt; Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c83576c5c46d9a32f990d23fa20b116be36e4c0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611993"
---
# <a name="ltgcconcurrentgt-element"></a><span data-ttu-id="ead6b-102">&lt;gcConcurrent&gt; Element</span><span class="sxs-lookup"><span data-stu-id="ead6b-102">&lt;gcConcurrent&gt; Element</span></span>
<span data-ttu-id="ead6b-103">Určuje, zda modul common language runtime spustí uvolnění paměti na samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="ead6b-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>  
  
 <span data-ttu-id="ead6b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="ead6b-104">\<configuration></span></span>  
<span data-ttu-id="ead6b-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="ead6b-105">\<runtime></span></span>  
<span data-ttu-id="ead6b-106">\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="ead6b-106">\<gcConcurrent></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead6b-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ead6b-107">Syntax</span></span>  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ead6b-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ead6b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ead6b-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ead6b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ead6b-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ead6b-110">Attributes</span></span>  
  
|<span data-ttu-id="ead6b-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ead6b-111">Attribute</span></span>|<span data-ttu-id="ead6b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ead6b-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="ead6b-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ead6b-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ead6b-114">Určuje, zda modul runtime souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ead6b-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="ead6b-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ead6b-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="ead6b-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ead6b-116">Value</span></span>|<span data-ttu-id="ead6b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ead6b-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="ead6b-118">Nejde spustit uvolňování paměti současně.</span><span class="sxs-lookup"><span data-stu-id="ead6b-118">Does not run garbage collection concurrently.</span></span>|  
|`true`|<span data-ttu-id="ead6b-119">Uvolňování paměti běží souběžně.</span><span class="sxs-lookup"><span data-stu-id="ead6b-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="ead6b-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ead6b-120">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ead6b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ead6b-121">Child Elements</span></span>  
 <span data-ttu-id="ead6b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="ead6b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ead6b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ead6b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="ead6b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ead6b-124">Element</span></span>|<span data-ttu-id="ead6b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ead6b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="ead6b-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ead6b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ead6b-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ead6b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ead6b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ead6b-128">Remarks</span></span>  
 <span data-ttu-id="ead6b-129">Před rozhraní .NET Framework 4 uvolnění paměti pracovní stanice nepodporuje souběžné uvolňování paměti, které provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="ead6b-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ead6b-130">Souběžné uvolňování paměti v rozhraní .NET Framework 4, byl nahrazen uvolňování paměti, který také provádí uvolňování paměti na pozadí v samostatném vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ead6b-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="ead6b-131">Od verze rozhraní .NET Framework 4.5, shromažďování na pozadí jsou dostupné v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="ead6b-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="ead6b-132">`<gcConcurrent>` Prvek určuje, zda modul runtime provádí buď souběžné nebo při uvolňování paměti na pozadí, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="ead6b-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it is available, or whether it performs garbage collection in the foreground.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ead6b-133">Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ead6b-133">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="ead6b-134">Podmínky *souběžných* a *pozadí* zaměňují v dokumentaci k rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ead6b-134">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="ead6b-135">Chcete-li zakázat uvolňování paměti na pozadí, použijte `<gcConcurrent>` elementu, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="ead6b-135">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>  
  
 <span data-ttu-id="ead6b-136">Ve výchozím nastavení používá modul runtime souběžné nebo uvolňování paměti na pozadí, které je optimalizováno pro zpoždění.</span><span class="sxs-lookup"><span data-stu-id="ead6b-136">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="ead6b-137">Pokud aplikace vyžaduje interakci uživatele náročné, nechte souběžné uvolňování paměti povoleno, chcete-li minimalizovat čas pozastavení aplikace pro provádění uvolnění.</span><span class="sxs-lookup"><span data-stu-id="ead6b-137">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="ead6b-138">Pokud jste nastavili `enabled` atribut `<gcConcurrent>` element `false`, používá modul runtime nesouběžné uvolňování paměti, které je optimalizováno pro výkon.</span><span class="sxs-lookup"><span data-stu-id="ead6b-138">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="ead6b-139">Následující konfigurační soubor zakáže uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ead6b-139">The following configuration file disables background garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="ead6b-140">Pokud je `<gcConcurrentSetting>` nastavení v konfiguračním souboru počítače, definuje výchozí hodnotu pro všechny aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ead6b-140">If there is a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="ead6b-141">Nastavení konfiguračního souboru počítače přepíše nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="ead6b-141">The machine configuration file setting overrides the application configuration file setting.</span></span>  
  
 <span data-ttu-id="ead6b-142">Další informace o současných a uvolňování paměti na pozadí, naleznete v části "souběžné uvolňování paměti" v [základy kolekce paměti](../../../../../docs/standard/garbage-collection/fundamentals.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="ead6b-142">For more information on concurrent and background garbage collection, see the "Concurrent garbage collection" section in the [Fundamentals of Garbage Collection](../../../../../docs/standard/garbage-collection/fundamentals.md) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ead6b-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="ead6b-143">Example</span></span>  
 <span data-ttu-id="ead6b-144">Následující příklad umožňuje souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ead6b-144">The following example enables concurrent garbage collection.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ead6b-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ead6b-145">See also</span></span>
- [<span data-ttu-id="ead6b-146">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ead6b-146">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="ead6b-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ead6b-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="ead6b-148">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="ead6b-148">Fundamentals of Garbage Collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md)
