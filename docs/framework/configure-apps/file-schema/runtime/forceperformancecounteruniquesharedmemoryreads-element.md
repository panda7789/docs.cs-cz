---
title: Element <forcePerformanceCounterUniqueSharedMemoryReads>
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154137"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a><span data-ttu-id="0ff9c-102">Element \<forcePerformanceCounterUniqueSharedMemoryReads></span><span class="sxs-lookup"><span data-stu-id="0ff9c-102">\<forcePerformanceCounterUniqueSharedMemoryReads> Element</span></span>
<span data-ttu-id="0ff9c-103">Určuje, jestli dokončení PerfCounter. dll používá nastavení registru CategoryOptions v aplikaci .NET Framework verze 1,1 k určení toho, jestli se mají načíst data čítače výkonu z sdílené paměti nebo globální paměti specifické pro danou kategorii.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-103">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a><span data-ttu-id="0ff9c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ff9c-104">Syntax</span></span>  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ff9c-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ff9c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0ff9c-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ff9c-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ff9c-107">Attributes</span></span>  
  
|<span data-ttu-id="0ff9c-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="0ff9c-108">Attribute</span></span>|<span data-ttu-id="0ff9c-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0ff9c-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0ff9c-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="0ff9c-111">Určuje, zda dokončení PerfCounter. dll používá nastavení registru CategoryOptions k určení, zda mají být načtena data čítače výkonu z sdílené paměti specifické pro kategorii nebo z globální paměti.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-111">Indicates whether PerfCounter.dll uses the CategoryOptions registry setting to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="0ff9c-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="0ff9c-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="0ff9c-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0ff9c-113">Value</span></span>|<span data-ttu-id="0ff9c-114">Description</span><span class="sxs-lookup"><span data-stu-id="0ff9c-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0ff9c-115">Dokončení PerfCounter. dll nepoužívá nastavení registru CategoryOptions, což je výchozí nastavení.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-115">PerfCounter.dll does not use the CategoryOptions registry setting This is the default.</span></span>|  
|`true`|<span data-ttu-id="0ff9c-116">Dokončení PerfCounter. dll používá nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-116">PerfCounter.dll does use the CategoryOptions registry setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ff9c-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0ff9c-117">Child Elements</span></span>  
 <span data-ttu-id="0ff9c-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ff9c-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ff9c-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0ff9c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0ff9c-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="0ff9c-120">Element</span></span>|<span data-ttu-id="0ff9c-121">Description</span><span class="sxs-lookup"><span data-stu-id="0ff9c-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0ff9c-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="0ff9c-123">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-123">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ff9c-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ff9c-124">Remarks</span></span>  
 <span data-ttu-id="0ff9c-125">Ve verzích .NET Framework před .NET Framework 4 je nahraná verze dokončení PerfCounter. dll odpovídající modulu runtime, který byl načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-125">In versions of the .NET Framework before the .NET Framework 4, the version of PerfCounter.dll that was loaded corresponded to the runtime that was loaded in the process.</span></span> <span data-ttu-id="0ff9c-126">Pokud má počítač nainstalovanou verzi .NET Framework 1,1 i .NET Framework 2,0, aplikace .NET Framework 1,1 by načetla .NET Framework 1,1 verze souboru dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-126">If a computer had both the .NET Framework version 1.1 and the .NET Framework 2.0 installed, a .NET Framework 1.1 application would load the .NET Framework 1.1 version of PerfCounter.dll.</span></span> <span data-ttu-id="0ff9c-127">Počínaje .NET Framework 4 je načtena nejnovější nainstalovaná verze dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-127">Starting with the .NET Framework 4, the newest installed version of PerfCounter.dll is loaded.</span></span> <span data-ttu-id="0ff9c-128">To znamená, že aplikace .NET Framework 1,1 načte .NET Framework 4 verzi dokončení PerfCounter. dll, pokud je v počítači nainstalováno .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-128">This means that a .NET Framework 1.1 application will load the .NET Framework 4 version of PerfCounter.dll if the .NET Framework 4 is installed on the computer.</span></span>  
  
 <span data-ttu-id="0ff9c-129">Počínaje .NET Framework 4 při zpracování čítačů výkonu zkontroluje dokončení PerfCounter. dll položku registru CategoryOptions pro každého poskytovatele a určí, jestli se má číst z sdílené paměti specifické pro kategorii nebo globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-129">Starting with the .NET Framework 4, when consuming performance counters, PerfCounter.dll checks the CategoryOptions registry entry for each provider to determine whether it should read from category-specific shared memory or global shared memory.</span></span> <span data-ttu-id="0ff9c-130">.NET Framework 1,1 dokončení PerfCounter. dll nepřečte položku registru, protože nemá informace o sdílené paměti specifické pro danou kategorii; vždy se čte z globální sdílené paměti.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-130">The .NET Framework 1.1 PerfCounter.dll does not read that registry entry, because it is not aware of category-specific shared memory; it always reads from global shared memory.</span></span>  
  
 <span data-ttu-id="0ff9c-131">Z důvodu zpětné kompatibility .NET Framework 4 dokončení PerfCounter. dll při spuštění v aplikaci .NET Framework 1,1 nekontroluje položku registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-131">For backward compatibility, the .NET Framework 4 PerfCounter.dll does not check the CategoryOptions registry entry when running in a .NET Framework 1.1 application.</span></span> <span data-ttu-id="0ff9c-132">Jednoduše používá globální sdílenou paměť, stejně jako .NET Framework 1,1 dokončení PerfCounter. dll.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-132">It simply uses global shared memory, just like the .NET Framework 1.1 PerfCounter.dll.</span></span> <span data-ttu-id="0ff9c-133">Můžete však dát pokyn .NET Framework 4 dokončení PerfCounter. dll pro kontrolu nastavení registru povolením `<forcePerformanceCounterUniqueSharedMemoryReads>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-133">However, you can instruct the .NET Framework 4 PerfCounter.dll to check the registry setting by enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ff9c-134">Povolení `<forcePerformanceCounterUniqueSharedMemoryReads>` prvku nezaručuje, že bude použita sdílená paměť specifická pro danou kategorii.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-134">Enabling the `<forcePerformanceCounterUniqueSharedMemoryReads>` element does not guarantee that category-specific shared memory will be used.</span></span> <span data-ttu-id="0ff9c-135">Nastavení povoleno `true` pouze způsobí, že dokončení PerfCounter. dll odkazuje na nastavení registru CategoryOptions.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-135">Setting enabled to `true` only causes PerfCounter.dll to reference the CategoryOptions registry setting.</span></span> <span data-ttu-id="0ff9c-136">Výchozím nastavením pro CategoryOptions je použít sdílenou paměť specifickou pro kategorii; CategoryOptions však můžete změnit tak, aby označovala, že by měla být použita globální sdílená paměť.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-136">The default setting for CategoryOptions is to use category-specific shared memory; however, you can change CategoryOptions to indicate that global shared memory should be used.</span></span>  
  
 <span data-ttu-id="0ff9c-137">Klíč registru, který obsahuje nastavení CategoryOptions, je HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<NázevKategorie \> \Performance.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-137">The registry key that contains the CategoryOptions setting is HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\<categoryName\>\Performance.</span></span> <span data-ttu-id="0ff9c-138">Ve výchozím nastavení je CategoryOptions nastaveno na hodnotu 3, což dává dokončení PerfCounter. dll pokyn, aby používala sdílenou paměť specifickou pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-138">By default, CategoryOptions is set to 3, which instructs PerfCounter.dll to use category-specific shared memory.</span></span> <span data-ttu-id="0ff9c-139">Pokud je CategoryOptions nastavené na 0, dokončení PerfCounter. dll používá globální sdílenou paměť.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-139">If CategoryOptions is set to 0, PerfCounter.dll uses global shared memory.</span></span> <span data-ttu-id="0ff9c-140">Data instance se znovu použijí pouze v případě, že je název vytvářené instance stejný jako instance, která se právě používá.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-140">Instance data will be reused only if the name of the instance being created is identical to the instance being reused.</span></span> <span data-ttu-id="0ff9c-141">Všechny verze budou moci zapisovat do kategorie.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-141">All versions will be able to write to the category.</span></span> <span data-ttu-id="0ff9c-142">Pokud je CategoryOptions nastaveno na hodnotu 1, je použita globální sdílená paměť, ale data instance lze znovu použít, pokud má název kategorie stejnou délku jako znovu používané kategorie.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-142">If CategoryOptions is set to 1, global shared memory is used, but instance data can be reused if the category name is the same length as the category being reused.</span></span>  
  
 <span data-ttu-id="0ff9c-143">Nastavení 0 a 1 mohou vést k nevrácení paměti a vyplňování paměti čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-143">The settings 0 and 1 can lead to memory leaks and the filling up of performance counter memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ff9c-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ff9c-144">Example</span></span>  
 <span data-ttu-id="0ff9c-145">Následující příklad ukazuje, jak určit, že dokončení PerfCounter. dll má odkazovat na položku registru CategoryOptions, aby určila, zda má používat sdílenou paměť specifickou pro kategorii.</span><span class="sxs-lookup"><span data-stu-id="0ff9c-145">The following example shows how to specify that PerfCounter.dll should reference the CategoryOptions registry entry to determine whether it should use category-specific shared memory.</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ff9c-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ff9c-146">See also</span></span>

- [<span data-ttu-id="0ff9c-147">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="0ff9c-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0ff9c-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0ff9c-148">Configuration File Schema</span></span>](../index.md)
