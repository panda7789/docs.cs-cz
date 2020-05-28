---
title: Element GCNoAffinitize
ms.date: 11/08/2019
helpviewer_keywords:
- gcNoAffinitize element
- <gcNoAffinitize> element
ms.openlocfilehash: 16d6e5adefe2b632d7251669650058d7df7cea70
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004735"
---
# <a name="gcnoaffinitize-element"></a><span data-ttu-id="94d23-102">\<GCNoAffinitize> – element</span><span class="sxs-lookup"><span data-stu-id="94d23-102">\<GCNoAffinitize> element</span></span>

<span data-ttu-id="94d23-103">Určuje, jestli se mají spřažení vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="94d23-103">Specifies whether or not to affinitize server GC threads with CPUs.</span></span>

\<configuration>\
&nbsp;&nbsp;\<runtime>\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCNoAffinitize>

## <a name="syntax"></a><span data-ttu-id="94d23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94d23-104">Syntax</span></span>

```xml
<GCNoAffinitize
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="94d23-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="94d23-105">Attributes and elements</span></span>

<span data-ttu-id="94d23-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="94d23-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="94d23-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="94d23-107">Attributes</span></span>

|<span data-ttu-id="94d23-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="94d23-108">Attribute</span></span>|<span data-ttu-id="94d23-109">Description</span><span class="sxs-lookup"><span data-stu-id="94d23-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="94d23-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="94d23-110">Required attribute.</span></span><br /><br /><span data-ttu-id="94d23-111">Určuje, zda jsou vlákna nebo haldy GC serveru spřažené s procesory dostupnými v počítači.</span><span class="sxs-lookup"><span data-stu-id="94d23-111">Specifies whether server GC threads/heaps are affinitized with the processors available on the machine.</span></span>|

#### <a name="enabled-attribute"></a><span data-ttu-id="94d23-112">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="94d23-112">enabled attribute</span></span>

|<span data-ttu-id="94d23-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="94d23-113">Value</span></span>|<span data-ttu-id="94d23-114">Description</span><span class="sxs-lookup"><span data-stu-id="94d23-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="94d23-115">Spřáhne vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="94d23-115">Affinitizes server GC threads with CPUs.</span></span> <span data-ttu-id="94d23-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="94d23-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="94d23-117">Nespřaženíuje vlákna GC serveru pomocí procesorů.</span><span class="sxs-lookup"><span data-stu-id="94d23-117">Does not affinitize server GC threads with CPUs.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="94d23-118">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="94d23-118">Child elements</span></span>

<span data-ttu-id="94d23-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="94d23-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="94d23-120">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="94d23-120">Parent elements</span></span>

|<span data-ttu-id="94d23-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="94d23-121">Element</span></span>|<span data-ttu-id="94d23-122">Description</span><span class="sxs-lookup"><span data-stu-id="94d23-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="94d23-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94d23-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="94d23-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="94d23-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="94d23-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94d23-125">Remarks</span></span>

<span data-ttu-id="94d23-126">Ve výchozím nastavení jsou vlákna uvolňování paměti serveru pevně spřažené s příslušnými procesory.</span><span class="sxs-lookup"><span data-stu-id="94d23-126">By default, server GC threads are hard-affinitized with their respective CPUs.</span></span> <span data-ttu-id="94d23-127">Každý z dostupných procesorů systému má vlastní haldu a vlákno GC.</span><span class="sxs-lookup"><span data-stu-id="94d23-127">Each of the system's available processors has its own GC heap and thread.</span></span> <span data-ttu-id="94d23-128">To je obvykle preferované nastavení, protože optimalizuje využití mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="94d23-128">This is typically the preferred setting since it optimizes cache usage.</span></span> <span data-ttu-id="94d23-129">Počínaje .NET Framework 4.6.2 nastavením atributu elementu **GCNoAffinitize** `enabled` na můžete `true` určit, že vlákna uvolňování paměti serveru a CPU by neměly být pevně spojeny.</span><span class="sxs-lookup"><span data-stu-id="94d23-129">Starting with .NET Framework 4.6.2, by setting the **GCNoAffinitize** element's `enabled` attribute to `true`, you can specify that server GC threads and CPUs should not be tightly coupled.</span></span>

<span data-ttu-id="94d23-130">Můžete zadat pouze konfigurační element **GCNoAffinitize** , aby nespřaženíy vlákna GC serveru pomocí CPU.</span><span class="sxs-lookup"><span data-stu-id="94d23-130">You can specify the **GCNoAffinitize** configuration element alone to not affinitize server GC threads with CPUs.</span></span> <span data-ttu-id="94d23-131">Můžete ji také použít spolu s elementem [GCHeapCount](gcheapcount-element.md) k řízení počtu hald GC a vláken používaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="94d23-131">You can also use it along with the [GCHeapCount](gcheapcount-element.md) element to control the number of GC heaps and threads used by an application.</span></span>

<span data-ttu-id="94d23-132">Pokud `enabled` je atribut elementu **GCNoAffinitize** `false` (jeho výchozí hodnota), můžete také použít element [GCHEAPCOUNT](gcheapcount-element.md) k určení počtu vláken GC a hald společně s elementem [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) pro určení procesorů, do kterých jsou vlákna uvolňování paměti a haldy spřažené.</span><span class="sxs-lookup"><span data-stu-id="94d23-132">If the `enabled` attribute of the **GCNoAffinitize** element is `false` (its default value), you can also use the [GCHeapCount](gcheapcount-element.md) element to specify the number of GC threads and heaps, along with the [GCHeapAffinitizeMask](gcheapaffinitizemask-element.md) element to specify the processors to which the GC threads and heaps are affinitized.</span></span>

## <a name="example"></a><span data-ttu-id="94d23-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="94d23-133">Example</span></span>

<span data-ttu-id="94d23-134">Následující příklad neprovádí pevným spřažením vláken v GC serveru:</span><span class="sxs-lookup"><span data-stu-id="94d23-134">The following example does not hard-affinitize server GC threads:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

<span data-ttu-id="94d23-135">Následující příklad nespřaženíuje vlákna uvolňování paměti serveru a omezuje počet hald a vláken GC na 10:</span><span class="sxs-lookup"><span data-stu-id="94d23-135">The following example does not affinitize server GC threads and limits the number of GC heaps/threads to 10:</span></span>

```xml
<configuration>
   <runtime>
      <gcServer enabled="true"/>
      <GCHeapCount enabled="10"/>
      <GCNoAffinitize enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="94d23-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="94d23-136">See also</span></span>

- <xref:System.Runtime.GCSettings.IsServerGC%2A?displayProperty=nameWithType>
- [<span data-ttu-id="94d23-137">Element GCHeapAffinitizeMask</span><span class="sxs-lookup"><span data-stu-id="94d23-137">GCHeapAffinitizeMask element</span></span>](gcheapaffinitizemask-element.md)
- [<span data-ttu-id="94d23-138">Element GCHeapCount</span><span class="sxs-lookup"><span data-stu-id="94d23-138">GCHeapCount element</span></span>](gcheapcount-element.md)
- [<span data-ttu-id="94d23-139">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="94d23-139">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="94d23-140">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="94d23-140">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="94d23-141">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="94d23-141">Configuration File Schema</span></span>](../index.md)
