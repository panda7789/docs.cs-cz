---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56b23b6d5fca6d0527d509c9b6a6fc6dd82336
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920785"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="68db9-102">\<GCCpuGroup – element ></span><span class="sxs-lookup"><span data-stu-id="68db9-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="68db9-103">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="68db9-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="68db9-104">\<> Konfigurace </span><span class="sxs-lookup"><span data-stu-id="68db9-104">\<configuration></span></span>\
<span data-ttu-id="68db9-105">\<běhové > </span><span class="sxs-lookup"><span data-stu-id="68db9-105">\<runtime></span></span>\
<span data-ttu-id="68db9-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="68db9-106">\<GCCpuGroup></span></span>

## <a name="syntax"></a><span data-ttu-id="68db9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68db9-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="68db9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68db9-108">Attributes and Elements</span></span>

<span data-ttu-id="68db9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68db9-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="68db9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="68db9-110">Attributes</span></span>

|<span data-ttu-id="68db9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="68db9-111">Attribute</span></span>|<span data-ttu-id="68db9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="68db9-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="68db9-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="68db9-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="68db9-114">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="68db9-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="68db9-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="68db9-115">enabled Attribute</span></span>

|<span data-ttu-id="68db9-116">Value</span><span class="sxs-lookup"><span data-stu-id="68db9-116">Value</span></span>|<span data-ttu-id="68db9-117">Popis</span><span class="sxs-lookup"><span data-stu-id="68db9-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="68db9-118">Uvolňování paměti nepodporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="68db9-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="68db9-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="68db9-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="68db9-120">Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="68db9-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="68db9-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68db9-121">Child Elements</span></span>

<span data-ttu-id="68db9-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="68db9-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="68db9-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68db9-123">Parent Elements</span></span>

|<span data-ttu-id="68db9-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="68db9-124">Element</span></span>|<span data-ttu-id="68db9-125">Popis</span><span class="sxs-lookup"><span data-stu-id="68db9-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="68db9-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68db9-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="68db9-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="68db9-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="68db9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68db9-128">Remarks</span></span>

<span data-ttu-id="68db9-129">Pokud je v počítači více skupin procesorů a uvolňování paměti serveru (viz [ \<gcServer >](gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU a při vytváření a zabere všechny jádra do účtu. vyvážení hald.</span><span class="sxs-lookup"><span data-stu-id="68db9-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="68db9-130">Tento prvek se vztahuje pouze na vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="68db9-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="68db9-131">Chcete-li povolit modulu runtime pro distribuci uživatelských vláken napříč všemi skupinami procesorů, je [ \<](thread-useallcpugroups-element.md) nutné povolit také > element Thread_UseAllCpuGroups.</span><span class="sxs-lookup"><span data-stu-id="68db9-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="68db9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="68db9-132">Example</span></span>

<span data-ttu-id="68db9-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="68db9-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="68db9-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68db9-134">See also</span></span>

- [<span data-ttu-id="68db9-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="68db9-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="68db9-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="68db9-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="68db9-137">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="68db9-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="68db9-138">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="68db9-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
