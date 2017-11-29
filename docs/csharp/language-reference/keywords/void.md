---
title: "void (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords: void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a><span data-ttu-id="f6ee3-102">void (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f6ee3-102">void (C# Reference)</span></span>
<span data-ttu-id="f6ee3-103">Když se použije jako návratový typ pro metodu, `void` Určuje, že metoda nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="f6ee3-104">`void`v seznamu parametrů metody není povolena.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="f6ee3-105">Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu je deklarovaná následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f6ee3-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="f6ee3-106">`void`se také používá v kontextu unsafe deklarovat ukazatel na neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="f6ee3-107">Další informace najdete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="f6ee3-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="f6ee3-108">`void`je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="f6ee3-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f6ee3-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6ee3-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6ee3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6ee3-110">See also</span></span>
 [<span data-ttu-id="f6ee3-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6ee3-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f6ee3-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f6ee3-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f6ee3-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f6ee3-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f6ee3-114">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="f6ee3-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="f6ee3-115">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="f6ee3-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="f6ee3-116">Metody</span><span class="sxs-lookup"><span data-stu-id="f6ee3-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="f6ee3-117">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="f6ee3-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
