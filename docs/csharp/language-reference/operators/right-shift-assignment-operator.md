---
title: '&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: ccc3f688d985b9e35404550f0c53a7acf8095dd5
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171415"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="4388a-102">&gt;&gt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4388a-102">&gt;&gt;= Operator (C# Reference)</span></span>
<span data-ttu-id="4388a-103">Operátor přiřazení posunutí doprava.</span><span class="sxs-lookup"><span data-stu-id="4388a-103">The right-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4388a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4388a-104">Remarks</span></span>  
 <span data-ttu-id="4388a-105">Výraz, který formuláře</span><span class="sxs-lookup"><span data-stu-id="4388a-105">An expression of the form</span></span>  
  
```csharp  
x >>= y  
```  
  
 <span data-ttu-id="4388a-106">vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="4388a-106">is evaluated as</span></span>  
  
```csharp  
x = x >> y  
```  
  
 <span data-ttu-id="4388a-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="4388a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4388a-108">[>> Operátor](../../../csharp/language-reference/operators/right-shift-operator.md) posune `x` doprava o částku určeného `y`.</span><span class="sxs-lookup"><span data-stu-id="4388a-108">The [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) shifts `x` right by an amount specified by `y`.</span></span>  
  
 <span data-ttu-id="4388a-109">>> = Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [>> operátor](../../../csharp/language-reference/operators/right-shift-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4388a-109">The >>= operator cannot be overloaded directly, but user-defined types can overload the [>> operator](../../../csharp/language-reference/operators/right-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4388a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="4388a-110">Example</span></span>  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4388a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="4388a-111">See Also</span></span>  
 [<span data-ttu-id="4388a-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4388a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4388a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4388a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4388a-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4388a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
