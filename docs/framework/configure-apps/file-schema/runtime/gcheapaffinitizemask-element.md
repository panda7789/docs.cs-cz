---
title: Element GCHeapAffinitizeMask
ms.date: 11/08/2019
helpviewer_keywords:
- gcHeapCount element
- <gcHeapCount> element
ms.openlocfilehash: 09d6523fb10692dd3617a3827d5bccf112bc632b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73978380"
---
# <a name="gcheapaffinitizemask-element"></a><span data-ttu-id="9314b-102">\<GCHeapAffinitizeMask> – element</span><span class="sxs-lookup"><span data-stu-id="9314b-102">\<GCHeapAffinitizeMask> element</span></span>

<span data-ttu-id="9314b-103">Definuje spřažení mezi haldami GC a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="9314b-103">Defines the affinity between GC heaps and individual processors.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCHeapAffinitizeMask>

## <a name="syntax"></a><span data-ttu-id="9314b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9314b-104">Syntax</span></span>

```xml
<GCHeapAffinitizeMask
   enabled="nnnn"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="9314b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9314b-105">Attributes and elements</span></span>

<span data-ttu-id="9314b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9314b-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="9314b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="9314b-107">Attributes</span></span>

|<span data-ttu-id="9314b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="9314b-108">Attribute</span></span>|<span data-ttu-id="9314b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9314b-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="9314b-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="9314b-110">Required attribute.</span></span><br /><br /><span data-ttu-id="9314b-111">Určuje spřažení mezi haldami GC a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="9314b-111">Specifies the affinity between GC heaps and individual processors.</span></span> |

#### <a name="enabled-attribute"></a><span data-ttu-id="9314b-112">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="9314b-112">enabled attribute</span></span>

|<span data-ttu-id="9314b-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="9314b-113">Value</span></span>|<span data-ttu-id="9314b-114">Description</span><span class="sxs-lookup"><span data-stu-id="9314b-114">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="9314b-115">Desítková hodnota, která vytvoří bitovou masku definující spřažení mezi haldami GC serveru a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="9314b-115">A decimal value that forms a bitmask defining the affinity between server GC heaps and individual processors.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="9314b-116">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="9314b-116">Child elements</span></span>

<span data-ttu-id="9314b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="9314b-117">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="9314b-118">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="9314b-118">Parent elements</span></span>

|<span data-ttu-id="9314b-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="9314b-119">Element</span></span>|<span data-ttu-id="9314b-120">Description</span><span class="sxs-lookup"><span data-stu-id="9314b-120">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="9314b-121">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9314b-121">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="9314b-122">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="9314b-122">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="9314b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9314b-123">Remarks</span></span>

<span data-ttu-id="9314b-124">Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s jejich vlastním PROCESORem, aby existovala jedna Halda GC, jedno vlákno GC serveru a jeden podproces GC na pozadí pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="9314b-124">By default, server GC threads are hard-affinitized with their respective CPU so that there is one GC heap, one server GC thread, and one background server GC thread for each processor.</span></span> <span data-ttu-id="9314b-125">Počínaje .NET Framework 4.6.2 můžete použít prvek **GCHeapAffinitizeMask** k řízení spřažení mezi haldami GC serveru a procesory, pokud je počet haldy omezený prvkem **GCHeapCount** .</span><span class="sxs-lookup"><span data-stu-id="9314b-125">Starting with .NET Framework 4.6.2, you can use the **GCHeapAffinitizeMask** element to control the affinity between server GC heaps and processors when the number of heaps is limited by the **GCHeapCount** element.</span></span>

<span data-ttu-id="9314b-126">**GCHeapAffinitizeMask** se obvykle používá společně se dvěma dalšími příznaky:</span><span class="sxs-lookup"><span data-stu-id="9314b-126">**GCHeapAffinitizeMask** is typically used along with two other flags:</span></span>

- <span data-ttu-id="9314b-127">[GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda jsou vlákna a haldy GC serveru spřažené s procesory.</span><span class="sxs-lookup"><span data-stu-id="9314b-127">[GCNoAffinitize](gcnoaffinitize-element.md), which controls whether server GC threads/heaps are affinitized with CPUs.</span></span> <span data-ttu-id="9314b-128">`enabled`Atribut elementu [GCNoAffinitize](gcnoaffinitize-element.md) musí být `false` (jeho výchozí hodnota), aby se použilo nastavení **GCHeapAffinitizeMask** .</span><span class="sxs-lookup"><span data-stu-id="9314b-128">The `enabled` attribute of the [GCNoAffinitize](gcnoaffinitize-element.md) element must be `false` (its default value) for the **GCHeapAffinitizeMask** setting to be used.</span></span>

- <span data-ttu-id="9314b-129">[GCHeapCount](gcheapcount-element.md), která omezuje počet hald používaných procesem pro uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="9314b-129">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by the process for server GC.</span></span> <span data-ttu-id="9314b-130">Ve výchozím nastavení je pro každý procesor k dispozici jedna halda.</span><span class="sxs-lookup"><span data-stu-id="9314b-130">By default, there is one heap for each processor.</span></span>

<span data-ttu-id="9314b-131">**nnnn** je Bitová maska vyjádřená jako Desítková hodnota.</span><span class="sxs-lookup"><span data-stu-id="9314b-131">**nnnn** is a bit mask expressed as a decimal value.</span></span> <span data-ttu-id="9314b-132">Bit 0 bajtů 0 představuje procesor 0, bit 1 bajtů 0 představuje procesor 1 atd.</span><span class="sxs-lookup"><span data-stu-id="9314b-132">Bit 0 of byte 0 represents processor 0, bit 1 of byte 0 represents processor 1, and so on.</span></span> <span data-ttu-id="9314b-133">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9314b-133">For example:</span></span>

```xml
<GCHeapAffinitizeMask enabled="1023"/>
```

<span data-ttu-id="9314b-134">Hodnota 1023 je 0x3FF nebo 0011 1111 1111b.</span><span class="sxs-lookup"><span data-stu-id="9314b-134">A value of 1023 is 0x3FF or 0011 1111 1111b.</span></span> <span data-ttu-id="9314b-135">Proces používá 10 procesorů od procesorů 0 do procesoru 9.</span><span class="sxs-lookup"><span data-stu-id="9314b-135">The process uses 10 processors, from processor 0 through processor 9.</span></span>

## <a name="example"></a><span data-ttu-id="9314b-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="9314b-136">Example</span></span>

<span data-ttu-id="9314b-137">Následující příklad označuje, že aplikace používá GC serveru s 10 haldami nebo vlákny.</span><span class="sxs-lookup"><span data-stu-id="9314b-137">The following example indicates that an application uses server GC with 10 heaps/threads.</span></span> <span data-ttu-id="9314b-138">Vzhledem k tomu, že nechcete, aby se tyto haldy překrývaly s haldami z jiných aplikací spuštěných v systému, použijte **GCHeapAffinitizeMask** a určete tak, že by měl proces používat CPU 0 až 9.</span><span class="sxs-lookup"><span data-stu-id="9314b-138">Since you don't want those heaps to overlap with heaps from other applications running on the system, use **GCHeapAffinitizeMask** to specify that the process should use CPUs 0 through 9.</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCHeapAffinitizeMask enabled="1023"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="9314b-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="9314b-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9314b-140">Element GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="9314b-140">GCNoAffinitize element</span></span>](gcnoaffinitize-element.md)
- [<span data-ttu-id="9314b-141">Element GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="9314b-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="9314b-142">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="9314b-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="9314b-143">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="9314b-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="9314b-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="9314b-144">Configuration File Schema</span></span>](../index.md)
