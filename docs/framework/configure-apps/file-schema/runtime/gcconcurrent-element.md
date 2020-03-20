---
title: gcConcurrent Element
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400041"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="6c283-102">\<gcConcurrent> element</span><span class="sxs-lookup"><span data-stu-id="6c283-102">\<gcConcurrent> element</span></span>

<span data-ttu-id="6c283-103">Určuje, zda soubor RUNTIME společného jazyka spustí uvolňování paměti v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="6c283-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="6c283-104">[\<>konfigurace](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c283-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="6c283-105">&nbsp;&nbsp;[\<>za běhu](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c283-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="6c283-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span><span class="sxs-lookup"><span data-stu-id="6c283-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcConcurrent></span></span>

## <a name="syntax"></a><span data-ttu-id="6c283-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c283-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6c283-108">Atributy a prvky</span><span class="sxs-lookup"><span data-stu-id="6c283-108">Attributes and elements</span></span>

<span data-ttu-id="6c283-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6c283-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="6c283-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="6c283-110">Attributes</span></span>

|<span data-ttu-id="6c283-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="6c283-111">Attribute</span></span>|<span data-ttu-id="6c283-112">Popis</span><span class="sxs-lookup"><span data-stu-id="6c283-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="6c283-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="6c283-113">Required attribute.</span></span><br /><br /><span data-ttu-id="6c283-114">Určuje, zda běhový čas spouští souběžné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6c283-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="6c283-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="6c283-115">enabled attribute</span></span>

|<span data-ttu-id="6c283-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="6c283-116">Value</span></span>|<span data-ttu-id="6c283-117">Popis</span><span class="sxs-lookup"><span data-stu-id="6c283-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="6c283-118">Nespustí uvolňování paměti současně.</span><span class="sxs-lookup"><span data-stu-id="6c283-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="6c283-119">Souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6c283-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="6c283-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="6c283-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="6c283-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="6c283-121">Child elements</span></span>

<span data-ttu-id="6c283-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="6c283-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="6c283-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="6c283-123">Parent elements</span></span>

|<span data-ttu-id="6c283-124">Element</span><span class="sxs-lookup"><span data-stu-id="6c283-124">Element</span></span>|<span data-ttu-id="6c283-125">Popis</span><span class="sxs-lookup"><span data-stu-id="6c283-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="6c283-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c283-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="6c283-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="6c283-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6c283-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c283-128">Remarks</span></span>

<span data-ttu-id="6c283-129">Před rozhraním .NET Framework 4 uvolňování paměti pracovní stanice podporovalo souběžné uvolňování paměti, které provedlo uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="6c283-129">Prior to .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="6c283-130">V rozhraní .NET Framework 4 bylo souběžné uvolňování paměti nahrazeno gc na pozadí, který také provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="6c283-130">In .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="6c283-131">Počínaje rozhraním .NET Framework 4.5 je kolekce na pozadí dostupná v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="6c283-131">Starting with .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="6c283-132">Prvek **gcConcurrent** určuje, zda runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici, nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="6c283-132">The **gcConcurrent** element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="6c283-133">Zakázání uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="6c283-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="6c283-134">Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6c283-134">Starting with .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="6c283-135">Termíny *souběžné* a *pozadí* se používají zaměnitelně v dokumentaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c283-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="6c283-136">Chcete-li zakázat uvolňování paměti na pozadí, použijte **gcConcurrent** element, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="6c283-136">To disable background garbage collection, use the **gcConcurrent** element, as discussed in this article.</span></span>

<span data-ttu-id="6c283-137">Ve výchozím nastavení používá runtime souběžné nebo pozadí uvolňování paměti, který je optimalizován pro latenci.</span><span class="sxs-lookup"><span data-stu-id="6c283-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="6c283-138">Pokud vaše aplikace zahrnuje náročnou interakci uživatele, ponechte souběžné uvolňování paměti povoleno minimalizovat dobu pozastavení aplikace k provedení uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6c283-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="6c283-139">Pokud nastavíte `enabled` atribut **gcConcurrent** `false`element , runtime používá non-souběžné uvolňování paměti, který je optimalizován pro propustnost.</span><span class="sxs-lookup"><span data-stu-id="6c283-139">If you set the `enabled` attribute of the **gcConcurrent** element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span>

<span data-ttu-id="6c283-140">Následující konfigurační soubor zakáže uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="6c283-140">The following configuration file disables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="6c283-141">Pokud je v konfiguračním souboru počítače nastaveno **gcConcurrentSetting,** definuje výchozí hodnotu pro všechny aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6c283-141">If there's a **gcConcurrentSetting** setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="6c283-142">Nastavení konfiguračního souboru počítače přepíše nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="6c283-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

<span data-ttu-id="6c283-143">Další informace o souběžné a pozadí uvolňování paměti naleznete [v části Souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), uvolňování paměti pracovní stanice na [pozadí](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection)a uvolňování paměti serveru [na pozadí](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) v článku [Základy uvolňování paměti.](../../../../standard/garbage-collection/fundamentals.md)</span><span class="sxs-lookup"><span data-stu-id="6c283-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection), [Background workstation garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-workstation-garbage-collection), and [Background server garbage collection](../../../../standard/garbage-collection/fundamentals.md#background-server-garbage-collection) sections in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="6c283-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c283-144">Example</span></span>

<span data-ttu-id="6c283-145">Následující příklad umožňuje uvolňování paměti na pozadí:</span><span class="sxs-lookup"><span data-stu-id="6c283-145">The following example enables background garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="6c283-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c283-146">See also</span></span>

- [<span data-ttu-id="6c283-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="6c283-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6c283-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="6c283-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6c283-149">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="6c283-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
