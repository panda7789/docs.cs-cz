---
title: Jak inicializovat objekty pomocí inicializačního systému objektu - Průvodce programováním jazyka C#
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: a2ecc9df211d0082bd4b413653e374758c877abc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705584"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="62fb0-102">Jak inicializovat objekty pomocí inicializačního zařízení objektu (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62fb0-102">How to initialize objects by using an object initializer (C# Programming Guide)</span></span>

<span data-ttu-id="62fb0-103">Inicializační metody objektu můžete použít k inicializaci objektů typu deklarativním způsobem bez explicitního vyvolání konstruktoru pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="62fb0-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="62fb0-104">Následující příklady ukazují, jak používat inicializační prvky objektu s pojmenovanými objekty.</span><span class="sxs-lookup"><span data-stu-id="62fb0-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="62fb0-105">Kompilátor zpracovává inicializátory objektů tak, že nejprve přistupuje k výchozímu konstruktoru instance a poté zpracovává inicializace členů.</span><span class="sxs-lookup"><span data-stu-id="62fb0-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="62fb0-106">Proto pokud konstruktor bez parametrů `private` je deklarován jako ve třídě, inicializátory objektu, které vyžadují veřejný přístup se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="62fb0-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="62fb0-107">Inicializátor objektu je nutné použít, pokud definujete anonymní typ.</span><span class="sxs-lookup"><span data-stu-id="62fb0-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="62fb0-108">Další informace naleznete v [tématu Jak vrátit podmnožiny vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="62fb0-108">For more information, see [How to return subsets of element properties in a query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62fb0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="62fb0-109">Example</span></span>  

<span data-ttu-id="62fb0-110">Následující příklad ukazuje, jak inicializovat nový `StudentName` typ pomocí inicializačních objektů.</span><span class="sxs-lookup"><span data-stu-id="62fb0-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="62fb0-111">Tento příklad nastaví `StudentName` vlastnosti v typu:</span><span class="sxs-lookup"><span data-stu-id="62fb0-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="62fb0-112">Inicializátory objektů lze použít k nastavení indexerů v objektu.</span><span class="sxs-lookup"><span data-stu-id="62fb0-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="62fb0-113">Následující příklad definuje `BaseballTeam` třídu, která používá indexer získat a nastavit hráče na různých pozicích.</span><span class="sxs-lookup"><span data-stu-id="62fb0-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="62fb0-114">Inicializátor může přiřadit hráče na základě zkratky pro pozici nebo číslo použité pro každou pozici baseballscorecards:</span><span class="sxs-lookup"><span data-stu-id="62fb0-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="62fb0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="62fb0-115">See also</span></span>

- [<span data-ttu-id="62fb0-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62fb0-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="62fb0-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="62fb0-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
