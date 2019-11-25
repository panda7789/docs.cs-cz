---
title: Element GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 4031ff19131c905072696837d1622dbb6e54ae61
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978373"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="c84ce-102">\<element > GCNoAffinitize</span><span class="sxs-lookup"><span data-stu-id="c84ce-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="c84ce-103">Určuje, jestli se mají spřažení vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="c84ce-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

<span data-ttu-id="c84ce-104">Konfigurace \<> </span><span class="sxs-lookup"><span data-stu-id="c84ce-104">\<configuration></span></span>\
<span data-ttu-id="c84ce-105">&nbsp;&nbsp;\<runtime > </span><span class="sxs-lookup"><span data-stu-id="c84ce-105">&nbsp;&nbsp;\<runtime></span></span>\
<span data-ttu-id="c84ce-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize ></span><span class="sxs-lookup"><span data-stu-id="c84ce-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize></span></span>

## <a name="syntax"></a><span data-ttu-id="c84ce-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c84ce-107">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c84ce-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c84ce-108">Attributes and elements</span></span>

<span data-ttu-id="c84ce-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c84ce-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c84ce-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c84ce-110">Attributes</span></span>

|<span data-ttu-id="c84ce-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c84ce-111">Attribute</span></span>|<span data-ttu-id="c84ce-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c84ce-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c84ce-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c84ce-113">Required attribute.</span></span><br /><br /><span data-ttu-id="c84ce-114">Určuje, zda jsou vlákna nebo haldy GC serveru spřažené s procesory dostupnými v počítači.</span><span class="sxs-lookup"><span data-stu-id="c84ce-114">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="c84ce-115">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="c84ce-115">enabled attribute</span></span>

|<span data-ttu-id="c84ce-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c84ce-116">Value</span></span>|<span data-ttu-id="c84ce-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c84ce-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c84ce-118">Spřáhne vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="c84ce-118">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="c84ce-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c84ce-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="c84ce-120">Nespřaženíuje vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="c84ce-120">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c84ce-121">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="c84ce-121">Child elements</span></span>

<span data-ttu-id="c84ce-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="c84ce-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c84ce-123">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="c84ce-123">Parent elements</span></span>

|<span data-ttu-id="c84ce-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c84ce-124">Element</span></span>|<span data-ttu-id="c84ce-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c84ce-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c84ce-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c84ce-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c84ce-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c84ce-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c84ce-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c84ce-128">Remarks</span></span>

<span data-ttu-id="c84ce-129">Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s příslušnými procesory.</span><span class="sxs-lookup"><span data-stu-id="c84ce-129">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="c84ce-130">Každý z dostupných procesorů systému má vlastní haldu a vlákno GC.</span><span class="sxs-lookup"><span data-stu-id="c84ce-130">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="c84ce-131">To je obvykle preferované nastavení, protože optimalizuje využití mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c84ce-131">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="c84ce-132">Počínaje .NET Framework 4.6.2 nastavením atributu `enabled` elementu **GCNoAffinitize** na hodnotu `false`můžete určit, že vlákna uvolňování paměti serveru a CPU by neměly být pevně spojeny.</span><span class="sxs-lookup"><span data-stu-id="c84ce-132">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `false`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="c84ce-133">Můžete zadat pouze konfigurační element **GCNoAffinitize** , aby nespřaženíy vlákna GC serveru pomocí CPU.</span><span class="sxs-lookup"><span data-stu-id="c84ce-133">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="c84ce-134">Můžete ji také použít spolu s elementem [GCHeapCount](gcheapcount-element.md) k řízení počtu hald GC a vláken používaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="c84ce-134">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="c84ce-135">Pokud je atribut `enabled` elementu **GCNoAffinitize** `false` (jeho výchozí hodnota), můžete také použít element [GCHeapCount](gcheapcount-element.md) k určení počtu vláken GC a hald společně s elementem [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pro určení procesorů, do kterých jsou vlákna uvolňování paměti a haldy spřažené.</span><span class="sxs-lookup"><span data-stu-id="c84ce-135">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="c84ce-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="c84ce-136">Example</span></span>

<span data-ttu-id="c84ce-137">Následující příklad neprovádí pevným spřažením vláken v GC serveru:</span><span class="sxs-lookup"><span data-stu-id="c84ce-137">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="c84ce-138">Následující příklad nespřaženíuje vlákna uvolňování paměti serveru a omezuje počet hald a vláken GC na 10:</span><span class="sxs-lookup"><span data-stu-id="c84ce-138">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c84ce-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c84ce-139">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c84ce-140">Element GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="c84ce-140">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="c84ce-141">Element GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="c84ce-141">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="c84ce-142">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="c84ce-142">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="c84ce-143">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="c84ce-143">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c84ce-144">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c84ce-144">Configuration File Schema</span></span>](../index.md)
