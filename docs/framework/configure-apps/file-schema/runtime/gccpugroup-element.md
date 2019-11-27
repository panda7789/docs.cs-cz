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
# <a name="gccpugroup-element"></a><span data-ttu-id="ca26a-102">\<element > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="ca26a-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="ca26a-103">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ca26a-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="ca26a-104">[**konfigurační >\<** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca26a-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ca26a-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="ca26a-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="ca26a-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**</span><span class="sxs-lookup"><span data-stu-id="ca26a-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>

## <a name="syntax"></a><span data-ttu-id="ca26a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca26a-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ca26a-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ca26a-108">Attributes and Elements</span></span>

<span data-ttu-id="ca26a-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ca26a-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ca26a-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="ca26a-110">Attributes</span></span>

|<span data-ttu-id="ca26a-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="ca26a-111">Attribute</span></span>|<span data-ttu-id="ca26a-112">Popis</span><span class="sxs-lookup"><span data-stu-id="ca26a-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ca26a-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="ca26a-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="ca26a-114">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ca26a-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ca26a-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="ca26a-115">enabled Attribute</span></span>

|<span data-ttu-id="ca26a-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca26a-116">Value</span></span>|<span data-ttu-id="ca26a-117">Popis</span><span class="sxs-lookup"><span data-stu-id="ca26a-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="ca26a-118">Uvolňování paměti nepodporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ca26a-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="ca26a-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="ca26a-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="ca26a-120">Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="ca26a-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ca26a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ca26a-121">Child Elements</span></span>

<span data-ttu-id="ca26a-122">Žádné.</span><span class="sxs-lookup"><span data-stu-id="ca26a-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ca26a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ca26a-123">Parent Elements</span></span>

|<span data-ttu-id="ca26a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="ca26a-124">Element</span></span>|<span data-ttu-id="ca26a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="ca26a-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ca26a-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ca26a-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ca26a-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="ca26a-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ca26a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca26a-128">Remarks</span></span>

<span data-ttu-id="ca26a-129">Pokud je v počítači více skupin PROCESORů a uvolňování paměti serveru (viz [\<gcServer >](gcserver-element.md) element), povolením tohoto elementu dojde k rozšíření uvolňování paměti napříč všemi skupinami CPU a při vytváření a vyrovnávání hald budou brát v úvahu všechny jádra.</span><span class="sxs-lookup"><span data-stu-id="ca26a-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="ca26a-130">Tento prvek se vztahuje pouze na vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ca26a-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="ca26a-131">Chcete-li povolit modulu runtime pro distribuci uživatelských vláken napříč všemi skupinami PROCESORů, je nutné povolit také [\<Thread_UseAllCpuGroups >](thread-useallcpugroups-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="ca26a-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="ca26a-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="ca26a-132">Example</span></span>

<span data-ttu-id="ca26a-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="ca26a-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ca26a-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ca26a-134">See also</span></span>

- [<span data-ttu-id="ca26a-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="ca26a-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ca26a-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="ca26a-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ca26a-137">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="ca26a-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="ca26a-138">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="ca26a-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation-and-server-garbage-collection)
