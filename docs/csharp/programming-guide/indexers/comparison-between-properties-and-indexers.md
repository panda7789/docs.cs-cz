---
title: Porovnání mezi vlastnostmi a indexery – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 330d222083ce599719698c023803196dfe88da84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712127"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="f92a2-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="f92a2-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="f92a2-103">Indexery jsou jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f92a2-103">Indexers are like properties.</span></span> <span data-ttu-id="f92a2-104">S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.</span><span class="sxs-lookup"><span data-stu-id="f92a2-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="f92a2-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f92a2-105">Property</span></span>|<span data-ttu-id="f92a2-106">Indexer</span><span class="sxs-lookup"><span data-stu-id="f92a2-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f92a2-107">Povoluje volání metod, jako by šlo o veřejné datové členy.</span><span class="sxs-lookup"><span data-stu-id="f92a2-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="f92a2-108">Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.</span><span class="sxs-lookup"><span data-stu-id="f92a2-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="f92a2-109">Je k dispozici prostřednictvím jednoduchého názvu.</span><span class="sxs-lookup"><span data-stu-id="f92a2-109">Accessed through a simple name.</span></span>|<span data-ttu-id="f92a2-110">Je k dispozici prostřednictvím indexu.</span><span class="sxs-lookup"><span data-stu-id="f92a2-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="f92a2-111">Může být statický nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="f92a2-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="f92a2-112">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="f92a2-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="f92a2-113">Přístupový objekt [Get](../../language-reference/keywords/get.md) vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="f92a2-113">A [get](../../language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="f92a2-114">Přístupový objekt `get` indexeru má stejný seznam formálních parametrů jako indexer.</span><span class="sxs-lookup"><span data-stu-id="f92a2-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="f92a2-115">Přístupový objekt [set](../../language-reference/keywords/set.md) vlastnosti obsahuje implicitní parametr `value`.</span><span class="sxs-lookup"><span data-stu-id="f92a2-115">A [set](../../language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="f92a2-116">Přístupový objekt `set` indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value](../../language-reference/keywords/value.md) .</span><span class="sxs-lookup"><span data-stu-id="f92a2-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="f92a2-117">Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="f92a2-117">Supports shortened syntax with [Auto-Implemented Properties](../classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="f92a2-118">Podporuje členy Expression těle pro získání pouze indexerů.</span><span class="sxs-lookup"><span data-stu-id="f92a2-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f92a2-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f92a2-119">See also</span></span>

- [<span data-ttu-id="f92a2-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f92a2-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f92a2-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="f92a2-121">Indexers</span></span>](./index.md)
- [<span data-ttu-id="f92a2-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f92a2-122">Properties</span></span>](../classes-and-structs/properties.md)
