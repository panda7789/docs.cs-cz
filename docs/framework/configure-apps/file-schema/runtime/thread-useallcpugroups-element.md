---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9758e009e012c8af5f5f7bd19dcd21f34b8c7d96
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689732"
---
# <a name="threaduseallcpugroups-element"></a><span data-ttu-id="18898-102">\<Thread_UseAllCpuGroups > – Element</span><span class="sxs-lookup"><span data-stu-id="18898-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="18898-103">Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="18898-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="18898-104">\<Konfigurace > </span><span class="sxs-lookup"><span data-stu-id="18898-104">\<configuration></span></span>\
<span data-ttu-id="18898-105">\<modul runtime > </span><span class="sxs-lookup"><span data-stu-id="18898-105">\<runtime></span></span>\
<span data-ttu-id="18898-106">\<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="18898-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="18898-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18898-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="18898-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="18898-108">Attributes and Elements</span></span>

<span data-ttu-id="18898-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="18898-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="18898-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="18898-110">Attributes</span></span>

|<span data-ttu-id="18898-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="18898-111">Attribute</span></span>|<span data-ttu-id="18898-112">Popis</span><span class="sxs-lookup"><span data-stu-id="18898-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="18898-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="18898-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="18898-114">Určuje, zda modul runtime provádí distribuci spravovaných vláken ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="18898-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="18898-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="18898-115">enabled Attribute</span></span>

|<span data-ttu-id="18898-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="18898-116">Value</span></span>|<span data-ttu-id="18898-117">Popis</span><span class="sxs-lookup"><span data-stu-id="18898-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="18898-118">Modul runtime neprovádí distribuci spravovaných vláken ve více skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="18898-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="18898-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="18898-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="18898-120">Modul runtime provádí distribuci spravovaných vláken ve více skupinách procesoru, pokud má počítač více skupin procesorů a [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) prvek povolený.</span><span class="sxs-lookup"><span data-stu-id="18898-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="18898-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="18898-121">Child Elements</span></span>

<span data-ttu-id="18898-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="18898-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="18898-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="18898-123">Parent Elements</span></span>

|<span data-ttu-id="18898-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="18898-124">Element</span></span>|<span data-ttu-id="18898-125">Popis</span><span class="sxs-lookup"><span data-stu-id="18898-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="18898-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18898-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="18898-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="18898-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="18898-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18898-128">Remarks</span></span>

<span data-ttu-id="18898-129">Pokud počítač má více skupin procesorů, povolení tohoto prvku způsobí, že modul runtime bude distribuovat spravovaná vlákna ve všech skupinách procesoru.</span><span class="sxs-lookup"><span data-stu-id="18898-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="18898-130">Chcete-li tuto funkci používat, musíte také povolit [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, který rozšiřuje uvolňování paměti na všech skupinách procesoru a všechna jádra bere v úvahu při vytváření a rozložení zátěže haldy.</span><span class="sxs-lookup"><span data-stu-id="18898-130">To use this feature, you must also enable the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="18898-131">Povolení [ \<gccpugroup – >](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element vyžaduje povolení [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="18898-131">Enabling the [\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md) element requires enabling the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element.</span></span> <span data-ttu-id="18898-132">Pokud tyto prvky nejsou povoleny, takže `<Thread_UseAllCpuGroups>` element nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="18898-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="18898-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="18898-133">Example</span></span>

<span data-ttu-id="18898-134">Následující příklad ukazuje, jak povolit podporu pro více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="18898-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="18898-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18898-135">See also</span></span>

- [<span data-ttu-id="18898-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="18898-136">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="18898-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="18898-137">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="18898-138">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="18898-138">\<GCCpuGroup> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)
