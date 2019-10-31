---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: 352890519c1a227d664d877c3123866e5e4e1657
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116834"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="54fd3-102">\<element > GCCpuGroup</span><span class="sxs-lookup"><span data-stu-id="54fd3-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="54fd3-103">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="54fd3-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

<span data-ttu-id="54fd3-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="54fd3-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="54fd3-105">&nbsp;&nbsp;[ **\<runtime >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="54fd3-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="54fd3-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<GCCpuGroup >**</span><span class="sxs-lookup"><span data-stu-id="54fd3-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="54fd3-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54fd3-107">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="54fd3-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54fd3-108">Attributes and Elements</span></span>

<span data-ttu-id="54fd3-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54fd3-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="54fd3-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="54fd3-110">Attributes</span></span>

|<span data-ttu-id="54fd3-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="54fd3-111">Attribute</span></span>|<span data-ttu-id="54fd3-112">Popis</span><span class="sxs-lookup"><span data-stu-id="54fd3-112">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="54fd3-113">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="54fd3-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="54fd3-114">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="54fd3-114">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="54fd3-115">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="54fd3-115">enabled Attribute</span></span>

|<span data-ttu-id="54fd3-116">Hodnota</span><span class="sxs-lookup"><span data-stu-id="54fd3-116">Value</span></span>|<span data-ttu-id="54fd3-117">Popis</span><span class="sxs-lookup"><span data-stu-id="54fd3-117">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="54fd3-118">Uvolňování paměti nepodporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="54fd3-118">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="54fd3-119">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="54fd3-119">This is the default.</span></span>|
|`true`|<span data-ttu-id="54fd3-120">Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="54fd3-120">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="54fd3-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54fd3-121">Child Elements</span></span>

<span data-ttu-id="54fd3-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="54fd3-122">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="54fd3-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54fd3-123">Parent Elements</span></span>

|<span data-ttu-id="54fd3-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="54fd3-124">Element</span></span>|<span data-ttu-id="54fd3-125">Popis</span><span class="sxs-lookup"><span data-stu-id="54fd3-125">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="54fd3-126">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="54fd3-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="54fd3-127">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="54fd3-127">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54fd3-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54fd3-128">Remarks</span></span>

<span data-ttu-id="54fd3-129">Pokud je v počítači více skupin PROCESORů a uvolňování paměti serveru (viz [\<gcServer >](gcserver-element.md) element), povolení tohoto elementu rozšiřuje uvolňování paměti napříč všemi skupinami CPU a při vytváření a zabere všechny jádra do účtu. vyvážení hald.</span><span class="sxs-lookup"><span data-stu-id="54fd3-129">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="54fd3-130">Tento prvek se vztahuje pouze na vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="54fd3-130">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="54fd3-131">Chcete-li modulu runtime povolit distribuci uživatelských vláken napříč všemi skupinami CPU, je nutné povolit také [\<prvek > Thread_UseAllCpuGroups](thread-useallcpugroups-element.md) .</span><span class="sxs-lookup"><span data-stu-id="54fd3-131">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="54fd3-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="54fd3-132">Example</span></span>

<span data-ttu-id="54fd3-133">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="54fd3-133">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="54fd3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54fd3-134">See also</span></span>

- [<span data-ttu-id="54fd3-135">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="54fd3-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="54fd3-136">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="54fd3-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="54fd3-137">Zakázání souběžného uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="54fd3-137">To disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="54fd3-138">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="54fd3-138">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md#workstation_and_server_garbage_collection)
