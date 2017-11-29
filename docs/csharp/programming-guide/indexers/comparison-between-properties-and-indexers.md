---
title: "Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 102a6a97726fa19fcba0e6f19876a3935e8625f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="84ef1-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="84ef1-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="84ef1-103">Indexery jsou stejné jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="84ef1-103">Indexers are like properties.</span></span> <span data-ttu-id="84ef1-104">S výjimkou rozdíly uvedené v následující tabulce všechna pravidla, které jsou definovány pro vlastnost přístupových objektů týkají přístupové objekty indexer také.</span><span class="sxs-lookup"><span data-stu-id="84ef1-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="84ef1-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="84ef1-105">Property</span></span>|<span data-ttu-id="84ef1-106">indexer</span><span class="sxs-lookup"><span data-stu-id="84ef1-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="84ef1-107">Umožňuje metody, která se má volat, jako kdyby byly členy veřejná data.</span><span class="sxs-lookup"><span data-stu-id="84ef1-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="84ef1-108">Umožňuje elementy vnitřní objekt nelze přistupovat pomocí notace pole na samotný objekt kolekce.</span><span class="sxs-lookup"><span data-stu-id="84ef1-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="84ef1-109">Přistupovat prostřednictvím jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="84ef1-109">Accessed through a simple name.</span></span>|<span data-ttu-id="84ef1-110">Dostupné v indexu.</span><span class="sxs-lookup"><span data-stu-id="84ef1-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="84ef1-111">Může být statické nebo instanci členu.</span><span class="sxs-lookup"><span data-stu-id="84ef1-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="84ef1-112">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="84ef1-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="84ef1-113">A [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="84ef1-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="84ef1-114">A `get` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru.</span><span class="sxs-lookup"><span data-stu-id="84ef1-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="84ef1-115">A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="84ef1-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="84ef1-116">A `set` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="84ef1-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="84ef1-117">Podporuje zkrácený syntax s [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="84ef1-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="84ef1-118">Nepodporuje zkrácenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="84ef1-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84ef1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="84ef1-119">See Also</span></span>  
 [<span data-ttu-id="84ef1-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="84ef1-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="84ef1-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="84ef1-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="84ef1-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="84ef1-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
