---
title: Element GCLOHThreshold
ms.date: 11/20/2019
helpviewer_keywords:
- GCLOHThreshold element
- <GCLOHThreshold> element
ms.openlocfilehash: d72dc9d27984f60dfb6296217263ce8b176093c6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451218"
---
# <a name="gclohthreshold-element"></a><span data-ttu-id="1fe2d-102">Element GCLOHThreshold</span><span class="sxs-lookup"><span data-stu-id="1fe2d-102">GCLOHThreshold element</span></span>

<span data-ttu-id="1fe2d-103">Určuje velikost prahové hodnoty v bajtech, která způsobí, že systém uvolňování paměti vloží objekty do haldy velkých objektů (LOH).</span><span class="sxs-lookup"><span data-stu-id="1fe2d-103">Specifies the threshold size, in bytes, that causes the garbage collector to put objects on the large object heap (LOH).</span></span>

<span data-ttu-id="1fe2d-104">[konfigurační >\<](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1fe2d-104">[\<configuration>](../configuration-element.md)</span></span>\
<span data-ttu-id="1fe2d-105">&nbsp;&nbsp;[\<runtime >](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="1fe2d-105">&nbsp;&nbsp;[\<runtime>](runtime-element.md)</span></span>\
<span data-ttu-id="1fe2d-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold ></span><span class="sxs-lookup"><span data-stu-id="1fe2d-106">&nbsp;&nbsp;&nbsp;&nbsp;\<GCLOHThreshold></span></span>

## <a name="syntax"></a><span data-ttu-id="1fe2d-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fe2d-107">Syntax</span></span>

```xml
<GCLOHThreshold
   enabled="nnnn"/>
```

## <a name="attributes"></a><span data-ttu-id="1fe2d-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="1fe2d-108">Attributes</span></span>

|<span data-ttu-id="1fe2d-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="1fe2d-109">Attribute</span></span>|<span data-ttu-id="1fe2d-110">Popis</span><span class="sxs-lookup"><span data-stu-id="1fe2d-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="1fe2d-111">Požadovaný atribut.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-111">Required attribute.</span></span><br /><br /><span data-ttu-id="1fe2d-112">Určuje velikost prahové hodnoty, která způsobí, že objekty přejdou na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-112">Specifies the threshold size that causes objects to go on the large object heap.</span></span>|

### <a name="enabled-attribute"></a><span data-ttu-id="1fe2d-113">povolený atribut</span><span class="sxs-lookup"><span data-stu-id="1fe2d-113">enabled attribute</span></span>

|<span data-ttu-id="1fe2d-114">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1fe2d-114">Value</span></span>|<span data-ttu-id="1fe2d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1fe2d-115">Description</span></span>|
|-----------|-----------------|
|`nnnn`|<span data-ttu-id="1fe2d-116">Velikost prahové hodnoty (v bajtech), která způsobí, že objekty přejdou na haldu velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-116">The threshold size, in bytes, that causes objects to go on the large object heap.</span></span>|

## <a name="child-elements"></a><span data-ttu-id="1fe2d-117">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="1fe2d-117">Child elements</span></span>

<span data-ttu-id="1fe2d-118">Žádné.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-118">None.</span></span>

## <a name="parent-elements"></a><span data-ttu-id="1fe2d-119">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="1fe2d-119">Parent elements</span></span>

|<span data-ttu-id="1fe2d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="1fe2d-120">Element</span></span>|<span data-ttu-id="1fe2d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1fe2d-121">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="1fe2d-122">Kořenový prvek v každém konfiguračním souboru, který je používán modulem Common Language Runtime (CLR) a aplikacemi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="1fe2d-123">Obsahuje informace o vazbách sestavení a uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-123">Contains information about assembly binding and garbage collection.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1fe2d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1fe2d-124">Remarks</span></span>

<span data-ttu-id="1fe2d-125">Toto nastavení bylo zavedeno v .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="1fe2d-125">This setting was introduced in .NET Framework 4.8.</span></span>

## <a name="see-also"></a><span data-ttu-id="1fe2d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1fe2d-126">See also</span></span>

- [<span data-ttu-id="1fe2d-127">Schéma nastavení běhu</span><span class="sxs-lookup"><span data-stu-id="1fe2d-127">Run-time settings schema</span></span>](index.md)
- [<span data-ttu-id="1fe2d-128">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="1fe2d-128">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="1fe2d-129">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="1fe2d-129">Fundamentals of garbage collection</span></span>](../../../../standard/garbage-collection/fundamentals.md)
- [<span data-ttu-id="1fe2d-130">Možnosti konfigurace NET Core Runtime pro GC</span><span class="sxs-lookup"><span data-stu-id="1fe2d-130">NET Core run-time config options for GC</span></span>](../../../../core/run-time-config/garbage-collector.md)
