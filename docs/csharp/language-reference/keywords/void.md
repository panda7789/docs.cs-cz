---
title: void (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48028306"
---
# <a name="void-c-reference"></a><span data-ttu-id="2d201-102">void (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d201-102">void (C# Reference)</span></span>
<span data-ttu-id="2d201-103">Při použití jako návratový typ pro metodu, `void` Určuje, že metoda nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2d201-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="2d201-104">`void` není povoleno v seznamu parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="2d201-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="2d201-105">Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu, je deklarována následovně:</span><span class="sxs-lookup"><span data-stu-id="2d201-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="2d201-106">`void` slouží také v nezabezpečeném kontextu. Chcete-li deklarovat ukazatel na neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="2d201-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="2d201-107">Další informace najdete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="2d201-107">For more information, see [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="2d201-108">`void` je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="2d201-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2d201-109">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d201-109">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2d201-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d201-110">See also</span></span>

- [<span data-ttu-id="2d201-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d201-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2d201-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2d201-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2d201-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d201-113">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="2d201-114">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="2d201-114">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
- [<span data-ttu-id="2d201-115">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="2d201-115">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
- [<span data-ttu-id="2d201-116">Metody</span><span class="sxs-lookup"><span data-stu-id="2d201-116">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [<span data-ttu-id="2d201-117">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="2d201-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
