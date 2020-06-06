---
title: Element <GCCpuGroup>
ms.date: 03/30/2017
helpviewer_keywords:
- GCCpuGroup element
- <GCCpuGroup> element
ms.assetid: c1fc7d6c-7220-475c-a312-5b8b201f66e0
ms.openlocfilehash: f1cbe5a7109d6e4aae2e92710920a1c6b3a40d00
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "82102889"
---
# <a name="gccpugroup-element"></a><span data-ttu-id="97753-102">Element \<GCCpuGroup></span><span class="sxs-lookup"><span data-stu-id="97753-102">\<GCCpuGroup> Element</span></span>

<span data-ttu-id="97753-103">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="97753-103">Specifies whether garbage collection supports multiple CPU groups.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<GCCpuGroup>**

## <a name="syntax"></a><span data-ttu-id="97753-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="97753-104">Syntax</span></span>

```xml
<GCCpuGroup
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="97753-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="97753-105">Attributes and Elements</span></span>

<span data-ttu-id="97753-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="97753-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="97753-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="97753-107">Attributes</span></span>

|<span data-ttu-id="97753-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="97753-108">Attribute</span></span>|<span data-ttu-id="97753-109">Popis</span><span class="sxs-lookup"><span data-stu-id="97753-109">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="97753-110">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="97753-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="97753-111">Určuje, zda uvolňování paměti podporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="97753-111">Specifies whether garbage collection supports multiple CPU groups.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="97753-112">Atribut enabled</span><span class="sxs-lookup"><span data-stu-id="97753-112">enabled Attribute</span></span>

|<span data-ttu-id="97753-113">Hodnota</span><span class="sxs-lookup"><span data-stu-id="97753-113">Value</span></span>|<span data-ttu-id="97753-114">Description</span><span class="sxs-lookup"><span data-stu-id="97753-114">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="97753-115">Uvolňování paměti nepodporuje více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="97753-115">Garbage collection does not support multiple CPU groups.</span></span> <span data-ttu-id="97753-116">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="97753-116">This is the default.</span></span>|
|`true`|<span data-ttu-id="97753-117">Uvolňování paměti podporuje více skupin PROCESORů, pokud je povoleno shromažďování paměti serveru.</span><span class="sxs-lookup"><span data-stu-id="97753-117">Garbage collection supports multiple CPU groups, if server garbage collection is enabled.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="97753-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="97753-118">Child Elements</span></span>

<span data-ttu-id="97753-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="97753-119">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="97753-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="97753-120">Parent Elements</span></span>

|<span data-ttu-id="97753-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="97753-121">Element</span></span>|<span data-ttu-id="97753-122">Description</span><span class="sxs-lookup"><span data-stu-id="97753-122">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="97753-123">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="97753-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="97753-124">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="97753-124">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="97753-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="97753-125">Remarks</span></span>

<span data-ttu-id="97753-126">Pokud je v počítači více skupin PROCESORů a uvolňování paměti serveru (viz [\<gcServer>](gcserver-element.md) element), povolením tohoto elementu dojde k rozšíření uvolňování paměti napříč všemi skupinami procesorů a při vytváření a vyrovnávání hald budou brát v úvahu všechny jádra.</span><span class="sxs-lookup"><span data-stu-id="97753-126">When a computer has multiple CPU groups and server garbage collection is enabled (see the [\<gcServer>](gcserver-element.md) element), enabling this element extends garbage collection across all CPU groups and takes all cores into account when creating and balancing heaps.</span></span>

> [!NOTE]
> <span data-ttu-id="97753-127">Tento prvek se vztahuje pouze na vlákna uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="97753-127">This element applies only to garbage collection threads.</span></span> <span data-ttu-id="97753-128">Chcete-li povolit modulu runtime pro distribuci uživatelských vláken napříč všemi skupinami CPU, je nutné povolit také [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="97753-128">To enable the runtime to distribute user threads across all CPU groups, you must also enable the [\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md) element.</span></span>

## <a name="example"></a><span data-ttu-id="97753-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="97753-129">Example</span></span>

<span data-ttu-id="97753-130">Následující příklad ukazuje, jak povolit uvolňování paměti pro více skupin PROCESORů.</span><span class="sxs-lookup"><span data-stu-id="97753-130">The following example shows how to enable garbage collection for multiple CPU groups.</span></span>

```xml
<configuration>
   <runtime>
      <GCCpuGroup enabled="true"/>
      <gcServer enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="97753-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="97753-131">See also</span></span>

- [<span data-ttu-id="97753-132">Schéma nastavení modulu runtime</span><span class="sxs-lookup"><span data-stu-id="97753-132">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="97753-133">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="97753-133">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="97753-134">Zakázat souběžné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="97753-134">Disable concurrent garbage collection</span></span>](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [<span data-ttu-id="97753-135">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="97753-135">Workstation and server garbage collection</span></span>](../../../../standard/garbage-collection/workstation-server-gc.md)
