---
title: "^ – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4ccd32ea8abd8ca3252380083eafecad2b572ed7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e2d0d-102">^ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e2d0d-102">^ Operator (C# Reference)</span></span>
<span data-ttu-id="e2d0d-103">Binární `^` jsou operátory předdefinovány pro integrální typy a `bool`.</span><span class="sxs-lookup"><span data-stu-id="e2d0d-103">Binary `^` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="e2d0d-104">Pro integrální typy `^` vypočítá bitový exkluzivní disjunkce OR z operandů.</span><span class="sxs-lookup"><span data-stu-id="e2d0d-104">For integral types, `^` computes the bitwise exclusive-OR of its operands.</span></span> <span data-ttu-id="e2d0d-105">Pro `bool` operandy, `^` vypočítá logické exkluzivní- nebo operandů; výsledek je `true` jenom v případě právě jeden z jeho operandy je `true`.</span><span class="sxs-lookup"><span data-stu-id="e2d0d-105">For `bool` operands, `^` computes the logical exclusive-or of its operands; that is, the result is `true` if and only if exactly one of its operands is `true`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2d0d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2d0d-106">Remarks</span></span>  
 <span data-ttu-id="e2d0d-107">Uživatelem definované typy může přetížit `^` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e2d0d-107">User-defined types can overload the `^` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="e2d0d-108">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2d0d-108">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2d0d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e2d0d-109">Example</span></span>  
 [!code-csharp[csRefOperators#30](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-operator_1.cs)]  
  
 <span data-ttu-id="e2d0d-110">Výpočet z `0xf8 ^ 0x3f` v předchozím příkladu provede bitové exkluzivní disjunkce OR následující dvě binárních hodnot, které odpovídají hexadecimální hodnoty F8 a 3F:</span><span class="sxs-lookup"><span data-stu-id="e2d0d-110">The computation of `0xf8 ^ 0x3f` in the previous example performs a bitwise exclusive-OR of the following two binary values, which correspond to the hexadecimal values F8 and 3F:</span></span>  
  
 `1111 1000`  
  
 `0011 1111`  
  
 <span data-ttu-id="e2d0d-111">Výsledkem exkluzivní disjunkce OR je `1100 0111`, což je C7 v šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="e2d0d-111">The result of the exclusive-OR is `1100 0111`, which is C7 in hexadecimal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2d0d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e2d0d-112">See Also</span></span>  
 [<span data-ttu-id="e2d0d-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2d0d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e2d0d-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="e2d0d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e2d0d-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e2d0d-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
