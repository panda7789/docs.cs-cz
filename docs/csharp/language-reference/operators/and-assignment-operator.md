---
title: '&amp;= – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933949"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="0b63a-102">&amp;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0b63a-102">&amp;= Operator (C# Reference)</span></span>
<span data-ttu-id="0b63a-103">Operátor přiřazení AND.</span><span class="sxs-lookup"><span data-stu-id="0b63a-103">The AND assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b63a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b63a-104">Remarks</span></span>  
 <span data-ttu-id="0b63a-105">Pomocí výrazu `&=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="0b63a-105">An expression using the `&=` assignment operator, such as</span></span>  
  
```csharp  
x &= y  
```  
  
 <span data-ttu-id="0b63a-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="0b63a-106">is equivalent to</span></span>  
  
```csharp  
x = x & y  
```  
  
 <span data-ttu-id="0b63a-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="0b63a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0b63a-108">[& – Operátor](../../../csharp/language-reference/operators/and-operator.md) provádí bitové logické AND operace na celočíselných operandech a logický operátor AND `bool` operandy.</span><span class="sxs-lookup"><span data-stu-id="0b63a-108">The [& operator](../../../csharp/language-reference/operators/and-operator.md) performs a bitwise logical AND operation on integral operands and logical AND on `bool` operands.</span></span>  
  
 <span data-ttu-id="0b63a-109">`&=` Operátor nelze přetížit přímo, ale uživatelské typy mohou přetížit binárního souboru [& – operátor](../../../csharp/language-reference/operators/and-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0b63a-109">The `&=` operator cannot be overloaded directly, but user-defined types can overload the binary [& operator](../../../csharp/language-reference/operators/and-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b63a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b63a-110">Example</span></span>  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0b63a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b63a-111">See Also</span></span>

- [<span data-ttu-id="0b63a-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b63a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0b63a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0b63a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0b63a-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b63a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
