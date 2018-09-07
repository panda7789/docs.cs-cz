---
title: '%= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: c475517666bdadaa457dbb4188808b3a96fcdf0e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085637"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6a9f4-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6a9f4-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="6a9f4-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="6a9f4-103">The remainder assignment operator.</span></span>

<span data-ttu-id="6a9f4-104">Pomocí výrazu `%=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="6a9f4-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="6a9f4-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="6a9f4-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="6a9f4-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="6a9f4-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="6a9f4-107">[Operátor zbytku](remainder-operator.md) `%` podporuje všechny číselné typy a vypočítá zbytek po dělení operandů.</span><span class="sxs-lookup"><span data-stu-id="6a9f4-107">The [remainder operator](remainder-operator.md) `%` is supported by all numeric types and computes the remainder after division of its operands.</span></span>

<span data-ttu-id="6a9f4-108">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor zbytku](remainder-operator.md) `%`, operátor přiřazení zbytku `%=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="6a9f4-108">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="6a9f4-109">Následující příklad ukazuje použití `%=` operátor:</span><span class="sxs-lookup"><span data-stu-id="6a9f4-109">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="6a9f4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a9f4-110">See also</span></span>

- [<span data-ttu-id="6a9f4-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6a9f4-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6a9f4-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6a9f4-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6a9f4-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6a9f4-113">C# Operators</span></span>](index.md)
