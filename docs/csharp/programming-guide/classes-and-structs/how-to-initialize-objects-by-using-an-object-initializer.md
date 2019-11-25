---
title: Postup inicializace objektů pomocí inicializátoru objektu – C# Průvodce programováním
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: be555688a645c7689e76b5b4499c44255c18dbc8
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970881"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="009f8-102">Postup inicializace objektů pomocí inicializátoru objektu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="009f8-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="009f8-103">Inicializátory objektů můžete použít k inicializaci typu objektů deklarativním způsobem bez explicitního vyvolání konstruktoru pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="009f8-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="009f8-104">Následující příklady ukazují, jak používat Inicializátory objektů s pojmenovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="009f8-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="009f8-105">Kompilátor zpracovává Inicializátory objektů, protože nejprve přistupuje k výchozímu konstruktoru instance a pak zpracovává inicializace členů.</span><span class="sxs-lookup"><span data-stu-id="009f8-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="009f8-106">Proto pokud je konstruktor bez parametrů deklarován jako `private` ve třídě, Inicializátory objektů, které vyžadují veřejný přístup, se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="009f8-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="009f8-107">Je nutné použít inicializátor objektu, pokud definujete anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="009f8-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="009f8-108">Další informace naleznete v tématu [jak vracet podmnožiny vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="009f8-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="009f8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="009f8-109">Example</span></span>  

<span data-ttu-id="009f8-110">Následující příklad ukazuje, jak inicializovat nový typ `StudentName` pomocí inicializátorů objektů.</span><span class="sxs-lookup"><span data-stu-id="009f8-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="009f8-111">Tento příklad nastaví vlastnosti v typu `StudentName`:</span><span class="sxs-lookup"><span data-stu-id="009f8-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="009f8-112">Inicializátory objektů lze použít k nastavení indexerů v objektu.</span><span class="sxs-lookup"><span data-stu-id="009f8-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="009f8-113">Následující příklad definuje třídu `BaseballTeam`, která používá indexer k získání a nastavení hráčů na různých pozicích.</span><span class="sxs-lookup"><span data-stu-id="009f8-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="009f8-114">Inicializátor může přiřadit přehrávače na základě zkratky pro pozici nebo čísla používaného pro všechny baseballové Scorecardy na pozici:</span><span class="sxs-lookup"><span data-stu-id="009f8-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="009f8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="009f8-115">See also</span></span>

- [<span data-ttu-id="009f8-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="009f8-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="009f8-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="009f8-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
