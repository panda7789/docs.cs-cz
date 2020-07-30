---
title: Porovnání mezi vlastnostmi a indexery – Průvodce programováním v C#
description: Porovnejte, jak Indexery v jazyce C# jsou jako vlastnosti. S výjimkou některých rozdílů se pravidla definovaná pro přistupující objekty vlastnosti vztahují na přistupující objekty indexeru.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: b83ce3db3d4b53fb7bcc5f3b3cd603a375d5d473
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299172"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="b6c86-104">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="b6c86-104">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="b6c86-105">Indexery jsou jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6c86-105">Indexers are like properties.</span></span> <span data-ttu-id="b6c86-106">S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.</span><span class="sxs-lookup"><span data-stu-id="b6c86-106">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="b6c86-107">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b6c86-107">Property</span></span>|<span data-ttu-id="b6c86-108">Indexer</span><span class="sxs-lookup"><span data-stu-id="b6c86-108">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="b6c86-109">Povoluje volání metod, jako by šlo o veřejné datové členy.</span><span class="sxs-lookup"><span data-stu-id="b6c86-109">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="b6c86-110">Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.</span><span class="sxs-lookup"><span data-stu-id="b6c86-110">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="b6c86-111">Je k dispozici prostřednictvím jednoduchého názvu.</span><span class="sxs-lookup"><span data-stu-id="b6c86-111">Accessed through a simple name.</span></span>|<span data-ttu-id="b6c86-112">Je k dispozici prostřednictvím indexu.</span><span class="sxs-lookup"><span data-stu-id="b6c86-112">Accessed through an index.</span></span>|  
|<span data-ttu-id="b6c86-113">Může být statický nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="b6c86-113">Can be a static or an instance member.</span></span>|<span data-ttu-id="b6c86-114">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="b6c86-114">Must be an instance member.</span></span>|  
|<span data-ttu-id="b6c86-115">Přístupový objekt [Get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="b6c86-115">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="b6c86-116">`get`Přistupující objekt indexeru má stejný seznam formálních parametrů jako indexer.</span><span class="sxs-lookup"><span data-stu-id="b6c86-116">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="b6c86-117">Přístupový objekt [set](../../language-reference/keywords/set.md) vlastnosti obsahuje implicitní `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="b6c86-117">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="b6c86-118">`set`Přistupující objekt indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value](../../language-reference/keywords/value.md) .</span><span class="sxs-lookup"><span data-stu-id="b6c86-118">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="b6c86-119">Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b6c86-119">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="b6c86-120">Podporuje členy Expression těle pro získání pouze indexerů.</span><span class="sxs-lookup"><span data-stu-id="b6c86-120">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b6c86-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6c86-121">See also</span></span>

- [<span data-ttu-id="b6c86-122">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="b6c86-122">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b6c86-123">Indexery</span><span class="sxs-lookup"><span data-stu-id="b6c86-123">Indexers</span></span>](./index.md)
- [<span data-ttu-id="b6c86-124">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b6c86-124">Properties</span></span>](../classes-and-structs/properties.md)
