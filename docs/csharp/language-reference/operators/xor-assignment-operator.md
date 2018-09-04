---
title: ^= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43540043"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0b795-102">^= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0b795-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="0b795-103">Operátor přiřazení exkluzivní disjunkce OR.</span><span class="sxs-lookup"><span data-stu-id="0b795-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b795-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b795-104">Remarks</span></span>  
 <span data-ttu-id="0b795-105">Výraz ve tvaru</span><span class="sxs-lookup"><span data-stu-id="0b795-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="0b795-106">je vyhodnocen jako</span><span class="sxs-lookup"><span data-stu-id="0b795-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="0b795-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="0b795-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="0b795-108">[^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní operátor OR operaci na celočíselných operandech a logické exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="0b795-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="0b795-109">^ = – Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0b795-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b795-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b795-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0b795-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b795-111">See Also</span></span>

- [<span data-ttu-id="0b795-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b795-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="0b795-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0b795-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="0b795-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0b795-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
