---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102889"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="c2498-102">\<Prvek> skupiny GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="c2498-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="c2498-103">Určuje, zda uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="c2498-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="c2498-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2498-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c2498-105">&nbsp;&nbsp;[**\<>za běhu**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="c2498-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="c2498-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<>GCCpuGroup**</span><span class="sxs-lookup"><span data-stu-id="c2498-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="c2498-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2498-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c2498-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c2498-108">Attributes and Elements</span></span>

<span data-ttu-id="c2498-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c2498-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c2498-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="c2498-110">Attributes</span></span>

|<span data-ttu-id="c2498-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="c2498-111">Attribute</span></span>|<span data-ttu-id="c2498-112">Popis</span><span class="sxs-lookup"><span data-stu-id="c2498-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="c2498-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="c2498-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="c2498-114">Určuje, zda uvolňování paměti podporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="c2498-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="c2498-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="c2498-115">enabled Attribute</span></span>

|<span data-ttu-id="c2498-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c2498-116">Value</span></span>|<span data-ttu-id="c2498-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c2498-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="c2498-118">Uvolňování paměti nepodporuje více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="c2498-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="c2498-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="c2498-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="c2498-120">Uvolňování paměti podporuje více skupin procesoru, pokud je povoleno uvolňování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="c2498-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c2498-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c2498-121">Child Elements</span></span>

<span data-ttu-id="c2498-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="c2498-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c2498-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c2498-123">Parent Elements</span></span>

|<span data-ttu-id="c2498-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="c2498-124">Element</span></span>|<span data-ttu-id="c2498-125">Popis</span><span class="sxs-lookup"><span data-stu-id="c2498-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c2498-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2498-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="c2498-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c2498-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c2498-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2498-128">Remarks</span></span>

<span data-ttu-id="c2498-129">Pokud má počítač více skupin procesoru a je povoleno uvolňování paměti serveru (viz [ \<gcServer>](gcserver-element.md) element), povolení tohoto prvku rozšiřuje uvolňování paměti ve všech skupinách procesoru a bere v úvahu všechna jádra při vytváření a vyvažování hromady.</span><span class="sxs-lookup"><span data-stu-id="c2498-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="c2498-130">Tento prvek platí pouze pro vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c2498-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="c2498-131">Chcete-li povolit runtime distribuovat vlákna uživatelů ve všech skupinách procesoru, musíte také povolit [ \<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) prvek.</span><span class="sxs-lookup"><span data-stu-id="c2498-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="c2498-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2498-132">Example</span></span>

<span data-ttu-id="c2498-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin procesoru.</span><span class="sxs-lookup"><span data-stu-id="c2498-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="c2498-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2498-134">See also</span></span>

- [<span data-ttu-id="c2498-135">Schéma nastavení běhu</span><span class="sxs-lookup"><span data-stu-id="c2498-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c2498-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="c2498-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c2498-137">Zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="c2498-137">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="c2498-138">Uvolňování paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="c2498-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
