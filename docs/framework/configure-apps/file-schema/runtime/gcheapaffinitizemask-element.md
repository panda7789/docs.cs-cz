---
title: Element GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978380"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="5c529-102">\<element > GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="5c529-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="5c529-103">Definuje spřažení mezi haldami GC a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="5c529-103">Defines the affinity between GC heaps and individual processors.</span></span>

<span data-ttu-id="5c529-104">Konfigurace \<> </span><span class="sxs-lookup"><span data-stu-id="5c529-104">\<configuration></span></span>\
<span data-ttu-id="5c529-105">&nbsp;&nbsp;\<runtime > </span><span class="sxs-lookup"><span data-stu-id="5c529-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="5c529-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask ></span><span class="sxs-lookup"><span data-stu-id="5c529-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask></span></span>

## <a name="syntax"></a><span data-ttu-id="5c529-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c529-107">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c529-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5c529-108">Attributes and elements</span></span>

<span data-ttu-id="5c529-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5c529-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c529-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c529-110">Attributes</span></span>

|<span data-ttu-id="5c529-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5c529-111">Attribute</span></span>|<span data-ttu-id="5c529-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5c529-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="5c529-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="5c529-113">Required attribute.</span></span><br /><br /><span data-ttu-id="5c529-114">Určuje spřažení mezi haldami GC a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="5c529-114">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="5c529-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="5c529-115">enabled attribute</span></span>

|<span data-ttu-id="5c529-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="5c529-116">Value</span></span>|<span data-ttu-id="5c529-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5c529-117">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="5c529-118">Desítková hodnota, která vytvoří bitovou masku definující spřažení mezi haldami GC serveru a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="5c529-118">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="5c529-119">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="5c529-119">Child elements</span></span>

<span data-ttu-id="5c529-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c529-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5c529-121">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="5c529-121">Parent elements</span></span>

|<span data-ttu-id="5c529-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="5c529-122">Element</span></span>|<span data-ttu-id="5c529-123">Popis</span><span class="sxs-lookup"><span data-stu-id="5c529-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="5c529-124">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c529-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="5c529-125">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="5c529-125">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c529-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c529-126">Remarks</span></span>

<span data-ttu-id="5c529-127">Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s jejich vlastním PROCESORem, aby existovala jedna Halda GC, jedno vlákno GC serveru a jeden podproces GC na pozadí pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="5c529-127">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="5c529-128">Počínaje .NET Framework 4.6.2 můžete použít prvek **GCHeapAffinitizeMask** k řízení spřažení mezi haldami GC serveru a procesory, pokud je počet haldy omezený prvkem **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="5c529-128">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="5c529-129">**GCHeapAffinitizeMask** se obvykle používá společně se dvěma dalšími příznaky:</span><span class="sxs-lookup"><span data-stu-id="5c529-129">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="5c529-130">[GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda jsou vlákna a haldy GC serveru spřažené s procesory.</span><span class="sxs-lookup"><span data-stu-id="5c529-130">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="5c529-131">Atribut `enabled` elementu [GCNoAffinitize](gcnoaffinitize-element.md) musí být `false` (jeho výchozí hodnota) pro použití nastavení **GCHeapAffinitizeMask** .</span><span class="sxs-lookup"><span data-stu-id="5c529-131">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="5c529-132">[GCHeapCount](gcheapcount-element.md), která omezuje počet hald používaných procesem pro uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="5c529-132">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="5c529-133">Ve výchozím nastavení je pro každý procesor k dispozici jedna halda.</span><span class="sxs-lookup"><span data-stu-id="5c529-133">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="5c529-134">**nnnn** je Bitová maska vyjádřená jako Desítková hodnota.</span><span class="sxs-lookup"><span data-stu-id="5c529-134">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="5c529-135">Bit 0 bajtů 0 představuje procesor 0, bit 1 bajtů 0 představuje procesor 1 atd.</span><span class="sxs-lookup"><span data-stu-id="5c529-135">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="5c529-136">Příklad:</span><span class="sxs-lookup"><span data-stu-id="5c529-136">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="5c529-137">Hodnota 1023 je 0x3FF nebo 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="5c529-137">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="5c529-138">Proces používá 10 procesorů od procesorů 0 do procesoru 9.</span><span class="sxs-lookup"><span data-stu-id="5c529-138">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="5c529-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c529-139">Example</span></span>

<span data-ttu-id="5c529-140">Následující příklad označuje, že aplikace používá GC serveru s 10 haldami nebo vlákny.</span><span class="sxs-lookup"><span data-stu-id="5c529-140">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="5c529-141">Vzhledem k tomu, že nechcete, aby se tyto haldy překrývaly s haldami z jiných aplikací spuštěných v systému, použijte **GCHeapAffinitizeMask** a určete tak, že by měl proces používat CPU 0 až 9.</span><span class="sxs-lookup"><span data-stu-id="5c529-141">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="5c529-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c529-142">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5c529-143">Element GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="5c529-143">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="5c529-144">Element GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="5c529-144">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="5c529-145">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="5c529-145">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="5c529-146">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="5c529-146">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="5c529-147">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="5c529-147">Configuration File Schema</span></span>](../index.md)
