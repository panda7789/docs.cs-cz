---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9ee6bdb7094ea2bc9e283e331c0f6ad9b68e4f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663426"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="ecfd1-102">\<Thread_UseAllCpuGroups – element ></span><span class="sxs-lookup"><span data-stu-id="ecfd1-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="ecfd1-103">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="ecfd1-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="ecfd1-104">\<configuration></span></span>\
<span data-ttu-id="ecfd1-105">\<běhové > </span><span class="sxs-lookup"><span data-stu-id="ecfd1-105">\<runtime></span></span>\
<span data-ttu-id="ecfd1-106">\<Thread_UseAllCpuGroups ></span><span class="sxs-lookup"><span data-stu-id="ecfd1-106">\<Thread_UseAllCpuGroups></span></span>

## <a name="syntax"></a><span data-ttu-id="ecfd1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecfd1-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ecfd1-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ecfd1-108">Attributes and Elements</span></span>

<span data-ttu-id="ecfd1-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ecfd1-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ecfd1-110">Attributes</span></span>

|<span data-ttu-id="ecfd1-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ecfd1-111">Attribute</span></span>|<span data-ttu-id="ecfd1-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ecfd1-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ecfd1-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ecfd1-114">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ecfd1-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ecfd1-115">enabled Attribute</span></span>

|<span data-ttu-id="ecfd1-116">Value</span><span class="sxs-lookup"><span data-stu-id="ecfd1-116">Value</span></span>|<span data-ttu-id="ecfd1-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ecfd1-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ecfd1-118">Modul runtime nedistribuuje spravovaná vlákna napříč více skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="ecfd1-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="ecfd1-120">Modul runtime distribuuje spravovaná vlákna napříč více skupinami procesorů, pokud má počítač více skupin procesorů a [ \<](gccpugroup-element.md) je povolený element GCCpuGroup >.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ecfd1-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ecfd1-121">Child Elements</span></span>

<span data-ttu-id="ecfd1-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="ecfd1-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ecfd1-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ecfd1-123">Parent Elements</span></span>

|<span data-ttu-id="ecfd1-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ecfd1-124">Element</span></span>|<span data-ttu-id="ecfd1-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ecfd1-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ecfd1-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ecfd1-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ecfd1-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ecfd1-128">Remarks</span></span>

<span data-ttu-id="ecfd1-129">Pokud má počítač více skupin PROCESORů, povolení tohoto elementu způsobí, že modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="ecfd1-130">Chcete-li použít tuto funkci, je nutné povolit [ \<také prvek GCCpuGroup >](gccpugroup-element.md) , který rozšiřuje uvolňování paměti do všech skupin CPU a při vytváření a vyrovnávání haldy bere v úvahu všechny jádra.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="ecfd1-131">Povolení prvku [GCCpuGroup > vyžaduje povolení prvku > gcServer. \<](gccpugroup-element.md) [ \<](gcserver-element.md)</span><span class="sxs-lookup"><span data-stu-id="ecfd1-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="ecfd1-132">Pokud tyto prvky nejsou povoleny, povolení `<Thread_UseAllCpuGroups>` prvku nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="ecfd1-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="ecfd1-133">Example</span></span>

<span data-ttu-id="ecfd1-134">Následující příklad ukazuje, jak povolit podporu více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ecfd1-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ecfd1-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ecfd1-135">See also</span></span>

- [<span data-ttu-id="ecfd1-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ecfd1-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ecfd1-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ecfd1-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ecfd1-138">\<GCCpuGroup – element ></span><span class="sxs-lookup"><span data-stu-id="ecfd1-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
