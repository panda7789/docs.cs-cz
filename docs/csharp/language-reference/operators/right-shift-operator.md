---
title: '&gt;&gt; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 7a2992befcacfdc1d9bb968b611051e15702cca8
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42924821"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="50205-102">&gt;&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="50205-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="50205-103">Operátor posunutí doprava (`>>`) posune jeho prvního operandu vpravo o počet bitů určený svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="50205-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50205-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="50205-104">Remarks</span></span>  
 <span data-ttu-id="50205-105">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [uint](../../../csharp/language-reference/keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu (Druhý operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="50205-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="50205-106">Pokud je první operand [dlouhé](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu (Druhý operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="50205-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="50205-107">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [dlouhé](../../../csharp/language-reference/keywords/long.md), pravého posunutí je aritmetické posun (horní prázdnou bity jsou nastaveny na bit znaménka).</span><span class="sxs-lookup"><span data-stu-id="50205-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="50205-108">Pokud je první operand je typu [uint](../../../csharp/language-reference/keywords/uint.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), pravého posunutí je logický posun (bity nejvyšším jsou vyplněny nulami).</span><span class="sxs-lookup"><span data-stu-id="50205-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="50205-109">Lze přetěžovat uživatelsky definované typy `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu [int](../../../csharp/language-reference/keywords/int.md). Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="50205-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="50205-110">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="50205-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50205-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="50205-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="50205-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="50205-112">See Also</span></span>

- [<span data-ttu-id="50205-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50205-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="50205-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="50205-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="50205-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50205-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
