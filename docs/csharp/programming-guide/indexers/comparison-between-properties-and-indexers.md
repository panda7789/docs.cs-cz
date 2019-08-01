---
title: Porovnání mezi vlastnostmi a indexery – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 31e6b4b10a6ffec031a2e41a2bd16c843f802fb7
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671681"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="1650b-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1650b-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="1650b-103">Indexery jsou jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1650b-103">Indexers are like properties.</span></span> <span data-ttu-id="1650b-104">S výjimkou rozdílů uvedených v následující tabulce se všechna pravidla, která jsou definována pro přistupující objekty vlastnosti, vztahují také na přistupující objekty indexeru.</span><span class="sxs-lookup"><span data-stu-id="1650b-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="1650b-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="1650b-105">Property</span></span>|<span data-ttu-id="1650b-106">Indexer</span><span class="sxs-lookup"><span data-stu-id="1650b-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="1650b-107">Povoluje volání metod, jako by šlo o veřejné datové členy.</span><span class="sxs-lookup"><span data-stu-id="1650b-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="1650b-108">Povoluje prvky interní kolekce objektu, které jsou k dispozici pomocí zápisu pole u objektu samotného.</span><span class="sxs-lookup"><span data-stu-id="1650b-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="1650b-109">Je k dispozici prostřednictvím jednoduchého názvu.</span><span class="sxs-lookup"><span data-stu-id="1650b-109">Accessed through a simple name.</span></span>|<span data-ttu-id="1650b-110">Je k dispozici prostřednictvím indexu.</span><span class="sxs-lookup"><span data-stu-id="1650b-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="1650b-111">Může být statický nebo členem instance.</span><span class="sxs-lookup"><span data-stu-id="1650b-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="1650b-112">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="1650b-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="1650b-113">Přístupový objekt [Get](../../../csharp/language-reference/keywords/get.md) vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="1650b-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="1650b-114">`get` Přistupující objekt indexeru má stejný seznam formálních parametrů jako indexer.</span><span class="sxs-lookup"><span data-stu-id="1650b-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="1650b-115">Přístupový objekt [set](../../../csharp/language-reference/keywords/set.md) vlastnosti obsahuje implicitní `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="1650b-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="1650b-116">Přistupující objekt indexeru má stejný formální seznam parametrů jako indexer a také parametr [Value.](../../../csharp/language-reference/keywords/value.md) `set`</span><span class="sxs-lookup"><span data-stu-id="1650b-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="1650b-117">Podporuje zkrácenou syntaxi s [automaticky implementovanými vlastnostmi](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="1650b-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="1650b-118">Podporuje členy Expression těle pro získání pouze indexerů.</span><span class="sxs-lookup"><span data-stu-id="1650b-118">Supports expression bodied members for get only indexers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1650b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1650b-119">See also</span></span>

- [<span data-ttu-id="1650b-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1650b-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1650b-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="1650b-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="1650b-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1650b-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
