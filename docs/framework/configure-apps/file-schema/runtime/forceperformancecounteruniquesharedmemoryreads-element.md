---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154137"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="2e607-102">\<forcePerformanceCounterUniqueSharedMemoryRe> element</span><span class="sxs-lookup"><span data-stu-id="2e607-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="2e607-103">Určuje, zda program PerfCounter.dll používá nastavení registru CategoryOptions v aplikaci rozhraní .NET Framework verze 1.1 k určení, zda má být načtena data čítače výkonu ze sdílené paměti specifické pro danou kategorii nebo globální paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="2e607-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2e607-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2e607-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2e607-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2e607-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryRe>**</span><span class="sxs-lookup"><span data-stu-id="2e607-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e607-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e607-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e607-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e607-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2e607-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e607-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e607-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e607-110">Attributes</span></span>  
  
|<span data-ttu-id="2e607-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2e607-111">Attribute</span></span>|<span data-ttu-id="2e607-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2e607-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2e607-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2e607-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2e607-114">Označuje, zda služba PerfCounter.dll používá nastavení registru CategoryOptions k určení, zda se mají načíst data čítače výkonu ze sdílené paměti specifické pro danou kategorii nebo globální paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2e607-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="2e607-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="2e607-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2e607-116">Value</span></span>|<span data-ttu-id="2e607-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2e607-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2e607-118">Soubor PerfCounter.dll nepoužívá nastavení registru CategoryOptions Toto je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="2e607-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="2e607-119">Soubor PerfCounter.dll používá nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="2e607-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e607-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e607-120">Child Elements</span></span>  
 <span data-ttu-id="2e607-121">Žádné.</span><span class="sxs-lookup"><span data-stu-id="2e607-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e607-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e607-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2e607-123">Element</span><span class="sxs-lookup"><span data-stu-id="2e607-123">Element</span></span>|<span data-ttu-id="2e607-124">Popis</span><span class="sxs-lookup"><span data-stu-id="2e607-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2e607-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2e607-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2e607-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e607-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e607-127">Remarks</span></span>  
 <span data-ttu-id="2e607-128">Ve verzích rozhraní .NET Framework před rozhraním .NET Framework 4 odpovídala verze souboru PerfCounter.dll, která byla načtena, době runtime načtené v procesu.</span><span class="sxs-lookup"><span data-stu-id="2e607-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="2e607-129">Pokud by byl v počítači nainstalována rozhraní .NET Framework verze 1.1 i rozhraní .NET Framework 2.0, načetla by aplikace rozhraní .NET Framework 1.1 verzi souboru PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="2e607-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="2e607-130">Počínaje rozhraním .NET Framework 4 je načtena nejnovější nainstalovaná verze souboru PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="2e607-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="2e607-131">To znamená, že aplikace rozhraní .NET Framework 1.1 načte verzi souboru PerfCounter.dll v rámci rozhraní .NET Framework 4, pokud je v počítači nainstalována rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2e607-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="2e607-132">Počínaje rozhraním .NET Framework 4 při využívání čítačů výkonu perfCounter.dll zkontroluje položku registru CategoryOptions pro každého zprostředkovatele a určí, zda má číst ze sdílené paměti specifické pro kategorii nebo globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="2e607-133">Rozhraní .NET Framework 1.1 PerfCounter.dll nečte tuto položku registru, protože si není vědoma sdílené paměti specifické pro kategorii; vždy čte z globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="2e607-134">Z důvodu zpětné kompatibility nekontroluje soubor .NET Framework 4 PerfCounter.dll položku registru CategoryOptions při spuštění v aplikaci rozhraní .NET Framework 1.1.</span><span class="sxs-lookup"><span data-stu-id="2e607-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="2e607-135">Jednoduše používá globální sdílenou paměť, stejně jako rozhraní .NET Framework 1.1 PerfCounter.dll.</span><span class="sxs-lookup"><span data-stu-id="2e607-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="2e607-136">Můžete však dát pokyn rozhraní .NET Framework 4 PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` ke kontrole nastavení registru povolením prvku.</span><span class="sxs-lookup"><span data-stu-id="2e607-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e607-137">Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` prvku nezaručuje, že bude použita sdílená paměť specifická pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="2e607-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="2e607-138">Nastavení povoleno `true` pouze způsobí, že soubor PerfCounter.dll odkazuje na nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="2e607-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="2e607-139">Výchozí nastavení pro CategoryOptions je použití sdílené paměti specifické pro kategorii; můžete však změnit CategoryOptions označující, že by měla být použita globální sdílená paměť.</span><span class="sxs-lookup"><span data-stu-id="2e607-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="2e607-140">Klíč registru, který obsahuje nastavení CategoryOptions, je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span><span class="sxs-lookup"><span data-stu-id="2e607-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="2e607-141">Ve výchozím nastavení categoryOptions je nastavena na 3, který pokyn PerfCounter.dll používat kategorii specifické sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="2e607-142">Pokud CategoryOptions je nastavena na 0, PerfCounter.dll používá globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="2e607-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="2e607-143">Data instance budou znovu použita pouze v případě, že název vytvářené instance je shodný s opětovně používanou instancí.</span><span class="sxs-lookup"><span data-stu-id="2e607-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="2e607-144">Všechny verze budou moci zapisovat do kategorie.</span><span class="sxs-lookup"><span data-stu-id="2e607-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="2e607-145">Pokud CategoryOptions je nastavena na 1, globální sdílené paměti se používá, ale data instance lze znovu použít, pokud název kategorie je stejná délka jako kategorie opakovaně.</span><span class="sxs-lookup"><span data-stu-id="2e607-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="2e607-146">Nastavení 0 a 1 může vést k nevracení paměti a vyplnění paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="2e607-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e607-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e607-147">Example</span></span>  
 <span data-ttu-id="2e607-148">Následující příklad ukazuje, jak určit, že PerfCounter.dll by měl odkazovat na položku registru CategoryOptions k určení, zda by měl používat sdílené paměti specifické pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="2e607-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e607-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e607-149">See also</span></span>

- [<span data-ttu-id="2e607-150">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2e607-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2e607-151">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2e607-151">Configuration File Schema</span></span>](../index.md)
