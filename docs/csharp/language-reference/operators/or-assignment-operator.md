---
title: '|= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254093"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0671c-102">|= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0671c-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="0671c-103">Operátor přiřazení OR.</span><span class="sxs-lookup"><span data-stu-id="0671c-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0671c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0671c-104">Remarks</span></span>  
 <span data-ttu-id="0671c-105">Pomocí výrazu `|=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="0671c-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="0671c-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="0671c-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="0671c-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="0671c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0671c-108">[ &#124; Operátor](../../../csharp/language-reference/operators/or-operator.md) provádí bitové logické OR operace na celočíselných operandech a logický operátor OR na operandech typu bool.</span><span class="sxs-lookup"><span data-stu-id="0671c-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="0671c-109">`|=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [ &#124; operátor](../../../csharp/language-reference/operators/or-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0671c-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0671c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0671c-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0671c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0671c-111">See Also</span></span>

- [<span data-ttu-id="0671c-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0671c-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0671c-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0671c-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0671c-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0671c-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
