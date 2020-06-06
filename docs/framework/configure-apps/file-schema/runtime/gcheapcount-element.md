---
title: Element GCHeapCount
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 3d6cac4185af182758cb82e6bfd9d96ed24869b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74283075"
---
# <a name="gcheapcount-element"></a><span data-ttu-id="b1873-102">\<GCHeapCount> – element</span><span class="sxs-lookup"><span data-stu-id="b1873-102">\<GCHeapCount> element</span></span>

<span data-ttu-id="b1873-103">Určuje počet hald/vláken, které se mají použít pro uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1873-103">Specifies the number of heaps/threads to use for server garbage collection.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapCount>

## <a name="syntax"></a><span data-ttu-id="b1873-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1873-104">Syntax</span></span>

```xml
<GCHeapCount
   enabled="nn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b1873-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1873-105">Attributes and elements</span></span>

<span data-ttu-id="b1873-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1873-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b1873-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1873-107">Attributes</span></span>

|<span data-ttu-id="b1873-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1873-108">Attribute</span></span>|<span data-ttu-id="b1873-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b1873-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b1873-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b1873-110">Required attribute.</span></span><br /><br /><span data-ttu-id="b1873-111">Určuje počet hald, které se mají použít pro uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="b1873-111">Specifies the number of heaps to use for server garbage collection.</span></span> <span data-ttu-id="b1873-112">Skutečný počet hald je minimální počet hald, které zadáte, a počet procesorů, které může váš proces používat.</span><span class="sxs-lookup"><span data-stu-id="b1873-112">The actual number of heaps is the minimum of the number of heaps you specify and the number of processors your process is allowed to use.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="b1873-113">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="b1873-113">enabled attribute</span></span>

|<span data-ttu-id="b1873-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b1873-114">Value</span></span>|<span data-ttu-id="b1873-115">Description</span><span class="sxs-lookup"><span data-stu-id="b1873-115">Description</span></span>|
|-----------|-----------------|
|`nn`|<span data-ttu-id="b1873-116">Počet hald pro použití pro GC serveru.</span><span class="sxs-lookup"><span data-stu-id="b1873-116">The number of heaps to use for server GC.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b1873-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="b1873-117">Child elements</span></span>

<span data-ttu-id="b1873-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1873-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b1873-119">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="b1873-119">Parent elements</span></span>

|<span data-ttu-id="b1873-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1873-120">Element</span></span>|<span data-ttu-id="b1873-121">Description</span><span class="sxs-lookup"><span data-stu-id="b1873-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b1873-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1873-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b1873-123">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b1873-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b1873-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1873-124">Remarks</span></span>

<span data-ttu-id="b1873-125">Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s jejich vlastním PROCESORem, aby existovala jedna Halda GC, jedno vlákno GC serveru a jeden podproces GC na pozadí pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="b1873-125">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="b1873-126">Počínaje .NET Framework 4.6.2 můžete použít prvek **GCHeapCount** k omezení počtu hald používaných vaší aplikací pro uvolňování serveru.</span><span class="sxs-lookup"><span data-stu-id="b1873-126">Starting with .NET Framework 4.6.2, you can use the **GCHeapCount** element to limit the number of heaps used by your application for server GC.</span></span> <span data-ttu-id="b1873-127">Omezení počtu hald používaných pro GC serveru je zvlášť užitečné pro systémy, které spouštějí více instancí serverové aplikace.</span><span class="sxs-lookup"><span data-stu-id="b1873-127">Limiting the number of heaps used for server GC is particularly useful for systems that run multiple instances of a server application.</span></span>

<span data-ttu-id="b1873-128">**GCHeapCount** se obvykle používá společně se dvěma dalšími příznaky:</span><span class="sxs-lookup"><span data-stu-id="b1873-128">**GCHeapCount** is typically used along with two other flags:</span></span>

- <span data-ttu-id="b1873-129">[GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda jsou vlákna a haldy GC serveru spřažené s procesory.</span><span class="sxs-lookup"><span data-stu-id="b1873-129">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span>

- <span data-ttu-id="b1873-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), která řídí spřažení vláken a hald GC s procesory.</span><span class="sxs-lookup"><span data-stu-id="b1873-130">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which controls the affinity of GC threads/heaps with CPUs.</span></span>

<span data-ttu-id="b1873-131">Pokud je nastavená možnost **GCHeapCount** a **GCNoAffinitize** je zakázaná (výchozí nastavení), existuje spřažení mezi vlákny *NN* GC/haldami a prvními procesory *NN* .</span><span class="sxs-lookup"><span data-stu-id="b1873-131">If **GCHeapCount** is set and **GCNoAffinitize** is disabled (its default setting), there is an affinity between the *nn* GC threads/heaps and the first *nn* processors.</span></span> <span data-ttu-id="b1873-132">Pomocí elementu **GCHeapAffinitizeMask** můžete určit, které procesory jsou používány haldami GC serveru procesu.</span><span class="sxs-lookup"><span data-stu-id="b1873-132">You can use the **GCHeapAffinitizeMask** element to specify which processors are used by the process's server GC heaps.</span></span> <span data-ttu-id="b1873-133">V opačném případě, pokud je v systému spuštěno více procesů serveru, jejich využití procesoru se překrývá.</span><span class="sxs-lookup"><span data-stu-id="b1873-133">Otherwise, if multiple server processes are running on a system, their processor usage will overlap.</span></span>

<span data-ttu-id="b1873-134">Pokud je nastavená možnost **GCHeapCount** a je povolená možnost **GCNoAffinitize** , uvolňování paměti omezuje počet PROCESORů používaných pro uvolňování serveru, ale nespřažení haldy a procesory GC.</span><span class="sxs-lookup"><span data-stu-id="b1873-134">If **GCHeapCount** is set and **GCNoAffinitize** is enabled, the garbage collector limits the number of processors used for server GC but does not affinitize GC heaps and processors.</span></span>

## <a name="example"></a><span data-ttu-id="b1873-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1873-135">Example</span></span>

<span data-ttu-id="b1873-136">Následující příklad označuje, že aplikace používá GC serveru s 10 haldami nebo vlákny.</span><span class="sxs-lookup"><span data-stu-id="b1873-136">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="b1873-137">Vzhledem k tomu, že nechcete, aby se tyto haldy překrývaly s haldami z jiných aplikací spuštěných v systému, použijte **GCHeapAffinitizeMask** a určete tak, že by měl proces používat procesory 0 až 9.</span><span class="sxs-lookup"><span data-stu-id="b1873-137">Since you don't want those heaps to overlap with heaps from other applications running on the system, you use the **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

<span data-ttu-id="b1873-138">Následující příklad nespřaženíuje vlákna uvolňování paměti serveru a omezuje počet hald a vláken GC na 10.</span><span class="sxs-lookup"><span data-stu-id="b1873-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b1873-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1873-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b1873-140">Element GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="b1873-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="b1873-141">Element GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="b1873-141">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="b1873-142">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="b1873-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="b1873-143">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="b1873-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b1873-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b1873-144">Configuration File Schema</span></span>](../index.md)
