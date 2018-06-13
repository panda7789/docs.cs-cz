---
title: Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: a8b347be33ea6acbdf8a78a7af45fd3d0c27f8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33330369"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="2d922-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2d922-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="2d922-103">Indexery jsou stejné jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2d922-103">Indexers are like properties.</span></span> <span data-ttu-id="2d922-104">S výjimkou rozdíly uvedené v následující tabulce všechna pravidla, které jsou definovány pro vlastnost přístupových objektů týkají přístupové objekty indexer také.</span><span class="sxs-lookup"><span data-stu-id="2d922-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="2d922-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2d922-105">Property</span></span>|<span data-ttu-id="2d922-106">indexer</span><span class="sxs-lookup"><span data-stu-id="2d922-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2d922-107">Umožňuje metody, která se má volat, jako kdyby byly členy veřejná data.</span><span class="sxs-lookup"><span data-stu-id="2d922-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="2d922-108">Umožňuje elementy vnitřní objekt nelze přistupovat pomocí notace pole na samotný objekt kolekce.</span><span class="sxs-lookup"><span data-stu-id="2d922-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="2d922-109">Přistupovat prostřednictvím jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="2d922-109">Accessed through a simple name.</span></span>|<span data-ttu-id="2d922-110">Dostupné v indexu.</span><span class="sxs-lookup"><span data-stu-id="2d922-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="2d922-111">Může být statické nebo instanci členu.</span><span class="sxs-lookup"><span data-stu-id="2d922-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="2d922-112">Musí být členem instance.</span><span class="sxs-lookup"><span data-stu-id="2d922-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="2d922-113">A [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="2d922-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="2d922-114">A `get` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru.</span><span class="sxs-lookup"><span data-stu-id="2d922-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="2d922-115">A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametr.</span><span class="sxs-lookup"><span data-stu-id="2d922-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="2d922-116">A `set` přístupových indexer obsahuje stejný seznam formální parametr jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="2d922-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="2d922-117">Podporuje zkrácený syntax s [Auto-Implemented vlastnosti](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2d922-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="2d922-118">Nepodporuje zkrácenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="2d922-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d922-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d922-119">See Also</span></span>  
 [<span data-ttu-id="2d922-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2d922-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2d922-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="2d922-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="2d922-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2d922-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
