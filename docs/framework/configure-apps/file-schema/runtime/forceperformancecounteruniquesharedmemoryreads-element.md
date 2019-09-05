---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54bccd134a2f77925e80bfc681770b28c05f77a1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252607"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="c9813-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span><span class="sxs-lookup"><span data-stu-id="c9813-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="c9813-103">Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.</span><span class="sxs-lookup"><span data-stu-id="c9813-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
<span data-ttu-id="c9813-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c9813-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c9813-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c9813-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c9813-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<forcePerformanceCounterUniqueSharedMemoryReads>**</span><span class="sxs-lookup"><span data-stu-id="c9813-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9813-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9813-107">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9813-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9813-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c9813-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9813-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9813-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9813-110">Attributes</span></span>  
  
|<span data-ttu-id="c9813-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c9813-111">Attribute</span></span>|<span data-ttu-id="c9813-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c9813-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c9813-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c9813-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c9813-114">Určuje, zda dokončení PerfCounter. dll používá nastavení registru CategoryOptions k určení, zda mají být načtena data čítače výkonu z sdílené paměti specifické pro kategorii nebo z globální paměti.</span><span class="sxs-lookup"><span data-stu-id="c9813-114">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="c9813-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="c9813-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="c9813-116">Value</span><span class="sxs-lookup"><span data-stu-id="c9813-116">Value</span></span>|<span data-ttu-id="c9813-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c9813-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="c9813-118">Dokončení PerfCounter. dll nepoužívá nastavení registru CategoryOptions, což je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="c9813-118">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="c9813-119">Dokončení PerfCounter. dll používá nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="c9813-119">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9813-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9813-120">Child Elements</span></span>  
 <span data-ttu-id="c9813-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9813-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9813-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9813-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c9813-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9813-123">Element</span></span>|<span data-ttu-id="c9813-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c9813-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="c9813-125">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c9813-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="c9813-126">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c9813-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9813-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9813-127">Remarks</span></span>  
 <span data-ttu-id="c9813-128">Ve verzích .NET Framework před .NET Framework 4 je nahraná verze dokončení PerfCounter. dll odpovídající modulu runtime, který byl načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="c9813-128">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="c9813-129">Pokud má počítač nainstalovanou verzi .NET Framework 1,1 i .NET Framework 2,0, aplikace .NET Framework 1,1 by načetla .NET Framework 1,1 verze souboru dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="c9813-129">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="c9813-130">Počínaje .NET Framework 4 je načtena nejnovější nainstalovaná verze dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="c9813-130">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="c9813-131">To znamená, že aplikace .NET Framework 1,1 načte .NET Framework 4 verzi dokončení PerfCounter. dll, pokud je v počítači nainstalováno .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c9813-131">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="c9813-132">Počínaje .NET Framework 4 při zpracování čítačů výkonu zkontroluje dokončení PerfCounter. dll položku registru CategoryOptions pro každého poskytovatele a určí, jestli se má číst z sdílené paměti specifické pro kategorii nebo globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="c9813-132">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="c9813-133">.NET Framework 1,1 dokončení PerfCounter. dll nepřečte položku registru, protože nemá informace o sdílené paměti specifické pro danou kategorii; vždy se čte z globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="c9813-133">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="c9813-134">Z důvodu zpětné kompatibility .NET Framework 4 dokončení PerfCounter. dll při spuštění v aplikaci .NET Framework 1,1 nekontroluje položku registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="c9813-134">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="c9813-135">Jednoduše používá globální sdílenou paměť, stejně jako .NET Framework 1,1 dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="c9813-135">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="c9813-136">Můžete však dát pokyn .NET Framework 4 dokončení PerfCounter. dll pro kontrolu nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c9813-136">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c9813-137">`<forcePerformanceCounterUniqueSharedMemoryReads>` Povolení prvku nezaručuje, že bude použita sdílená paměť specifická pro danou kategorii.</span><span class="sxs-lookup"><span data-stu-id="c9813-137">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="c9813-138">Nastavení povoleno `true` pouze způsobí, že dokončení PerfCounter. dll odkazuje na nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="c9813-138">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="c9813-139">Výchozím nastavením pro CategoryOptions je použít sdílenou paměť specifickou pro kategorii; CategoryOptions však můžete změnit tak, aby označovala, že by měla být použita globální sdílená paměť.</span><span class="sxs-lookup"><span data-stu-id="c9813-139">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="c9813-140">Klíč registru obsahující nastavení CategoryOptions je HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\< CategoryName \Performance.\></span><span class="sxs-lookup"><span data-stu-id="c9813-140">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="c9813-141">Ve výchozím nastavení je CategoryOptions nastaveno na hodnotu 3, což dává dokončení PerfCounter. dll pokyn, aby používala sdílenou paměť specifickou pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="c9813-141">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="c9813-142">Pokud je CategoryOptions nastavené na 0, dokončení PerfCounter. dll používá globální sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="c9813-142">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="c9813-143">Data instance se znovu použijí pouze v případě, že je název vytvářené instance stejný jako instance, která se právě používá.</span><span class="sxs-lookup"><span data-stu-id="c9813-143">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="c9813-144">Všechny verze budou moci zapisovat do kategorie.</span><span class="sxs-lookup"><span data-stu-id="c9813-144">All versions will be able to write to the category.</span></span> <span data-ttu-id="c9813-145">Pokud je CategoryOptions nastaveno na hodnotu 1, je použita globální sdílená paměť, ale data instance lze znovu použít, pokud má název kategorie stejnou délku jako znovu používané kategorie.</span><span class="sxs-lookup"><span data-stu-id="c9813-145">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="c9813-146">Nastavení 0 a 1 mohou vést k nevrácení paměti a vyplňování paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="c9813-146">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9813-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9813-147">Example</span></span>  
 <span data-ttu-id="c9813-148">Následující příklad ukazuje, jak určit, že dokončení PerfCounter. dll má odkazovat na položku registru CategoryOptions, aby určila, zda má používat sdílenou paměť specifickou pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="c9813-148">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9813-149">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9813-149">See also</span></span>

- [<span data-ttu-id="c9813-150">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="c9813-150">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c9813-151">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c9813-151">Configuration File Schema</span></span>](../index.md)
