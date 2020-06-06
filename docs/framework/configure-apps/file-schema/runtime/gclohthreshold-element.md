---
title: Element GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74451218"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="e4a79-102">Element GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="e4a79-102">GCLOHThreshold element</span></span>

<span data-ttu-id="e4a79-103">Určuje velikost prahové hodnoty v bajtech, která způsobí, že systém uvolňování paměti vloží objekty do haldy velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="e4a79-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<runtime>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold>

## <a name="syntax"></a><span data-ttu-id="e4a79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a79-104">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="e4a79-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="e4a79-105">Attributes</span></span>

|<span data-ttu-id="e4a79-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="e4a79-106">Attribute</span></span>|<span data-ttu-id="e4a79-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e4a79-107">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="e4a79-108">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="e4a79-108">Required attribute.</span></span><br /><br /><span data-ttu-id="e4a79-109">Určuje velikost prahové hodnoty, která způsobí, že objekty přejdou na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-109">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="e4a79-110">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="e4a79-110">enabled attribute</span></span>

|<span data-ttu-id="e4a79-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e4a79-111">Value</span></span>|<span data-ttu-id="e4a79-112">Description</span><span class="sxs-lookup"><span data-stu-id="e4a79-112">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="e4a79-113">Velikost prahové hodnoty (v bajtech), která způsobí, že objekty přejdou na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="e4a79-113">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="e4a79-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="e4a79-114">Child elements</span></span>

<span data-ttu-id="e4a79-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="e4a79-115">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="e4a79-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="e4a79-116">Parent elements</span></span>

|<span data-ttu-id="e4a79-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="e4a79-117">Element</span></span>|<span data-ttu-id="e4a79-118">Description</span><span class="sxs-lookup"><span data-stu-id="e4a79-118">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="e4a79-119">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4a79-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="e4a79-120">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="e4a79-120">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e4a79-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4a79-121">Remarks</span></span>

<span data-ttu-id="e4a79-122">Toto nastavení bylo zavedeno v .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="e4a79-122">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="e4a79-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4a79-123">See also</span></span>

- [<span data-ttu-id="e4a79-124">Schéma nastavení běhového prostředí</span><span class="sxs-lookup"><span data-stu-id="e4a79-124">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="e4a79-125">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e4a79-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="e4a79-126">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="e4a79-126">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="e4a79-127">Možnosti konfigurace NET Core Runtime pro GC</span><span class="sxs-lookup"><span data-stu-id="e4a79-127">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
