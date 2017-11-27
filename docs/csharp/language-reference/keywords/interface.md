---
title: "interface (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: interface_CSharpKeyword
helpviewer_keywords: interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
caps.latest.revision: "29"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aba9ee66a90216066a47f22e251182caad465818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="interface-c-reference"></a><span data-ttu-id="5531f-102">interface (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5531f-102">interface (C# Reference)</span></span>
<span data-ttu-id="5531f-103">Rozhraní obsahuje pouze signatur [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md), [události](../../../csharp/programming-guide/events/index.md) nebo [indexery](../../../csharp/programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="5531f-103">An interface contains only the signatures of [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [events](../../../csharp/programming-guide/events/index.md) or [indexers](../../../csharp/programming-guide/indexers/index.md).</span></span> <span data-ttu-id="5531f-104">Třída nebo struktura, která implementuje rozhraní, musí implementovat členy rozhraní zadané v definici rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5531f-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="5531f-105">V následujícím příkladu musí třída `ImplementationClass` implementovat metodu s názvem `SampleMethod`, která nemá žádné parametry a vrací `void`.</span><span class="sxs-lookup"><span data-stu-id="5531f-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>  
  
 <span data-ttu-id="5531f-106">Další informace a příklady naleznete v tématu [rozhraní](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="5531f-106">For more information and examples, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5531f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5531f-107">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_1.cs)]  
  
 <span data-ttu-id="5531f-108">Rozhraní může být členem oboru názvů nebo třídy a může obsahovat podpisy následujících členů:</span><span class="sxs-lookup"><span data-stu-id="5531f-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>  
  
-   [<span data-ttu-id="5531f-109">Metody</span><span class="sxs-lookup"><span data-stu-id="5531f-109">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="5531f-110">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5531f-110">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
  
-   [<span data-ttu-id="5531f-111">Indexery</span><span class="sxs-lookup"><span data-stu-id="5531f-111">Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="5531f-112">Události</span><span class="sxs-lookup"><span data-stu-id="5531f-112">Events</span></span>](../../../csharp/language-reference/keywords/event.md)  
  
 <span data-ttu-id="5531f-113">Rozhraní může dědit z jednoho nebo více základních rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5531f-113">An interface can inherit from one or more base interfaces.</span></span>  
  
 <span data-ttu-id="5531f-114">Jestliže seznam základních typů obsahuje základní třídu a rozhraní, musí se základní třída nacházet v seznamu jako první.</span><span class="sxs-lookup"><span data-stu-id="5531f-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>  
  
 <span data-ttu-id="5531f-115">Třída, která implementuje rozhraní, může explicitně implementovat členy rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5531f-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="5531f-116">Explicitně implementovaný člen není přístupný prostřednictvím instance třídy, ale pouze prostřednictvím instance rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5531f-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>  
  
 <span data-ttu-id="5531f-117">Další informace a příklady kódu v implementace explicitního rozhraní najdete v tématu [explicitní implementace rozhraní](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="5531f-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5531f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5531f-118">Example</span></span>  
 <span data-ttu-id="5531f-119">Následující příklad ukazuje implementaci rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5531f-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="5531f-120">V tomto příkladu obsahuje rozhraní deklaraci vlastnosti a třída obsahuje implementaci.</span><span class="sxs-lookup"><span data-stu-id="5531f-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="5531f-121">Jakákoli instance třídy, která implementuje rozhraní `IPoint`, má celočíselné vlastnosti `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="5531f-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/interface_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5531f-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5531f-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5531f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="5531f-123">See Also</span></span>  
 [<span data-ttu-id="5531f-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5531f-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5531f-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5531f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5531f-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5531f-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5531f-127">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="5531f-127">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="5531f-128">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="5531f-128">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="5531f-129">Pomocí vlastností</span><span class="sxs-lookup"><span data-stu-id="5531f-129">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)  
 [<span data-ttu-id="5531f-130">Použití indexerů</span><span class="sxs-lookup"><span data-stu-id="5531f-130">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
 [<span data-ttu-id="5531f-131">– Třída</span><span class="sxs-lookup"><span data-stu-id="5531f-131">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="5531f-132">Struktura</span><span class="sxs-lookup"><span data-stu-id="5531f-132">struct</span></span>](../../../csharp/language-reference/keywords/struct.md)  
 [<span data-ttu-id="5531f-133">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="5531f-133">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
