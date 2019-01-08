---
title: 'Postupy: Inicializace objektů pomocí objektu inicializátoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 29987b9ba1f1f18f4e768766bd2391ebb5862f97
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084872"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="828f8-102">Postupy: Inicializace objektů pomocí inicializátoru objektů (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="828f8-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="828f8-103">Inicializátory objektů můžete použít třeba inicializovat objekty typu bez explicitní volání konstruktoru pro typ deklarativní způsobem.</span><span class="sxs-lookup"><span data-stu-id="828f8-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="828f8-104">Následující příklady ukazují, jak používat inicializátory objektů s pojmenovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="828f8-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="828f8-105">Procesy, které kompilátor inicializátorech objektu tak, že první přístup k výchozí konstruktor instance a potom zpracování inicializace člena.</span><span class="sxs-lookup"><span data-stu-id="828f8-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="828f8-106">Proto pokud výchozí konstruktor je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují přístup public.</span><span class="sxs-lookup"><span data-stu-id="828f8-106">Therefore, if the default constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="828f8-107">Pokud definujete anonymního typu je nutné použít inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="828f8-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="828f8-108">Další informace najdete v tématu [jak: Vrácení podmnožin vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="828f8-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="828f8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="828f8-109">Example</span></span>  

<span data-ttu-id="828f8-110">Následující příklad ukazuje způsob inicializace nového `StudentName` typu pomocí inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="828f8-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="828f8-111">V tomto příkladu nastaví vlastnosti `StudentName` typu:</span><span class="sxs-lookup"><span data-stu-id="828f8-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp-interactive[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="828f8-112">Inicializátory objektů je možné nastavit v objektu indexery.</span><span class="sxs-lookup"><span data-stu-id="828f8-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="828f8-113">Následující příklad definuje `BaseballTeam` třídu, která používá indexeru k získání a nastavení hráče na různých místech.</span><span class="sxs-lookup"><span data-stu-id="828f8-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="828f8-114">Inicializátor můžete přiřadit přehrávače, založené na zkratka pro umístění, nebo číslo používané pro každou pozici baseballu přehledů výkonnostních metrik:</span><span class="sxs-lookup"><span data-stu-id="828f8-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp-interactive[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="828f8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="828f8-115">See Also</span></span>

- [<span data-ttu-id="828f8-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="828f8-116">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="828f8-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="828f8-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
