---
title: Element gcServer
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcServer
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcServer
helpviewer_keywords:
- gcServer element
- <gcServer> element
ms.assetid: 8d25b80e-2581-4803-bd87-a59528e3cb03
ms.openlocfilehash: 8eab5e36bab90510aff4f1a3e15328197ac59ed7
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73968938"
---
# <a name="gcserver-element"></a><span data-ttu-id="0daee-102">\<element > gcServer</span><span class="sxs-lookup"><span data-stu-id="0daee-102">\<gcServer> element</span></span>

<span data-ttu-id="0daee-103">Určuje, zda modul CLR (Common Language Runtime) spouští uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-103">Specifies whether the common language runtime runs server garbage collection.</span></span>

<span data-ttu-id="0daee-104">[konfigurační >\<](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0daee-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="0daee-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="0daee-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="0daee-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer ></span><span class="sxs-lookup"><span data-stu-id="0daee-106">&nbsp;&nbsp;&nbsp;&nbsp;\<gcServer></span></span>

## <a name="syntax"></a><span data-ttu-id="0daee-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0daee-107">Syntax</span></span>

```xml
<gcServer
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0daee-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0daee-108">Attributes and elements</span></span>

<span data-ttu-id="0daee-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0daee-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="0daee-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="0daee-110">Attributes</span></span>

|<span data-ttu-id="0daee-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="0daee-111">Attribute</span></span>|<span data-ttu-id="0daee-112">Popis</span><span class="sxs-lookup"><span data-stu-id="0daee-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="0daee-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="0daee-113">Required attribute.</span></span><br /><br /><span data-ttu-id="0daee-114">Určuje, zda modul runtime spouští uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-114">Specifies whether the runtime runs server garbage collection.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="0daee-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="0daee-115">enabled attribute</span></span>

|<span data-ttu-id="0daee-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0daee-116">Value</span></span>|<span data-ttu-id="0daee-117">Popis</span><span class="sxs-lookup"><span data-stu-id="0daee-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="0daee-118">Nespustí shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-118">Does not run server garbage collection.</span></span> <span data-ttu-id="0daee-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="0daee-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="0daee-120">Spustí shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-120">Runs server garbage collection.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="0daee-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="0daee-121">Child elements</span></span>

<span data-ttu-id="0daee-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0daee-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="0daee-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="0daee-123">Parent elements</span></span>

|<span data-ttu-id="0daee-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0daee-124">Element</span></span>|<span data-ttu-id="0daee-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0daee-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="0daee-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0daee-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="0daee-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="0daee-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0daee-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0daee-128">Remarks</span></span>

<span data-ttu-id="0daee-129">Modul CLR (Common Language Runtime) podporuje dva typy uvolňování paměti: uvolnění paměti pracovní stanice, které je k dispozici ve všech systémech a uvolňování paměti serveru, které je k dispozici v systémech s více procesory.</span><span class="sxs-lookup"><span data-stu-id="0daee-129">The common language runtime (CLR) supports two types of garbage collection: workstation garbage collection, which is available on all systems, and server garbage collection, which is available on multiprocessor systems.</span></span> <span data-ttu-id="0daee-130">Použijte element **gcServer** k řízení typu uvolňování paměti, který modul CLR provede.</span><span class="sxs-lookup"><span data-stu-id="0daee-130">Use the **gcServer** element to control the type of garbage collection the CLR performs.</span></span> <span data-ttu-id="0daee-131">Pomocí vlastnosti <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> určete, zda je povoleno uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-131">Use the <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType> property to determine if server garbage collection is enabled.</span></span>

<span data-ttu-id="0daee-132">V případě počítačů s jedním procesorem by měla být výchozí kolekce uvolnění paměti pracovní stanice nejrychlejší možností.</span><span class="sxs-lookup"><span data-stu-id="0daee-132">For single-processor computers, the default workstation garbage collection should be the fastest option.</span></span> <span data-ttu-id="0daee-133">Pro počítače se dvěma procesory lze použít buď pracovní stanici, nebo server.</span><span class="sxs-lookup"><span data-stu-id="0daee-133">Either workstation or server can be used for two-processor computers.</span></span> <span data-ttu-id="0daee-134">Uvolňování paměti serveru by mělo být nejrychlejší možností pro více než dva procesory.</span><span class="sxs-lookup"><span data-stu-id="0daee-134">Server garbage collection should be the fastest option for more than two processors.</span></span> <span data-ttu-id="0daee-135">Nejčastěji serverové systémy s více procesory zakazují použití GC serveru a místo toho používají GC z pracovní stanice, když mnoho instancí serverové aplikace běží na stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="0daee-135">Most commonly, multiprocessor server systems disable server GC and use workstation GC instead when many instances of a server app run on the same machine.</span></span>

<span data-ttu-id="0daee-136">Tento element lze použít pouze v konfiguračním souboru aplikace; ignoruje se, pokud je v konfiguračním souboru počítače.</span><span class="sxs-lookup"><span data-stu-id="0daee-136">This element can be used only in the application configuration file; it is ignored if it is in the machine configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="0daee-137">V .NET Framework 4 a starších verzích není souběžné uvolňování paměti k dispozici, když je povoleno uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-137">In the .NET Framework 4 and earlier versions, concurrent garbage collection is not available when server garbage collection is enabled.</span></span> <span data-ttu-id="0daee-138">Počínaje .NET Framework 4,5 je shromažďování paměti serveru souběžné.</span><span class="sxs-lookup"><span data-stu-id="0daee-138">Starting with the .NET Framework 4.5, server garbage collection is concurrent.</span></span> <span data-ttu-id="0daee-139">Chcete-li použít nesouběžné uvolňování paměti serveru, nastavte element **gcServer** na hodnotu `true` a [element gcConcurrent](gcconcurrent-element.md) na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="0daee-139">To use non-concurrent server garbage collection, set the **gcServer** element to `true` and the [gcConcurrent element](gcconcurrent-element.md) to `false`.</span></span>

<span data-ttu-id="0daee-140">Počínaje .NET Framework 4.6.2 můžete ke konfiguraci GC serveru použít taky tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="0daee-140">Starting with .NET Framework 4.6.2, you can also use the following elements to configure server GC:</span></span>

- <span data-ttu-id="0daee-141">[GCNoAffinitize](gcnoaffinitize-element.md), která určuje, zda existuje spřažení mezi haldami a procesory GC serveru.</span><span class="sxs-lookup"><span data-stu-id="0daee-141">[GCNoAffinitize](gcnoaffinitize-element.md), which specifies whether there is an affinity between server GC heaps and processors.</span></span> <span data-ttu-id="0daee-142">Ve výchozím nastavení je k dispozici jedna Halda GC serveru pro každý procesor.</span><span class="sxs-lookup"><span data-stu-id="0daee-142">By default, there is one server GC heap for each processor.</span></span>

- <span data-ttu-id="0daee-143">[GCHeapCount](gcheapcount-element.md), která omezuje počet hald používaných procesem.</span><span class="sxs-lookup"><span data-stu-id="0daee-143">[GCHeapCount](gcheapcount-element.md), which limits the number of heaps used by a process.</span></span>

- <span data-ttu-id="0daee-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), která definuje spřažení mezi dostupnými haldami GC serveru a jednotlivými procesory.</span><span class="sxs-lookup"><span data-stu-id="0daee-144">[GCHeapAffinitizeMask](gcheapaffinitizemask-element.md), which defines the affinity between the available server GC heaps and individual processors.</span></span>

## <a name="example"></a><span data-ttu-id="0daee-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="0daee-145">Example</span></span>

<span data-ttu-id="0daee-146">Následující příklad povoluje uvolňování paměti serveru:</span><span class="sxs-lookup"><span data-stu-id="0daee-146">The following example enables server garbage collection:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="0daee-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0daee-147">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0daee-148">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="0daee-148">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="0daee-149">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="0daee-149">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="0daee-150">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0daee-150">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
