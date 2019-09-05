---
title: Element <gcConcurrent>
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
ms.openlocfilehash: 2b2774c32b4ee3e67772f84d599ecc5dbeb6598b
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252583"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="d14cf-102">\<gcConcurrent – element ></span><span class="sxs-lookup"><span data-stu-id="d14cf-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="d14cf-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="d14cf-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="d14cf-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d14cf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d14cf-105">&nbsp;&nbsp;[ **\<> modulu runtime**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="d14cf-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="d14cf-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent>**</span><span class="sxs-lookup"><span data-stu-id="d14cf-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcConcurrent>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="d14cf-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d14cf-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d14cf-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d14cf-108">Attributes and elements</span></span>

<span data-ttu-id="d14cf-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d14cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d14cf-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="d14cf-110">Attributes</span></span>

|<span data-ttu-id="d14cf-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="d14cf-111">Attribute</span></span>|<span data-ttu-id="d14cf-112">Popis</span><span class="sxs-lookup"><span data-stu-id="d14cf-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="d14cf-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="d14cf-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="d14cf-114">Určuje, zda modul runtime současně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="d14cf-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="d14cf-115">enabled attribute</span></span>

|<span data-ttu-id="d14cf-116">Value</span><span class="sxs-lookup"><span data-stu-id="d14cf-116">Value</span></span>|<span data-ttu-id="d14cf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d14cf-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="d14cf-118">Nespustí souběžný sběr paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="d14cf-119">Souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="d14cf-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="d14cf-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="d14cf-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="d14cf-121">Child elements</span></span>

<span data-ttu-id="d14cf-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="d14cf-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d14cf-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="d14cf-123">Parent elements</span></span>

|<span data-ttu-id="d14cf-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="d14cf-124">Element</span></span>|<span data-ttu-id="d14cf-125">Popis</span><span class="sxs-lookup"><span data-stu-id="d14cf-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="d14cf-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d14cf-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="d14cf-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d14cf-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d14cf-128">Remarks</span></span>

<span data-ttu-id="d14cf-129">Před verzí .NET Framework 4 bylo podporováno souběžné uvolňování paměti pracovní stanice, které provedlo uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="d14cf-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="d14cf-130">V .NET Framework 4 se souběžné uvolňování paměti nahradilo pomocí modulu GC na pozadí, který také provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="d14cf-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="d14cf-131">Počínaje .NET Framework 4,5 se kolekce na pozadí stala k dispozici v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="d14cf-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="d14cf-132">`<gcConcurrent>` Prvek řídí, zda modul runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="d14cf-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="d14cf-133">Zakázání uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="d14cf-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="d14cf-134">Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d14cf-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="d14cf-135">V dokumentaci .NET Framework se používají zaměnitelné a *pozadí* podmínek.</span><span class="sxs-lookup"><span data-stu-id="d14cf-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="d14cf-136">Chcete-li zakázat uvolňování paměti na `<gcConcurrent>` pozadí, použijte element, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="d14cf-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="d14cf-137">Ve výchozím nastavení používá modul runtime souběžné nebo pozadí uvolňování paměti, které je optimalizováno pro latenci.</span><span class="sxs-lookup"><span data-stu-id="d14cf-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="d14cf-138">Pokud vaše aplikace zahrnuje těžkou interakci s uživatelem, nechte souběžné uvolňování paměti povolené, aby se minimalizovala doba pozastavení aplikace, aby se provádělo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="d14cf-139">Pokud nastavíte `enabled` atribut `<gcConcurrent>` prvku na `false`, modul runtime používá nesouběžné uvolňování paměti, které je optimalizováno pro propustnost.</span><span class="sxs-lookup"><span data-stu-id="d14cf-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="d14cf-140">Následující konfigurační soubor zakáže uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d14cf-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="d14cf-141">Pokud je v konfiguračním souboru počítače nastavení,definujevýchozíhodnotuprovšechny.NETFrameworkaplikace.`<gcConcurrentSetting>`</span><span class="sxs-lookup"><span data-stu-id="d14cf-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="d14cf-142">Nastavení konfiguračního souboru počítače přepisuje nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d14cf-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="d14cf-143">Další informace o souběžném uvolňování paměti na pozadí naleznete v části [souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) v článku [Základy uvolňování](../../../../standard/garbage-collection/fundamentals.md) paměti.</span><span class="sxs-lookup"><span data-stu-id="d14cf-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="d14cf-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="d14cf-144">Example</span></span>

<span data-ttu-id="d14cf-145">Následující příklad povoluje souběžné uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="d14cf-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="d14cf-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d14cf-146">See also</span></span>

- [<span data-ttu-id="d14cf-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="d14cf-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d14cf-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="d14cf-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d14cf-149">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="d14cf-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
