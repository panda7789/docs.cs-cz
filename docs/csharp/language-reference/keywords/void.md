---
title: void – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: af79d39282ea38811777ea1f23054120afc39d2c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632938"
---
# <a name="void-c-reference"></a><span data-ttu-id="166ba-102">void (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="166ba-102">void (C# Reference)</span></span>

<span data-ttu-id="166ba-103">Při použití jako návratový typ pro metodu, `void` Určuje, že metoda nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="166ba-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="166ba-104">`void` není povoleno v seznamu parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="166ba-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="166ba-105">Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu, je deklarována následovně:</span><span class="sxs-lookup"><span data-stu-id="166ba-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="166ba-106">`void` slouží také v nezabezpečeném kontextu. Chcete-li deklarovat ukazatel na neznámého typu.</span><span class="sxs-lookup"><span data-stu-id="166ba-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="166ba-107">Další informace najdete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="166ba-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="166ba-108">`void` je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="166ba-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="166ba-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="166ba-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="166ba-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="166ba-110">See also</span></span>

- [<span data-ttu-id="166ba-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="166ba-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="166ba-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="166ba-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="166ba-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="166ba-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="166ba-114">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="166ba-114">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="166ba-115">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="166ba-115">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="166ba-116">Metody</span><span class="sxs-lookup"><span data-stu-id="166ba-116">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="166ba-117">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="166ba-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
