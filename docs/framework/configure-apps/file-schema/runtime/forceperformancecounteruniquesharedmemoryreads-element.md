---
title: '&lt;forceperformancecounteruniquesharedmemoryreads –&gt; – Element'
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1f041cbfb4195b2c649c3af4fa061bf63e227df
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754285"
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a><span data-ttu-id="3953f-102">&lt;forceperformancecounteruniquesharedmemoryreads –&gt; – Element</span><span class="sxs-lookup"><span data-stu-id="3953f-102">&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; Element</span></span>
<span data-ttu-id="3953f-103">Určuje, zda PerfCounter.dll používá nastavení registru CategoryOptions v rozhraní .NET Framework verze 1.1 aplikaci a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.</span><span class="sxs-lookup"><span data-stu-id="3953f-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="3953f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="3953f-104">\<configuration></span></span>  
<span data-ttu-id="3953f-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="3953f-105">\<runtime></span></span>  
<span data-ttu-id="3953f-106">\<forceperformancecounteruniquesharedmemoryreads – ></span><span class="sxs-lookup"><span data-stu-id="3953f-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3953f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3953f-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3953f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3953f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3953f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3953f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3953f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="3953f-110">Attributes</span></span>  
  
|<span data-ttu-id="3953f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="3953f-111">Attribute</span></span>|<span data-ttu-id="3953f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="3953f-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="3953f-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="3953f-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="3953f-114">Označuje, zda PerfCounter.dll používá nastavení registru CategoryOptions a určí, jestli se načíst data čítače výkonu z kategorie sdílené paměti nebo globální paměť.</span><span class="sxs-lookup"><span data-stu-id="3953f-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3953f-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="3953f-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="3953f-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="3953f-116">Value</span></span>|<span data-ttu-id="3953f-117">Popis</span><span class="sxs-lookup"><span data-stu-id="3953f-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="3953f-118">PerfCounter.dll CategoryOptions nepoužívá výchozí nastavení je toto nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="3953f-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="3953f-119">PerfCounter.dll pomocí nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="3953f-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3953f-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3953f-120">Child Elements</span></span>  
 <span data-ttu-id="3953f-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="3953f-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3953f-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3953f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="3953f-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="3953f-123">Element</span></span>|<span data-ttu-id="3953f-124">Popis</span><span class="sxs-lookup"><span data-stu-id="3953f-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3953f-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3953f-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3953f-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="3953f-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3953f-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3953f-127">Remarks</span></span>  
 <span data-ttu-id="3953f-128">Ve verzích rozhraní .NET Framework, než [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], verze PerfCounter.dll, která byla načtena odpovídaly modul runtime, která byla načtena v procesu.</span><span class="sxs-lookup"><span data-stu-id="3953f-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="3953f-129">Pokud počítač měl i rozhraní .NET Framework verze 1.1 a [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] nainstalovaná, by aplikace rozhraní .NET Framework 1.1 načtení verze rozhraní .NET Framework 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="3953f-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="3953f-130">Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], je nainstalovaná nejnovější verze PerfCounter.dll načtena.</span><span class="sxs-lookup"><span data-stu-id="3953f-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="3953f-131">To znamená, že se načte aplikaci .NET Framework 1.1 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] verzi PerfCounter.dll pokud [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="3953f-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="3953f-132">Od verze [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], při využívání čítače výkonu, PerfCounter.dll ověří položku registru CategoryOptions pro každého zprostředkovatele k určení, jestli má číst ze sdílené paměti podle kategorií nebo globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="3953f-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="3953f-133">PerfCounter.dll rozhraní .NET Framework 1.1 nepodporuje čtení této položky registru, protože nemá žádné informace o sdílené paměti podle kategorií; vždy čte z globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="3953f-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="3953f-134">Z důvodu zpětné kompatibility [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll nekontroluje položku registru CategoryOptions při spuštění v aplikaci .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="3953f-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="3953f-135">Používá jednoduše globální sdílené paměti, stejně jako PerfCounter.dll rozhraní .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="3953f-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="3953f-136">Ale můžete určit, aby [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll zkontrolovat nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3953f-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3953f-137">Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` element nezaručí, že se použije sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="3953f-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="3953f-138">Povoleným nastavením `true` pouze způsobí, že PerfCounter.dll tak, aby odkazovaly CategoryOptions nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="3953f-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="3953f-139">Výchozí nastavení pro CategoryOptions se má používat sdílené paměti podle kategorií; Můžete však změnit CategoryOptions indikující, že má být použita globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="3953f-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="3953f-140">Klíč registru, který obsahuje nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="3953f-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="3953f-141">Ve výchozím nastavení CategoryOptions je hodnotu 3, která dá pokyn PerfCounter.dll používat sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="3953f-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="3953f-142">Pokud CategoryOptions nastavena na hodnotu 0, používá PerfCounter.dll globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="3953f-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="3953f-143">Instance data bude znovu použita, pouze v případě, že název instance, vytváření je stejný jako instance opakovaně používáno.</span><span class="sxs-lookup"><span data-stu-id="3953f-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="3953f-144">Všechny verze budou moci zapsat do kategorie.</span><span class="sxs-lookup"><span data-stu-id="3953f-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="3953f-145">Pokud CategoryOptions nastavena na hodnotu 1, se používá globální sdílené paměti, ale instance data můžete znovu použít, pokud název kategorie je stejnou délku jako kategorie opakovaně používáno.</span><span class="sxs-lookup"><span data-stu-id="3953f-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="3953f-146">Nastavení hodnoty 0 a 1 může vést k nevracení paměti a naplnění až paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="3953f-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3953f-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="3953f-147">Example</span></span>  
 <span data-ttu-id="3953f-148">Následující příklad ukazuje, jak určit, že PerfCounter.dll by měla odkazovat položku registru CategoryOptions k určení, zda se má použít sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="3953f-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3953f-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="3953f-149">See Also</span></span>  
 [<span data-ttu-id="3953f-150">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="3953f-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3953f-151">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="3953f-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
