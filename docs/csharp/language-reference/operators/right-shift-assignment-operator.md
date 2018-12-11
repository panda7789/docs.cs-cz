---
title: '&gt;&gt;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239443"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="f86e0-102">&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f86e0-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="f86e0-103">Operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="f86e0-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f86e0-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f86e0-104">Remarks</span></span>  
 <span data-ttu-id="f86e0-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="f86e0-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="f86e0-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="f86e0-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="f86e0-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="f86e0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f86e0-108">[>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.</span><span class="sxs-lookup"><span data-stu-id="f86e0-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="f86e0-109">>> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f86e0-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f86e0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f86e0-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f86e0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f86e0-111">See Also</span></span>

- [<span data-ttu-id="f86e0-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f86e0-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f86e0-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f86e0-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f86e0-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f86e0-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
