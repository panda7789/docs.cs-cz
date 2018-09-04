---
title: '&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43517201"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="5b597-102">&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5b597-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="5b597-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="5b597-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b597-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b597-104">Remarks</span></span>  
 <span data-ttu-id="5b597-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="5b597-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="5b597-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="5b597-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="5b597-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="5b597-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="5b597-108">[<< Operátor](../../../csharp/language-reference/operators/left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.</span><span class="sxs-lookup"><span data-stu-id="5b597-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="5b597-109">`<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](../../../csharp/language-reference/operators/left-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="5b597-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b597-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b597-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5b597-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b597-111">See Also</span></span>

- [<span data-ttu-id="5b597-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b597-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="5b597-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5b597-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5b597-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b597-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
