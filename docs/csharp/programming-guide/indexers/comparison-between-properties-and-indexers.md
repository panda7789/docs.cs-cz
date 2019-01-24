---
title: Porovnání mezi vlastnostmi a indexery - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 41b27905edb8a0e00a6af5a4cce38988161326d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537722"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="2976a-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2976a-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="2976a-103">Indexery jsou stejné jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2976a-103">Indexers are like properties.</span></span> <span data-ttu-id="2976a-104">S výjimkou rozdílů je znázorněno v následující tabulce všechna pravidla, které jsou definovány pro přistupující objekty vlastnosti platí pro přistupující objekty indexer také.</span><span class="sxs-lookup"><span data-stu-id="2976a-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="2976a-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2976a-105">Property</span></span>|<span data-ttu-id="2976a-106">Indexer</span><span class="sxs-lookup"><span data-stu-id="2976a-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2976a-107">Povoluje metody, která se má volat, jakoby byly veřejné datové členy.</span><span class="sxs-lookup"><span data-stu-id="2976a-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="2976a-108">Umožňuje elementy vnitřní objekt přistupovat pomocí zápisu pole na samotného objektu kolekce.</span><span class="sxs-lookup"><span data-stu-id="2976a-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="2976a-109">Je možný přes jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="2976a-109">Accessed through a simple name.</span></span>|<span data-ttu-id="2976a-110">Přístup pomocí indexu.</span><span class="sxs-lookup"><span data-stu-id="2976a-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="2976a-111">Může být statická nebo člena instance.</span><span class="sxs-lookup"><span data-stu-id="2976a-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="2976a-112">Musí být člen instance.</span><span class="sxs-lookup"><span data-stu-id="2976a-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="2976a-113">A [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="2976a-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="2976a-114">A `get` stejného seznamu formálních parametrů jako indexeru má přistupující objekt indexeru.</span><span class="sxs-lookup"><span data-stu-id="2976a-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="2976a-115">A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="2976a-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="2976a-116">A `set` přistupující objekt indexeru má stejného seznamu formálních parametrů jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="2976a-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="2976a-117">Podporuje zkrátila syntaxe [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2976a-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="2976a-118">Nepodporuje zkrácený syntaxi.</span><span class="sxs-lookup"><span data-stu-id="2976a-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2976a-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2976a-119">See also</span></span>

- [<span data-ttu-id="2976a-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2976a-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2976a-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="2976a-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="2976a-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2976a-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
