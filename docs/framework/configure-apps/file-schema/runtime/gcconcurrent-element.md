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
ms.openlocfilehash: 5957337aa960a0d5f445249b410dbfaddb7b08e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969231"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="12e9e-102">\<element > gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="12e9e-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="12e9e-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="12e9e-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="12e9e-104">[konfigurační >\<](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="12e9e-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="12e9e-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="12e9e-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="12e9e-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent ></span><span class="sxs-lookup"><span data-stu-id="12e9e-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="12e9e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12e9e-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="12e9e-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="12e9e-108">Attributes and elements</span></span>

<span data-ttu-id="12e9e-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="12e9e-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="12e9e-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="12e9e-110">Attributes</span></span>

|<span data-ttu-id="12e9e-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="12e9e-111">Attribute</span></span>|<span data-ttu-id="12e9e-112">Popis</span><span class="sxs-lookup"><span data-stu-id="12e9e-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="12e9e-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="12e9e-113">Required attribute.</span></span><br /><br /><span data-ttu-id="12e9e-114">Určuje, zda modul runtime současně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="12e9e-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="12e9e-115">enabled attribute</span></span>

|<span data-ttu-id="12e9e-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="12e9e-116">Value</span></span>|<span data-ttu-id="12e9e-117">Popis</span><span class="sxs-lookup"><span data-stu-id="12e9e-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="12e9e-118">Nespustí souběžný sběr paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="12e9e-119">Souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="12e9e-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="12e9e-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="12e9e-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="12e9e-121">Child elements</span></span>

<span data-ttu-id="12e9e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="12e9e-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="12e9e-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="12e9e-123">Parent elements</span></span>

|<span data-ttu-id="12e9e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="12e9e-124">Element</span></span>|<span data-ttu-id="12e9e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="12e9e-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="12e9e-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12e9e-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="12e9e-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="12e9e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12e9e-128">Remarks</span></span>

<span data-ttu-id="12e9e-129">Před verzí .NET Framework 4 bylo podporováno souběžné uvolňování paměti pracovní stanice, které provedlo uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="12e9e-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="12e9e-130">V .NET Framework 4 se souběžné uvolňování paměti nahradilo pomocí GC na pozadí, které také provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="12e9e-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="12e9e-131">Počínaje .NET Framework 4,5 se kolekce na pozadí stala k dispozici v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="12e9e-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="12e9e-132">Element **gcConcurrent** řídí, zda modul runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="12e9e-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="12e9e-133">Zakázání uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="12e9e-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="12e9e-134">Počínaje .NET Framework 4 je souběžné uvolňování paměti nahrazeno kolekcí paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="12e9e-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="12e9e-135">V dokumentaci .NET Framework se používají zaměnitelné a *pozadí* podmínek.</span><span class="sxs-lookup"><span data-stu-id="12e9e-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="12e9e-136">Chcete-li zakázat uvolňování paměti na pozadí, použijte element **gcConcurrent** , jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="12e9e-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="12e9e-137">Ve výchozím nastavení používá modul runtime souběžné nebo pozadí uvolňování paměti, které je optimalizováno pro latenci.</span><span class="sxs-lookup"><span data-stu-id="12e9e-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="12e9e-138">Pokud vaše aplikace zahrnuje těžkou interakci s uživatelem, nechte souběžné uvolňování paměti povolené, aby se minimalizovala doba pozastavení aplikace, aby se provádělo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="12e9e-139">Pokud nastavíte atribut `enabled` elementu **gcConcurrent** na `false`, modul runtime používá nesouběžné uvolňování paměti, které je optimalizováno pro propustnost.</span><span class="sxs-lookup"><span data-stu-id="12e9e-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="12e9e-140">Následující konfigurační soubor zakáže uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="12e9e-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="12e9e-141">Pokud je v konfiguračním souboru počítače **NagcConcurrentSettingé** nastavení, definuje se výchozí hodnota pro všechny aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12e9e-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="12e9e-142">Nastavení konfiguračního souboru počítače přepisuje nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="12e9e-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="12e9e-143">Další informace o souběžném a uvolňování paměti na pozadí najdete v částech [souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [uvolňování paměti pracovní stanice na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)a [uvolňování paměti serveru na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) v článku [Základy uvolňování](../../../../standard/garbage-collection/fundamentals.md) paměti.</span><span class="sxs-lookup"><span data-stu-id="12e9e-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="12e9e-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="12e9e-144">Example</span></span>

<span data-ttu-id="12e9e-145">Následující příklad povoluje uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="12e9e-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="12e9e-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12e9e-146">See also</span></span>

- [<span data-ttu-id="12e9e-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="12e9e-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="12e9e-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="12e9e-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="12e9e-149">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="12e9e-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
