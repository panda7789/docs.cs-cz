---
title: '&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865020"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="9440d-102">&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9440d-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="9440d-103">Operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="9440d-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9440d-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9440d-104">Remarks</span></span>  
 <span data-ttu-id="9440d-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="9440d-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="9440d-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="9440d-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="9440d-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="9440d-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="9440d-108">[>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` přímo podle zadaného množství určené `y`.</span><span class="sxs-lookup"><span data-stu-id="9440d-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="9440d-109">>> = Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9440d-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9440d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9440d-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9440d-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="9440d-111">See Also</span></span>

- [<span data-ttu-id="9440d-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9440d-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9440d-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9440d-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9440d-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9440d-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
