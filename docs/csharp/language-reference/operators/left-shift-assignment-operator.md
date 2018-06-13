---
title: '&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: e5f3886670baa34b0360501ee15280b93fac36bc
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171790"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="bedaa-102">&lt;&lt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bedaa-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="bedaa-103">Operátor přiřazení posunutí doleva.</span><span class="sxs-lookup"><span data-stu-id="bedaa-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bedaa-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bedaa-104">Remarks</span></span>  
 <span data-ttu-id="bedaa-105">Výraz, který formuláře</span><span class="sxs-lookup"><span data-stu-id="bedaa-105">An expression of the form</span></span>  
  
```csharp  
x <<= y  
```  
  
 <span data-ttu-id="bedaa-106">vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="bedaa-106">is evaluated as</span></span>  
  
```csharp  
x = x << y  
```  
  
 <span data-ttu-id="bedaa-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="bedaa-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="bedaa-108">[<< Operátor](../../../csharp/language-reference/operators/left-shift-operator.md) posune `x` zbývajících podle počtu bitů určeného `y`.</span><span class="sxs-lookup"><span data-stu-id="bedaa-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="bedaa-109">`<<=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [<< operátor](../../../csharp/language-reference/operators/left-shift-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="bedaa-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bedaa-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="bedaa-110">Example</span></span>  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bedaa-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="bedaa-111">See Also</span></span>  
 [<span data-ttu-id="bedaa-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bedaa-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bedaa-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bedaa-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bedaa-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bedaa-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
