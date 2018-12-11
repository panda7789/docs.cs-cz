---
title: Porovnání mezi vlastnostmi a indexery - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 053eb7ee0fe9333f049e5b4f8a8e709e42aa2119
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234458"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a><span data-ttu-id="dc5be-102">Porovnání mezi vlastnostmi a indexery (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dc5be-102">Comparison Between Properties and Indexers (C# Programming Guide)</span></span>
<span data-ttu-id="dc5be-103">Indexery jsou stejné jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dc5be-103">Indexers are like properties.</span></span> <span data-ttu-id="dc5be-104">S výjimkou rozdílů je znázorněno v následující tabulce všechna pravidla, které jsou definovány pro přistupující objekty vlastnosti platí pro přistupující objekty indexer také.</span><span class="sxs-lookup"><span data-stu-id="dc5be-104">Except for the differences shown in the following table, all the rules that are defined for property accessors apply to indexer accessors also.</span></span>  
  
|<span data-ttu-id="dc5be-105">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="dc5be-105">Property</span></span>|<span data-ttu-id="dc5be-106">Indexer</span><span class="sxs-lookup"><span data-stu-id="dc5be-106">Indexer</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="dc5be-107">Povoluje metody, která se má volat, jakoby byly veřejné datové členy.</span><span class="sxs-lookup"><span data-stu-id="dc5be-107">Allows methods to be called as if they were public data members.</span></span>|<span data-ttu-id="dc5be-108">Umožňuje elementy vnitřní objekt přistupovat pomocí zápisu pole na samotného objektu kolekce.</span><span class="sxs-lookup"><span data-stu-id="dc5be-108">Allows elements of an internal collection of an object to be accessed by using array notation on the object itself.</span></span>|  
|<span data-ttu-id="dc5be-109">Je možný přes jednoduchý název.</span><span class="sxs-lookup"><span data-stu-id="dc5be-109">Accessed through a simple name.</span></span>|<span data-ttu-id="dc5be-110">Přístup pomocí indexu.</span><span class="sxs-lookup"><span data-stu-id="dc5be-110">Accessed through an index.</span></span>|  
|<span data-ttu-id="dc5be-111">Může být statická nebo člena instance.</span><span class="sxs-lookup"><span data-stu-id="dc5be-111">Can be a static or an instance member.</span></span>|<span data-ttu-id="dc5be-112">Musí být člen instance.</span><span class="sxs-lookup"><span data-stu-id="dc5be-112">Must be an instance member.</span></span>|  
|<span data-ttu-id="dc5be-113">A [získat](../../../csharp/language-reference/keywords/get.md) přistupující objekt vlastnosti nemá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="dc5be-113">A [get](../../../csharp/language-reference/keywords/get.md) accessor of a property has no parameters.</span></span>|<span data-ttu-id="dc5be-114">A `get` stejného seznamu formálních parametrů jako indexeru má přistupující objekt indexeru.</span><span class="sxs-lookup"><span data-stu-id="dc5be-114">A `get` accessor of an indexer has the same formal parameter list as the indexer.</span></span>|  
|<span data-ttu-id="dc5be-115">A [nastavit](../../../csharp/language-reference/keywords/set.md) přistupující objekt vlastnosti obsahuje implicitní `value` parametru.</span><span class="sxs-lookup"><span data-stu-id="dc5be-115">A [set](../../../csharp/language-reference/keywords/set.md) accessor of a property contains the implicit `value` parameter.</span></span>|<span data-ttu-id="dc5be-116">A `set` přistupující objekt indexeru má stejného seznamu formálních parametrů jako indexeru a také [hodnotu](../../../csharp/language-reference/keywords/value.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="dc5be-116">A `set` accessor of an indexer has the same formal parameter list as the indexer, and also to the [value](../../../csharp/language-reference/keywords/value.md) parameter.</span></span>|  
|<span data-ttu-id="dc5be-117">Podporuje zkrátila syntaxe [implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="dc5be-117">Supports shortened syntax with [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>|<span data-ttu-id="dc5be-118">Nepodporuje zkrácený syntaxi.</span><span class="sxs-lookup"><span data-stu-id="dc5be-118">Does not support shortened syntax.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc5be-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc5be-119">See Also</span></span>

- [<span data-ttu-id="dc5be-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dc5be-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="dc5be-121">Indexery</span><span class="sxs-lookup"><span data-stu-id="dc5be-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="dc5be-122">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc5be-122">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
