---
title: Element <Thread_UseAllCpuGroups>
ms.date: 03/30/2017
ms.assetid: d30fe7c5-8469-46e2-b804-e3eec7b24256
ms.openlocfilehash: a3a612c0ffbcb211157b9623d298ce8ad7a13e94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115401"
---
# <a name="thread_useallcpugroups-element"></a><span data-ttu-id="47f38-102">\<element > Thread_UseAllCpuGroups</span><span class="sxs-lookup"><span data-stu-id="47f38-102">\<Thread_UseAllCpuGroups> Element</span></span>

<span data-ttu-id="47f38-103">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="47f38-103">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>

<span data-ttu-id="47f38-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="47f38-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47f38-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="47f38-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="47f38-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<Thread_UseAllCpuGroups >**</span><span class="sxs-lookup"><span data-stu-id="47f38-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<Thread_UseAllCpuGroups>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="47f38-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47f38-107">Syntax</span></span>

```xml
<Thread_UseAllCpuGroups
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47f38-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47f38-108">Attributes and Elements</span></span>

<span data-ttu-id="47f38-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47f38-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="47f38-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="47f38-110">Attributes</span></span>

|<span data-ttu-id="47f38-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="47f38-111">Attribute</span></span>|<span data-ttu-id="47f38-112">Popis</span><span class="sxs-lookup"><span data-stu-id="47f38-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="47f38-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="47f38-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="47f38-114">Určuje, zda modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="47f38-114">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="47f38-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="47f38-115">enabled Attribute</span></span>

|<span data-ttu-id="47f38-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="47f38-116">Value</span></span>|<span data-ttu-id="47f38-117">Popis</span><span class="sxs-lookup"><span data-stu-id="47f38-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="47f38-118">Modul runtime nedistribuuje spravovaná vlákna napříč více skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="47f38-118">The runtime does not distribute managed threads across multiple CPU groups.</span></span> <span data-ttu-id="47f38-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="47f38-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="47f38-120">Modul runtime distribuuje spravovaná vlákna napříč více skupinami PROCESORů, pokud má počítač více skupin PROCESORů a [\<prvek > GCCpuGroup](gccpugroup-element.md) je povolen.</span><span class="sxs-lookup"><span data-stu-id="47f38-120">The runtime distributes managed threads across multiple CPU groups, if the computer has multiple CPU groups and the [\<GCCpuGroup>](gccpugroup-element.md) element is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="47f38-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47f38-121">Child Elements</span></span>

<span data-ttu-id="47f38-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="47f38-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="47f38-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47f38-123">Parent Elements</span></span>

|<span data-ttu-id="47f38-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="47f38-124">Element</span></span>|<span data-ttu-id="47f38-125">Popis</span><span class="sxs-lookup"><span data-stu-id="47f38-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="47f38-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47f38-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="47f38-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="47f38-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47f38-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47f38-128">Remarks</span></span>

<span data-ttu-id="47f38-129">Pokud má počítač více skupin PROCESORů, povolení tohoto elementu způsobí, že modul runtime distribuuje spravovaná vlákna napříč všemi skupinami PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="47f38-129">When a computer has multiple CPU groups, enabling this element causes the runtime to distribute managed threads across all CPU groups.</span></span> <span data-ttu-id="47f38-130">Chcete-li použít tuto funkci, je nutné povolit také [\<element > GCCpuGroup](gccpugroup-element.md) , který rozšiřuje uvolňování paměti do všech skupin CPU a při vytváření a vyrovnávání haldy bere v úvahu všechny jádra.</span><span class="sxs-lookup"><span data-stu-id="47f38-130">To use this feature, you must also enable the [\<GCCpuGroup>](gccpugroup-element.md) element, which extends garbage collection to all CPU groups and takes all cores into account when creating and balancing heaps.</span></span> <span data-ttu-id="47f38-131">Povolení prvku [\<> GCCpuGroup](gccpugroup-element.md) vyžaduje povolení prvku [\<gcServer](gcserver-element.md) .</span><span class="sxs-lookup"><span data-stu-id="47f38-131">Enabling the [\<GCCpuGroup>](gccpugroup-element.md) element requires enabling the [\<gcServer>](gcserver-element.md) element.</span></span> <span data-ttu-id="47f38-132">Pokud nejsou tyto prvky povoleny, povolení prvku `<Thread_UseAllCpuGroups>` nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="47f38-132">If these elements are not enabled, enabling the `<Thread_UseAllCpuGroups>` element has no effect.</span></span>

## <a name="example"></a><span data-ttu-id="47f38-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="47f38-133">Example</span></span>

<span data-ttu-id="47f38-134">Následující příklad ukazuje, jak povolit podporu více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="47f38-134">The following example shows how to enable support for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <Thread_UseAllCpuGroups enabled="true"/>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="47f38-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47f38-135">See also</span></span>

- [<span data-ttu-id="47f38-136">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="47f38-136">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="47f38-137">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="47f38-137">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="47f38-138">\<element > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="47f38-138">\<GCCpuGroup> Element</span></span>](gccpugroup-element.md)
