---
title: Element gcConcurrent
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
ms.openlocfilehash: 249518ae7477d284d50f9010757db83b7752c657
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102915"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="734f3-102">\<gcConcurrent> – element</span><span class="sxs-lookup"><span data-stu-id="734f3-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="734f3-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="734f3-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent>

## <a name="syntax"></a><span data-ttu-id="734f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="734f3-104">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="734f3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="734f3-105">Attributes and elements</span></span>

<span data-ttu-id="734f3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="734f3-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="734f3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="734f3-107">Attributes</span></span>

|<span data-ttu-id="734f3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="734f3-108">Attribute</span></span>|<span data-ttu-id="734f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="734f3-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="734f3-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="734f3-110">Required attribute.</span></span><br /><br /><span data-ttu-id="734f3-111">Určuje, zda modul runtime současně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="734f3-111">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="734f3-112">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="734f3-112">enabled attribute</span></span>

|<span data-ttu-id="734f3-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="734f3-113">Value</span></span>|<span data-ttu-id="734f3-114">Description</span><span class="sxs-lookup"><span data-stu-id="734f3-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="734f3-115">Nespustí souběžný sběr paměti.</span><span class="sxs-lookup"><span data-stu-id="734f3-115">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="734f3-116">Souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="734f3-116">Runs garbage collection concurrently.</span></span> <span data-ttu-id="734f3-117">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="734f3-117">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="734f3-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="734f3-118">Child elements</span></span>

<span data-ttu-id="734f3-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="734f3-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="734f3-120">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="734f3-120">Parent elements</span></span>

|<span data-ttu-id="734f3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="734f3-121">Element</span></span>|<span data-ttu-id="734f3-122">Description</span><span class="sxs-lookup"><span data-stu-id="734f3-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="734f3-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="734f3-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="734f3-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="734f3-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="734f3-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="734f3-125">Remarks</span></span>

<span data-ttu-id="734f3-126">Před verzí .NET Framework 4 bylo podporováno souběžné uvolňování paměti pracovní stanice, které provedlo uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="734f3-126">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="734f3-127">V .NET Framework 4 se souběžné uvolňování paměti nahradilo pomocí GC na pozadí, které také provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="734f3-127">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="734f3-128">Počínaje .NET Framework 4,5 se kolekce na pozadí stala k dispozici v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="734f3-128">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="734f3-129">Element **gcConcurrent** řídí, zda modul runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="734f3-129">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="734f3-130">Zakázání uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="734f3-130">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="734f3-131">Počínaje .NET Framework 4 je souběžné uvolňování paměti nahrazeno kolekcí paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="734f3-131">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="734f3-132">V dokumentaci *concurrent* .NET Framework se používají zaměnitelné a *pozadí* podmínek.</span><span class="sxs-lookup"><span data-stu-id="734f3-132">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="734f3-133">Chcete-li zakázat uvolňování paměti na pozadí, použijte element **gcConcurrent** , jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="734f3-133">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="734f3-134">Ve výchozím nastavení používá modul runtime souběžné nebo pozadí uvolňování paměti, které je optimalizováno pro latenci.</span><span class="sxs-lookup"><span data-stu-id="734f3-134">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="734f3-135">Pokud vaše aplikace zahrnuje těžkou interakci s uživatelem, nechte souběžné uvolňování paměti povolené, aby se minimalizovala doba pozastavení aplikace, aby se provádělo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="734f3-135">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="734f3-136">Pokud nastavíte `enabled` atribut prvku **gcConcurrent** na `false` , modul runtime používá nesouběžné uvolňování paměti, které je optimalizováno pro propustnost.</span><span class="sxs-lookup"><span data-stu-id="734f3-136">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="734f3-137">Následující konfigurační soubor zakáže uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="734f3-137">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="734f3-138">Pokud je v konfiguračním souboru počítače **NagcConcurrentSettingé** nastavení, definuje se výchozí hodnota pro všechny aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="734f3-138">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="734f3-139">Nastavení konfiguračního souboru počítače přepisuje nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="734f3-139">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="734f3-140">Další informace o souběžném uvolňování paměti na pozadí naleznete v tématu [kolekce paměti na pozadí](../../../../standard/garbage-collection/background-gc.md).</span><span class="sxs-lookup"><span data-stu-id="734f3-140">For more information on concurrent and background garbage collection, see [Background garbage collection](../../../../standard/garbage-collection/background-gc.md).</span></span>

## <a name="example"></a><span data-ttu-id="734f3-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="734f3-141">Example</span></span>

<span data-ttu-id="734f3-142">Následující příklad povoluje uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="734f3-142">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="734f3-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="734f3-143">See also</span></span>

- [<span data-ttu-id="734f3-144">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="734f3-144">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="734f3-145">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="734f3-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="734f3-146">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="734f3-146">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
