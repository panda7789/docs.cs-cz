---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: ae9c96c9d49cf3f6be94da3f77b91423cab12e0b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430477"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="b8343-102">\<GCCpuGroup> Element</span><span class="sxs-lookup"><span data-stu-id="b8343-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="b8343-103">Specifies whether garbage collection supports multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="b8343-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="b8343-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8343-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8343-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8343-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b8343-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup>**</span><span class="sxs-lookup"><span data-stu-id="b8343-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b8343-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8343-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b8343-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-108">Attributes and Elements</span></span>

<span data-ttu-id="b8343-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8343-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b8343-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8343-110">Attributes</span></span>

|<span data-ttu-id="b8343-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b8343-111">Attribute</span></span>|<span data-ttu-id="b8343-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b8343-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="b8343-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="b8343-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="b8343-114">Specifies whether garbage collection supports multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="b8343-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="b8343-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="b8343-115">enabled Attribute</span></span>

|<span data-ttu-id="b8343-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="b8343-116">Value</span></span>|<span data-ttu-id="b8343-117">Popis</span><span class="sxs-lookup"><span data-stu-id="b8343-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="b8343-118">Garbage collection does not support multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="b8343-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="b8343-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="b8343-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="b8343-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span><span class="sxs-lookup"><span data-stu-id="b8343-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b8343-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-121">Child Elements</span></span>

<span data-ttu-id="b8343-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8343-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b8343-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8343-123">Parent Elements</span></span>

|<span data-ttu-id="b8343-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="b8343-124">Element</span></span>|<span data-ttu-id="b8343-125">Popis</span><span class="sxs-lookup"><span data-stu-id="b8343-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b8343-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8343-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="b8343-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="b8343-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b8343-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8343-128">Remarks</span></span>

<span data-ttu-id="b8343-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span><span class="sxs-lookup"><span data-stu-id="b8343-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="b8343-130">This element applies only to garbage collection threads.</span><span class="sxs-lookup"><span data-stu-id="b8343-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="b8343-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b8343-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="b8343-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8343-132">Example</span></span>

<span data-ttu-id="b8343-133">The following example shows how to enable garbage collection for multiple CPU groups.</span><span class="sxs-lookup"><span data-stu-id="b8343-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b8343-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8343-134">See also</span></span>

- [<span data-ttu-id="b8343-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="b8343-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b8343-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b8343-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b8343-137">To disable concurrent garbage collection</span><span class="sxs-lookup"><span data-stu-id="b8343-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="b8343-138">Workstation and server garbage collection</span><span class="sxs-lookup"><span data-stu-id="b8343-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
