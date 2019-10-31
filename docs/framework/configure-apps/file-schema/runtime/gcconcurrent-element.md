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
ms.openlocfilehash: 4897462e20b193496c44d26923d0d0e2a13f7dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116813"
---
# <a name="gcconcurrent-element"></a><span data-ttu-id="2b161-102">\<element > gcConcurrent</span><span class="sxs-lookup"><span data-stu-id="2b161-102">\<gcConcurrent> Element</span></span>

<span data-ttu-id="2b161-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="2b161-103">Specifies whether the common language runtime runs garbage collection on a separate thread.</span></span>

<span data-ttu-id="2b161-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2b161-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2b161-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2b161-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2b161-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<gcConcurrent >**</span><span class="sxs-lookup"><span data-stu-id="2b161-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<gcConcurrent>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="2b161-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b161-107">Syntax</span></span>

```xml
<gcConcurrent
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2b161-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2b161-108">Attributes and elements</span></span>

<span data-ttu-id="2b161-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2b161-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="2b161-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="2b161-110">Attributes</span></span>

|<span data-ttu-id="2b161-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="2b161-111">Attribute</span></span>|<span data-ttu-id="2b161-112">Popis</span><span class="sxs-lookup"><span data-stu-id="2b161-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="2b161-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="2b161-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="2b161-114">Určuje, zda modul runtime současně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-114">Specifies whether the runtime runs garbage collection concurrently.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="2b161-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="2b161-115">enabled attribute</span></span>

|<span data-ttu-id="2b161-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2b161-116">Value</span></span>|<span data-ttu-id="2b161-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2b161-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="2b161-118">Nespustí souběžný sběr paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-118">Doesn't run garbage collection concurrently.</span></span>|
|`true`|<span data-ttu-id="2b161-119">Souběžně spustí uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-119">Runs garbage collection concurrently.</span></span> <span data-ttu-id="2b161-120">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="2b161-120">This is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="2b161-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="2b161-121">Child elements</span></span>

<span data-ttu-id="2b161-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="2b161-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2b161-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="2b161-123">Parent elements</span></span>

|<span data-ttu-id="2b161-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="2b161-124">Element</span></span>|<span data-ttu-id="2b161-125">Popis</span><span class="sxs-lookup"><span data-stu-id="2b161-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="2b161-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2b161-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="2b161-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2b161-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b161-128">Remarks</span></span>

<span data-ttu-id="2b161-129">Před verzí .NET Framework 4 bylo podporováno souběžné uvolňování paměti pracovní stanice, které provedlo uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="2b161-129">Prior to the .NET Framework 4, workstation garbage collection supported concurrent garbage collection, which performed garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b161-130">V .NET Framework 4 se souběžné uvolňování paměti nahradilo pomocí modulu GC na pozadí, který také provádí uvolňování paměti na pozadí v samostatném vlákně.</span><span class="sxs-lookup"><span data-stu-id="2b161-130">In the .NET Framework 4, concurrent garbage collection was replaced by background GC, which also performs garbage collection in the background on a separate thread.</span></span> <span data-ttu-id="2b161-131">Počínaje .NET Framework 4,5 se kolekce na pozadí stala k dispozici v uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="2b161-131">Starting with the .NET Framework 4.5, background collection became available in server garbage collection.</span></span> <span data-ttu-id="2b161-132">Prvek `<gcConcurrent>` řídí, zda modul runtime provádí souběžné nebo pozadí uvolňování paměti, pokud je k dispozici nebo zda provádí uvolňování paměti v popředí.</span><span class="sxs-lookup"><span data-stu-id="2b161-132">The `<gcConcurrent>` element controls whether the runtime performs either concurrent or background garbage collection, if it's available, or whether it performs garbage collection in the foreground.</span></span>

### <a name="to-disable-background-garbage-collection"></a><span data-ttu-id="2b161-133">Zakázání uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="2b161-133">To disable background garbage collection</span></span>

> [!WARNING]
> <span data-ttu-id="2b161-134">Počínaje rozhraním .NET Framework 4 je souběžné uvolňování paměti nahrazeno uvolňováním paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2b161-134">Starting with the .NET Framework 4, concurrent garbage collection is replaced by background garbage collection.</span></span> <span data-ttu-id="2b161-135">V dokumentaci .NET Framework se používají zaměnitelné a *pozadí* podmínek.</span><span class="sxs-lookup"><span data-stu-id="2b161-135">The terms *concurrent* and *background* are used interchangeably in the .NET Framework documentation.</span></span> <span data-ttu-id="2b161-136">Chcete-li zakázat uvolňování paměti na pozadí, použijte element `<gcConcurrent>`, jak je popsáno v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="2b161-136">To disable background garbage collection, use the `<gcConcurrent>` element, as discussed in this article.</span></span>

<span data-ttu-id="2b161-137">Ve výchozím nastavení používá modul runtime souběžné nebo pozadí uvolňování paměti, které je optimalizováno pro latenci.</span><span class="sxs-lookup"><span data-stu-id="2b161-137">By default, the runtime uses concurrent or background garbage collection, which is optimized for latency.</span></span> <span data-ttu-id="2b161-138">Pokud vaše aplikace zahrnuje těžkou interakci s uživatelem, nechte souběžné uvolňování paměti povolené, aby se minimalizovala doba pozastavení aplikace, aby se provádělo uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-138">If your application involves heavy user interaction, leave concurrent garbage collection enabled to minimize the application's pause time to perform garbage collection.</span></span> <span data-ttu-id="2b161-139">Pokud nastavíte atribut `enabled` prvku `<gcConcurrent>` na `false`, modul runtime používá nesouběžné uvolňování paměti, které je optimalizováno pro propustnost.</span><span class="sxs-lookup"><span data-stu-id="2b161-139">If you set the `enabled` attribute of the `<gcConcurrent>` element to `false`, the runtime uses non-concurrent garbage collection, which is optimized for throughput.</span></span> <span data-ttu-id="2b161-140">Následující konfigurační soubor zakáže uvolňování paměti na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2b161-140">The following configuration file disables background garbage collection.</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="false"/>
   </runtime>
</configuration>
```

 <span data-ttu-id="2b161-141">Pokud je v konfiguračním souboru počítače `<gcConcurrentSetting>` nastavení, definuje výchozí hodnotu pro všechny .NET Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b161-141">If there's a `<gcConcurrentSetting>` setting in the machine configuration file, it defines the default value for all .NET Framework applications.</span></span> <span data-ttu-id="2b161-142">Nastavení konfiguračního souboru počítače přepisuje nastavení konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2b161-142">The machine configuration file setting overrides the application configuration file setting.</span></span>

 <span data-ttu-id="2b161-143">Další informace o souběžném uvolňování paměti na pozadí naleznete v části [souběžné uvolňování paměti](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) v článku [Základy uvolňování](../../../../standard/garbage-collection/fundamentals.md) paměti.</span><span class="sxs-lookup"><span data-stu-id="2b161-143">For more information on concurrent and background garbage collection, see the [Concurrent garbage collection](../../../../standard/garbage-collection/fundamentals.md#concurrent-garbage-collection) section in the [Fundamentals of Garbage Collection](../../../../standard/garbage-collection/fundamentals.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="2b161-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b161-144">Example</span></span>

<span data-ttu-id="2b161-145">Následující příklad povoluje souběžné uvolňování paměti:</span><span class="sxs-lookup"><span data-stu-id="2b161-145">The following example enables concurrent garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcConcurrent enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="2b161-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b161-146">See also</span></span>

- [<span data-ttu-id="2b161-147">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="2b161-147">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2b161-148">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="2b161-148">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="2b161-149">Základy kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="2b161-149">Fundamentals of Garbage Collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
