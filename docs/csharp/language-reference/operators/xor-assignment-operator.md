---
title: ^ = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: cf39c8e8586e9d4f537fe38d8b28f55542db6ab8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237152"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b347a-102">^= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b347a-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="b347a-103">Operátor přiřazení exkluzivní disjunkce OR.</span><span class="sxs-lookup"><span data-stu-id="b347a-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b347a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b347a-104">Remarks</span></span>  
 <span data-ttu-id="b347a-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="b347a-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="b347a-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="b347a-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="b347a-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="b347a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b347a-108">[^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní operátor OR operaci na celočíselných operandech a logické exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="b347a-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="b347a-109">^ = – Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b347a-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b347a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b347a-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b347a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b347a-111">See Also</span></span>

- [<span data-ttu-id="b347a-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b347a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b347a-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b347a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b347a-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b347a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
