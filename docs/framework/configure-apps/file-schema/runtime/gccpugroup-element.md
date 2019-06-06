---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1251f286a4e6168ef1d18b05288e0c5f353ad828
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689881"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="46654-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="46654-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="46654-103">Určuje, zda uvolňování podporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="46654-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="46654-104">\<Konfigurace > </span><span class="sxs-lookup"><span data-stu-id="46654-104">\<configuration></span></span>\
<span data-ttu-id="46654-105">\<modul runtime > </span><span class="sxs-lookup"><span data-stu-id="46654-105">\<runtime></span></span>\
<span data-ttu-id="46654-106">\<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="46654-106">\<GCCpuGroup></span></span>

## <a name="syntax"></a><span data-ttu-id="46654-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46654-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="46654-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46654-108">Attributes and Elements</span></span>

<span data-ttu-id="46654-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46654-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="46654-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="46654-110">Attributes</span></span>

|<span data-ttu-id="46654-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="46654-111">Attribute</span></span>|<span data-ttu-id="46654-112">Popis</span><span class="sxs-lookup"><span data-stu-id="46654-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="46654-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="46654-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="46654-114">Určuje, zda uvolňování podporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="46654-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="46654-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="46654-115">enabled Attribute</span></span>

|<span data-ttu-id="46654-116">Value</span><span class="sxs-lookup"><span data-stu-id="46654-116">Value</span></span>|<span data-ttu-id="46654-117">Popis</span><span class="sxs-lookup"><span data-stu-id="46654-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="46654-118">Uvolňování paměti kolekce nepodporuje více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="46654-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="46654-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="46654-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="46654-120">Uvolňování paměti podporuje více skupin procesorů, pokud je povolené uvolnění paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="46654-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="46654-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46654-121">Child Elements</span></span>

<span data-ttu-id="46654-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="46654-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="46654-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46654-123">Parent Elements</span></span>

|<span data-ttu-id="46654-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="46654-124">Element</span></span>|<span data-ttu-id="46654-125">Popis</span><span class="sxs-lookup"><span data-stu-id="46654-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="46654-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46654-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="46654-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="46654-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="46654-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46654-128">Remarks</span></span>

<span data-ttu-id="46654-129">Když počítač má více skupin procesorů a uvolňování paměti serveru je povolená (najdete v článku [ \<gcServer >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru a přejde do všech jader účet při vytváření a rozložení zátěže haldy.</span><span class="sxs-lookup"><span data-stu-id="46654-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="46654-130">Tento element se vztahují pouze k vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="46654-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="46654-131">Pokud chcete povolit modul runtime bude distribuovat Uživatelská vlákna ve všech skupinách procesoru, musíte také povolit [ \<Thread_UseAllCpuGroups >](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="46654-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="46654-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="46654-132">Example</span></span>

<span data-ttu-id="46654-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesorů.</span><span class="sxs-lookup"><span data-stu-id="46654-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="46654-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46654-134">See also</span></span>

- [<span data-ttu-id="46654-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="46654-135">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="46654-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="46654-136">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="46654-137">Chcete-li zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="46654-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="46654-138">Uvolňování paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="46654-138">Workstation and server garbage collection</span></span>](../../../../../docs/standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
