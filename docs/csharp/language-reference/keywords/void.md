---
title: void – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742770"
---
# <a name="void-c-reference"></a><span data-ttu-id="d5a21-102">void (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d5a21-102">void (C# Reference)</span></span>

<span data-ttu-id="d5a21-103">Při použití jako návratový typ pro metodu `void` určuje, že metoda nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d5a21-103">When used as the return type for a method, `void` specifies that the method doesn't return a value.</span></span>

<span data-ttu-id="d5a21-104">`void` není povolen v seznamu parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="d5a21-104">`void` isn't allowed in the parameter list of a method.</span></span> <span data-ttu-id="d5a21-105">Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu, je deklarována takto:</span><span class="sxs-lookup"><span data-stu-id="d5a21-105">A method that takes no parameters and returns no value is declared as follows:</span></span>

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

<span data-ttu-id="d5a21-106">`void` se používá také v nezabezpečeném kontextu k deklaraci ukazatele na neznámý typ.</span><span class="sxs-lookup"><span data-stu-id="d5a21-106">`void` is also used in an unsafe context to declare a pointer to an unknown type.</span></span> <span data-ttu-id="d5a21-107">Další informace naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="d5a21-107">For more information, see [Pointer types](../../programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>

<span data-ttu-id="d5a21-108">`void` je alias pro typ <xref:System.Void?displayProperty=nameWithType> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5a21-108">`void` is an alias for the .NET Framework <xref:System.Void?displayProperty=nameWithType> type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d5a21-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5a21-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="d5a21-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d5a21-110">See also</span></span>

- [<span data-ttu-id="d5a21-111">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="d5a21-111">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d5a21-112">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d5a21-112">C# keywords</span></span>](index.md)
- [<span data-ttu-id="d5a21-113">Typy odkazů</span><span class="sxs-lookup"><span data-stu-id="d5a21-113">Reference types</span></span>](reference-types.md)
- [<span data-ttu-id="d5a21-114">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="d5a21-114">Value types</span></span>](../builtin-types/value-types.md)
- [<span data-ttu-id="d5a21-115">Metody</span><span class="sxs-lookup"><span data-stu-id="d5a21-115">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)
- [<span data-ttu-id="d5a21-116">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="d5a21-116">Unsafe code and pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
