---
title: Postup inicializace objektů pomocí inicializátoru objektu – Průvodce programováním v C#
description: Naučte se používat Inicializátory objektů k inicializaci typů objektů v jazyce C# bez vyvolání konstruktoru. Použijte inicializátor objektu pro definování anonymního typu.
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 0781b168b0ae8b8383affe19d2721da67f662045
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865031"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="38ac4-104">Postup inicializace objektů pomocí inicializátoru objektu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="38ac4-104">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="38ac4-105">Inicializátory objektů můžete použít k inicializaci typu objektů deklarativním způsobem bez explicitního vyvolání konstruktoru pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="38ac4-105">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="38ac4-106">Následující příklady ukazují, jak používat Inicializátory objektů s pojmenovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="38ac4-106">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="38ac4-107">Kompilátor zpracovává Inicializátory objektů, protože nejprve přistupuje k výchozímu konstruktoru instance a pak zpracovává inicializace členů.</span><span class="sxs-lookup"><span data-stu-id="38ac4-107">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="38ac4-108">Proto pokud je konstruktor bez parametrů deklarován jako `private` ve třídě, Inicializátory objektů, které vyžadují veřejný přístup, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="38ac4-108">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="38ac4-109">Je nutné použít inicializátor objektu, pokud definujete anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="38ac4-109">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="38ac4-110">Další informace naleznete v tématu [jak vracet podmnožiny vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="38ac4-110">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="38ac4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="38ac4-111">Example</span></span>  

<span data-ttu-id="38ac4-112">Následující příklad ukazuje, jak inicializovat nový `StudentName` typ pomocí inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="38ac4-112">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="38ac4-113">Tento příklad nastaví vlastnosti v `StudentName` typu:</span><span class="sxs-lookup"><span data-stu-id="38ac4-113">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="38ac4-114">Inicializátory objektů lze použít k nastavení indexerů v objektu.</span><span class="sxs-lookup"><span data-stu-id="38ac4-114">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="38ac4-115">Následující příklad definuje `BaseballTeam` třídu, která používá indexer k získání a nastavení hráčů na různých pozicích.</span><span class="sxs-lookup"><span data-stu-id="38ac4-115">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="38ac4-116">Inicializátor může přiřadit přehrávače na základě zkratky pro pozici nebo čísla používaného pro všechny baseballové Scorecardy na pozici:</span><span class="sxs-lookup"><span data-stu-id="38ac4-116">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="38ac4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="38ac4-117">See also</span></span>

- [<span data-ttu-id="38ac4-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="38ac4-118">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="38ac4-119">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="38ac4-119">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
