---
title: '% = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 09/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: d0732f9578b64c894ecc1d3bb15cee11a8d5b6a3
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245558"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9aa75-102">%= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9aa75-102">%= Operator (C# Reference)</span></span>

<span data-ttu-id="9aa75-103">Operátor přiřazení zbytku.</span><span class="sxs-lookup"><span data-stu-id="9aa75-103">The remainder assignment operator.</span></span>

<span data-ttu-id="9aa75-104">Pomocí výrazu `%=` operátorů, například</span><span class="sxs-lookup"><span data-stu-id="9aa75-104">An expression using the `%=` operator, such as</span></span>  

```csharp
x %= y
```  

<span data-ttu-id="9aa75-105">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="9aa75-105">is equivalent to</span></span>  

```csharp
x = x % y
```  

<span data-ttu-id="9aa75-106">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="9aa75-106">except that `x` is only evaluated once.</span></span>
  
<span data-ttu-id="9aa75-107">[Operátor zbytku](remainder-operator.md) `%` vypočítá zbytek po dělení operandů.</span><span class="sxs-lookup"><span data-stu-id="9aa75-107">The [remainder operator](remainder-operator.md) `%` computes the remainder after division of its operands.</span></span> <span data-ttu-id="9aa75-108">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="9aa75-108">It's supported by all numeric types.</span></span>

<span data-ttu-id="9aa75-109">Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor zbytku](remainder-operator.md) `%`, operátor přiřazení zbytku `%=` je implicitně přetížena.</span><span class="sxs-lookup"><span data-stu-id="9aa75-109">If a user-defined type [overloads](../keywords/operator.md) the [remainder operator](remainder-operator.md) `%`, the remainder assignment operator `%=` is implicitly overloaded.</span></span>
  
<span data-ttu-id="9aa75-110">Následující příklad ukazuje použití `%=` operátor:</span><span class="sxs-lookup"><span data-stu-id="9aa75-110">The following example demonstrates the usage of the `%=` operator:</span></span>

[!code-csharp-interactive[%= example](~/samples/snippets/csharp/language-reference/operators/RemainderExamples.cs#3)]

## <a name="see-also"></a><span data-ttu-id="9aa75-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9aa75-111">See also</span></span>

- [<span data-ttu-id="9aa75-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9aa75-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9aa75-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9aa75-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9aa75-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9aa75-114">C# Operators</span></span>](index.md)
