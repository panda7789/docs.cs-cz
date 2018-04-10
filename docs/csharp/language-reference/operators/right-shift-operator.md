---
title: '&gt;&gt;Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7c2eddf06d7b8417c9fcb0fed395b2bf51e07144
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="84ed6-102">&gt;&gt;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="84ed6-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="84ed6-103">Operátor posunutí doprava (`>>`) posune jeho první operand právo podle počtu bitů určeného její druhý operand.</span><span class="sxs-lookup"><span data-stu-id="84ed6-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84ed6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84ed6-104">Remarks</span></span>  
 <span data-ttu-id="84ed6-105">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (32bitová verze množství), počet posunutí je dáno nejnižší pět bitů Druhý operand (Druhý operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="84ed6-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="84ed6-106">Pokud je první operand [dlouho](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunutí je dáno na nejnižší šesti bits Druhý operand (Druhý operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="84ed6-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="84ed6-107">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [dlouho](../../../csharp/language-reference/keywords/long.md), aritmetické posunutí je posunutí doprava (horní prázdný bity jsou nastaveny na bit přihlašování).</span><span class="sxs-lookup"><span data-stu-id="84ed6-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="84ed6-108">Pokud je první operand typu [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), je logické shift posunutí doprava (horní bity jsou vyplněna nula).</span><span class="sxs-lookup"><span data-stu-id="84ed6-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="84ed6-109">Uživatelem definované typy může přetížit `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typ Druhý operand [int](../../../csharp/language-reference/keywords/int.md). Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="84ed6-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="84ed6-110">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="84ed6-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84ed6-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="84ed6-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="84ed6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="84ed6-112">See Also</span></span>  
 [<span data-ttu-id="84ed6-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84ed6-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="84ed6-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="84ed6-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="84ed6-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="84ed6-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
