---
title: '&lt;&lt;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: f49c6360d6fee3f6d612aee51446545f25cd7d18
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239170"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="2c510-102">&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2c510-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="2c510-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="2c510-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c510-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c510-104">Remarks</span></span>  
 <span data-ttu-id="2c510-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="2c510-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="2c510-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="2c510-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="2c510-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="2c510-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="2c510-108">[<< Operátor](../../../csharp/language-reference/operators/left-shift-operator.md) posune `x` doleva o počet bitů určený `y`.</span><span class="sxs-lookup"><span data-stu-id="2c510-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="2c510-109">`<<=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [<< operátor](../../../csharp/language-reference/operators/left-shift-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2c510-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c510-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c510-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2c510-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c510-111">See Also</span></span>

- [<span data-ttu-id="2c510-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2c510-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="2c510-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2c510-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2c510-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2c510-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
