---
title: "^= – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f2e60-102">^= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f2e60-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="f2e60-103">Operátor přiřazení exkluzivní disjunkce OR.</span><span class="sxs-lookup"><span data-stu-id="f2e60-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2e60-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2e60-104">Remarks</span></span>  
 <span data-ttu-id="f2e60-105">Výraz, který formuláře</span><span class="sxs-lookup"><span data-stu-id="f2e60-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="f2e60-106">vyhodnotí jako</span><span class="sxs-lookup"><span data-stu-id="f2e60-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="f2e60-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="f2e60-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="f2e60-108">[^ – Operátor](../../../csharp/language-reference/operators/xor-operator.md) provádí bitový exkluzivní disjunkce OR operaci na integrální operandy a logických exkluzivní disjunkce OR na [bool](../../../csharp/language-reference/keywords/bool.md) operandy.</span><span class="sxs-lookup"><span data-stu-id="f2e60-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="f2e60-109">^ = – Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [^ – operátor](../../../csharp/language-reference/operators/xor-operator.md) (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="f2e60-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f2e60-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e60-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f2e60-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2e60-111">See Also</span></span>  
 [<span data-ttu-id="f2e60-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2e60-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f2e60-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f2e60-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f2e60-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f2e60-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
