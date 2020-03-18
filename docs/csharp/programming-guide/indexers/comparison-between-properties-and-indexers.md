---
title: Porovnání vlastností a indexerů – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712127"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="d8b67-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d8b67-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="d8b67-103">Indexery jsou jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d8b67-103">Indexers are like properties.</span></span> <span data-ttu-id="d8b67-104">S výjimkou rozdílů uvedených v následující tabulce platí všechna pravidla, která jsou definována pro přístupové objekty vlastností také pro přístupové objekty indexeru.</span><span class="sxs-lookup"><span data-stu-id="d8b67-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="d8b67-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="d8b67-105">Property</span></span>|<span data-ttu-id="d8b67-106">Indexer</span><span class="sxs-lookup"><span data-stu-id="d8b67-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="d8b67-107">Umožňuje metody, které mají být volány, jako by byly členy veřejných dat.</span><span class="sxs-lookup"><span data-stu-id="d8b67-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="d8b67-108">Umožňuje prvky vnitřní kolekce objektu, které mají být přístupné pomocí zápisu pole na samotný objekt.</span><span class="sxs-lookup"><span data-stu-id="d8b67-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="d8b67-109">Přístup prostřednictvím jednoduchého názvu.</span><span class="sxs-lookup"><span data-stu-id="d8b67-109">Accessed through a simple name.</span></span>|<span data-ttu-id="d8b67-110">Přístup prostřednictvím indexu.</span><span class="sxs-lookup"><span data-stu-id="d8b67-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="d8b67-111">Může být statický nebo člen instance.</span><span class="sxs-lookup"><span data-stu-id="d8b67-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="d8b67-112">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="d8b67-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="d8b67-113">Přístupový [objekt get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="d8b67-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="d8b67-114">Přistupující `get` objekt indexeru má stejný seznam formálních parametrů jako indexer.</span><span class="sxs-lookup"><span data-stu-id="d8b67-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="d8b67-115">Set [set](../../language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="d8b67-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="d8b67-116">Přistupující `set` objekt indexeru má stejný seznam formálních parametrů jako indexer a také parametr [hodnoty.](../../language-reference/keywords/value.md)</span><span class="sxs-lookup"><span data-stu-id="d8b67-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="d8b67-117">Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d8b67-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="d8b67-118">Podporuje výraz tělesně členy pro získat pouze indexery.</span><span class="sxs-lookup"><span data-stu-id="d8b67-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8b67-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8b67-119">See also</span></span>

- [<span data-ttu-id="d8b67-120">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d8b67-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d8b67-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="d8b67-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="d8b67-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d8b67-122">Properties</span></span>](../classes-and-structs/properties.md)
