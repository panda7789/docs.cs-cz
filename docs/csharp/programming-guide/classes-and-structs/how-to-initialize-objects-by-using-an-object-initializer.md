---
title: 'Postupy: Inicializace objektů pomocí objektu inicializátoru - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- object initializers [C#], how to use
- objects [C#], initializing
ms.assetid: 4b75ebb2-2e29-43de-929c-d736a8f27ce6
ms.openlocfilehash: 7b31e28c23a70e9f0794c82feb2a984c40ee9d0f
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267580"
---
# <a name="how-to-initialize-objects-by-using-an-object-initializer-c-programming-guide"></a><span data-ttu-id="e57b0-102">Postupy: Inicializace objektů pomocí inicializátoru objektů (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="e57b0-102">How to: Initialize Objects by Using an Object Initializer (C# Programming Guide)</span></span>

<span data-ttu-id="e57b0-103">Inicializátory objektů můžete použít třeba inicializovat objekty typu bez explicitní volání konstruktoru pro typ deklarativní způsobem.</span><span class="sxs-lookup"><span data-stu-id="e57b0-103">You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.</span></span>  
  
<span data-ttu-id="e57b0-104">Následující příklady ukazují, jak používat inicializátory objektů s pojmenovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="e57b0-104">The following examples show how to use object initializers with named objects.</span></span> <span data-ttu-id="e57b0-105">Procesy, které kompilátor inicializátorech objektu tak, že první přístup k výchozí konstruktor instance a potom zpracování inicializace člena.</span><span class="sxs-lookup"><span data-stu-id="e57b0-105">The compiler processes object initializers by first accessing the default instance constructor and then processing the member initializations.</span></span> <span data-ttu-id="e57b0-106">Proto pokud konstruktor bez parametrů je deklarován jako `private` ve třídě, se nezdaří inicializátory objektů, které vyžadují přístup public.</span><span class="sxs-lookup"><span data-stu-id="e57b0-106">Therefore, if the parameterless constructor is declared as `private` in the class, object initializers that require public access will fail.</span></span>
  
<span data-ttu-id="e57b0-107">Pokud definujete anonymního typu je nutné použít inicializátor objektu.</span><span class="sxs-lookup"><span data-stu-id="e57b0-107">You must use an object initializer if you're defining an anonymous type.</span></span> <span data-ttu-id="e57b0-108">Další informace najdete v tématu [jak: Vrácení podmnožin vlastností elementu v dotazu](how-to-return-subsets-of-element-properties-in-a-query.md).</span><span class="sxs-lookup"><span data-stu-id="e57b0-108">For more information, see [How to: Return Subsets of Element Properties in a Query](how-to-return-subsets-of-element-properties-in-a-query.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e57b0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e57b0-109">Example</span></span>  

<span data-ttu-id="e57b0-110">Následující příklad ukazuje způsob inicializace nového `StudentName` typu pomocí inicializátory objektů.</span><span class="sxs-lookup"><span data-stu-id="e57b0-110">The following example shows how to initialize a new `StudentName` type by using object initializers.</span></span> <span data-ttu-id="e57b0-111">V tomto příkladu nastaví vlastnosti `StudentName` typu:</span><span class="sxs-lookup"><span data-stu-id="e57b0-111">This example sets properties in the `StudentName` type:</span></span>
  
[!code-csharp[InitializerObjectExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToObjectInitializers.cs#HowToObjectInitializers)]  

<span data-ttu-id="e57b0-112">Inicializátory objektů je možné nastavit v objektu indexery.</span><span class="sxs-lookup"><span data-stu-id="e57b0-112">Object initializers can be used to set indexers in an object.</span></span> <span data-ttu-id="e57b0-113">Následující příklad definuje `BaseballTeam` třídu, která používá indexeru k získání a nastavení hráče na různých místech.</span><span class="sxs-lookup"><span data-stu-id="e57b0-113">The following example defines a `BaseballTeam` class that uses an indexer to get and set players at different positions.</span></span> <span data-ttu-id="e57b0-114">Inicializátor můžete přiřadit přehrávače, založené na zkratka pro umístění, nebo číslo používané pro každou pozici baseballu přehledů výkonnostních metrik:</span><span class="sxs-lookup"><span data-stu-id="e57b0-114">The initializer can assign players, based on the abbreviation for the position, or the number used for each position baseball scorecards:</span></span>

[!code-csharp[InitializerIndexerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToIndexInitializer.cs#HowToIndexInitializer)]  

## <a name="see-also"></a><span data-ttu-id="e57b0-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e57b0-115">See also</span></span>

- [<span data-ttu-id="e57b0-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e57b0-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e57b0-117">Inicializátory objektu a kolekce</span><span class="sxs-lookup"><span data-stu-id="e57b0-117">Object and Collection Initializers</span></span>](object-and-collection-initializers.md)
