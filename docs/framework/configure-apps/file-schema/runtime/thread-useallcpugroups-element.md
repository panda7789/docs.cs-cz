---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115401"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="53d1f-102">Element \<Thread_UseAllCpuGroups></span><span class="sxs-lookup"><span data-stu-id="53d1f-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="53d1f-103">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="53d1f-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**  

## <a name="syntax"></a><span data-ttu-id="53d1f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53d1f-104">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53d1f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53d1f-105">Attributes and Elements</span></span>

<span data-ttu-id="53d1f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53d1f-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="53d1f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="53d1f-107">Attributes</span></span>

|<span data-ttu-id="53d1f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="53d1f-108">Attribute</span></span>|<span data-ttu-id="53d1f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="53d1f-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="53d1f-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="53d1f-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="53d1f-111">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="53d1f-111">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="53d1f-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="53d1f-112">enabled Attribute</span></span>

|<span data-ttu-id="53d1f-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="53d1f-113">Value</span></span>|<span data-ttu-id="53d1f-114">Description</span><span class="sxs-lookup"><span data-stu-id="53d1f-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="53d1f-115">Modul runtime nedistribuuje spravovaná vlákna napříč více skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="53d1f-115">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="53d1f-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="53d1f-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="53d1f-117">Modul runtime distribuuje spravovaná vlákna napříč více skupinami PROCESORů, pokud má počítač více skupin PROCESORů a [\<GCCpuGroup>](gccpugroup-element.md) element je povolen.</span><span class="sxs-lookup"><span data-stu-id="53d1f-117">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="53d1f-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53d1f-118">Child Elements</span></span>

<span data-ttu-id="53d1f-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="53d1f-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53d1f-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53d1f-120">Parent Elements</span></span>

|<span data-ttu-id="53d1f-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="53d1f-121">Element</span></span>|<span data-ttu-id="53d1f-122">Description</span><span class="sxs-lookup"><span data-stu-id="53d1f-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="53d1f-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="53d1f-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="53d1f-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="53d1f-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="53d1f-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53d1f-125">Remarks</span></span>

<span data-ttu-id="53d1f-126">Pokud má počítač více skupin PROCESORů, povolení tohoto elementu způsobí, že modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="53d1f-126">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="53d1f-127">Chcete-li použít tuto funkci, je nutné povolit také [\<GCCpuGroup>](gccpugroup-element.md) element, který rozšiřuje uvolňování paměti do všech skupin CPU a při vytváření a vyrovnávání haldy bere v úvahu všechny jádra.</span><span class="sxs-lookup"><span data-stu-id="53d1f-127">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="53d1f-128">Povolení [\<GCCpuGroup>](gccpugroup-element.md) elementu vyžaduje povolení [\<gcServer>](gcserver-element.md) prvku.</span><span class="sxs-lookup"><span data-stu-id="53d1f-128">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="53d1f-129">Pokud tyto prvky nejsou povoleny, povolení `<Thread_UseAllCpuGroups>` prvku nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="53d1f-129">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="53d1f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="53d1f-130">Example</span></span>

<span data-ttu-id="53d1f-131">Následující příklad ukazuje, jak povolit podporu více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="53d1f-131">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="53d1f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="53d1f-132">See also</span></span>

- [<span data-ttu-id="53d1f-133">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="53d1f-133">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="53d1f-134">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="53d1f-134">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="53d1f-135">\<GCCpuGroup>Objekt</span><span class="sxs-lookup"><span data-stu-id="53d1f-135">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
