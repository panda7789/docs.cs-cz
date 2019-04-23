---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d4a205f643c844b2fe77d3aa5211b4bc1f322fd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186963"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="fba97-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="fba97-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="fba97-103">Určuje, jestli má PerfCounter.dll CategoryOptions nastavení registru v rozhraní .NET Framework verze 1.1 aplikace k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
 <span data-ttu-id="fba97-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="fba97-104">\<configuration></span></span>  
<span data-ttu-id="fba97-105">\<modul runtime ></span><span class="sxs-lookup"><span data-stu-id="fba97-105">\<runtime></span></span>  
<span data-ttu-id="fba97-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="fba97-106">\<forcePerformanceCounterUniqueSharedMemoryReads></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba97-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fba97-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fba97-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fba97-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fba97-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fba97-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fba97-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="fba97-110">Attributes</span></span>  
  
|<span data-ttu-id="fba97-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="fba97-111">Attribute</span></span>|<span data-ttu-id="fba97-112">Popis</span><span class="sxs-lookup"><span data-stu-id="fba97-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fba97-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="fba97-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="fba97-114">Určuje, zda PerfCounter.dll nastavení registru CategoryOptions používá k určení, jestli se má načíst data čítače výkonu ze sdílené paměti podle kategorií nebo globální paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fba97-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="fba97-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="fba97-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="fba97-116">Value</span></span>|<span data-ttu-id="fba97-117">Popis</span><span class="sxs-lookup"><span data-stu-id="fba97-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="fba97-118">PerfCounter.dll CategoryOptions nepoužívá výchozí nastavení je toto nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="fba97-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="fba97-119">PerfCounter.dll pomocí nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="fba97-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fba97-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fba97-120">Child Elements</span></span>  
 <span data-ttu-id="fba97-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="fba97-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fba97-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fba97-122">Parent Elements</span></span>  
  
|<span data-ttu-id="fba97-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="fba97-123">Element</span></span>|<span data-ttu-id="fba97-124">Popis</span><span class="sxs-lookup"><span data-stu-id="fba97-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fba97-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fba97-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fba97-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fba97-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fba97-127">Remarks</span></span>  
 <span data-ttu-id="fba97-128">Ve verzích rozhraní .NET Framework před [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], odpovídaly verzi PerfCounter.dll, který byl načten modul runtime, který byl načten v procesu.</span><span class="sxs-lookup"><span data-stu-id="fba97-128">In versions of the .NET Framework before the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="fba97-129">Pokud počítač měl i rozhraní .NET Framework verze 1.1 a [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] nainstalované, by aplikace rozhraní .NET Framework 1.1 načtení verze rozhraní .NET Framework 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="fba97-129">If a computer had both the .NET Framework version 1.1 and the [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="fba97-130">Počínaje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], je nainstalovaná nejnovější verze PerfCounter.dll načten.</span><span class="sxs-lookup"><span data-stu-id="fba97-130">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="fba97-131">To znamená, že se načte aplikace rozhraní .NET Framework 1.1 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] verzi PerfCounter.dll pokud [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] je nainstalován v počítači.</span><span class="sxs-lookup"><span data-stu-id="fba97-131">This means that a .NET Framework 1.1 application will load the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] version of PerfCounter.dll if the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] is installed on the computer.</span></span>  
  
 <span data-ttu-id="fba97-132">Počínaje [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], při využívání čítače výkonu, PerfCounter.dll kontroluje CategoryOptions položka registru pro každého zprostředkovatele k určení, zda by měl číst ze sdílené paměti podle kategorií nebo globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-132">Starting with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="fba97-133">Rozhraní .NET Framework 1.1 PerfCounter.dll nenačítá této položky registru, protože nebude vědět o sdílené paměti podle kategorií. vždy čte z globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="fba97-134">Z důvodu zpětné kompatibility [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll nekontroluje položku registru CategoryOptions při spuštění aplikace rozhraní .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="fba97-134">For backward compatibility, the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="fba97-135">Jednoduše používá globální sdílené paměti, stejně jako PerfCounter.dll 1.1 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fba97-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="fba97-136">Ale můžete dát pokyn [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll zkontrolovat nastavení registru tím, že `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fba97-136">However, you can instruct the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fba97-137">Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` element nezaručuje, že se použije sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="fba97-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="fba97-138">Nastavení povolit, aby `true` pouze způsobí, že PerfCounter.dll odkazovat CategoryOptions nastavení registru.</span><span class="sxs-lookup"><span data-stu-id="fba97-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="fba97-139">Výchozí nastavení pro CategoryOptions je použití sdílené paměti podle kategorií. Můžete však změnit CategoryOptions k označení, že má být použit globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="fba97-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="fba97-140">Klíč registru, který obsahuje nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="fba97-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="fba97-141">Ve výchozím nastavení CategoryOptions nastavená na 3, který dává pokyn PerfCounter.dll použití sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="fba97-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="fba97-142">Pokud CategoryOptions je nastavena na hodnotu 0, PerfCounter.dll používá globální sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="fba97-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="fba97-143">Instance data bude znovu použita, pouze v případě, že je název instance vytváří je stejný jako instance používána znovu.</span><span class="sxs-lookup"><span data-stu-id="fba97-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="fba97-144">Všechny verze bude moci zapisovat do kategorie.</span><span class="sxs-lookup"><span data-stu-id="fba97-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="fba97-145">Pokud CategoryOptions je nastavená na 1, se používá globální sdílenou paměť, ale instance data můžete opětovně název kategorie je stejnou délku jako kategorie používána znovu.</span><span class="sxs-lookup"><span data-stu-id="fba97-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="fba97-146">Nastavení 0 a 1 může vést k nevracení paměti a naplnění nahoru paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="fba97-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fba97-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="fba97-147">Example</span></span>  
 <span data-ttu-id="fba97-148">Následující příklad ukazuje, jak určit, že by měly odkazovat PerfCounter.dll položku registru CategoryOptions zjistěte, zda by měl použít sdílené paměti podle kategorií.</span><span class="sxs-lookup"><span data-stu-id="fba97-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fba97-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fba97-149">See also</span></span>

- [<span data-ttu-id="fba97-150">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="fba97-150">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="fba97-151">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="fba97-151">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
