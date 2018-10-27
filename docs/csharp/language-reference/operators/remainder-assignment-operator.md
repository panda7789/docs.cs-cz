---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: ab3a6a8d5cbfeb4d527ca1f9c233ddfaba3d35ff
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188713"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="be2dc-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="be2dc-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="be2dc-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="be2dc-103">The remainder assignment operator.</span></span>

<span data-ttu-id="be2dc-104">Pomocí výrazu `%=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="be2dc-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="be2dc-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="be2dc-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="be2dc-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="be2dc-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="be2dc-107">[Operátor zbytku](remainder-operator.md) `%` vypočítá zbytek po dělení operandů.</span><span class="sxs-lookup"><span data-stu-id="be2dc-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="be2dc-108">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="be2dc-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="be2dc-109">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor zbytku](remainder-operator.md) `%`, operátor přiřazení zbytku `%=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="be2dc-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="be2dc-110">Následující příklad ukazuje použití `%=` operátor:</span><span class="sxs-lookup"><span data-stu-id="be2dc-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="be2dc-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be2dc-111">See also</span></span>

- [<span data-ttu-id="be2dc-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be2dc-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be2dc-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be2dc-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be2dc-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be2dc-114">C# Operators</span></span>](index.md)
