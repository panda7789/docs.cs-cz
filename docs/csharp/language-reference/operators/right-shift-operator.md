---
title: '&gt;&gt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239992"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="1eddc-102">&gt;&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1eddc-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="1eddc-103">Operátor posunutí doprava (`>>`) posune jeho prvního operandu vpravo o počet bitů určený svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="1eddc-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1eddc-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1eddc-104">Remarks</span></span>  
 <span data-ttu-id="1eddc-105">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [uint](../../../csharp/language-reference/keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu (Druhý operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="1eddc-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="1eddc-106">Pokud je první operand [dlouhé](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu (Druhý operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="1eddc-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="1eddc-107">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [dlouhé](../../../csharp/language-reference/keywords/long.md), pravého posunutí je aritmetické posun (horní prázdnou bity jsou nastaveny na bit znaménka).</span><span class="sxs-lookup"><span data-stu-id="1eddc-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="1eddc-108">Pokud je první operand je typu [uint](../../../csharp/language-reference/keywords/uint.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), pravého posunutí je logický posun (bity nejvyšším jsou vyplněny nulami).</span><span class="sxs-lookup"><span data-stu-id="1eddc-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="1eddc-109">Lze přetěžovat uživatelsky definované typy `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu [int](../../../csharp/language-reference/keywords/int.md). Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="1eddc-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="1eddc-110">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="1eddc-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1eddc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1eddc-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1eddc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1eddc-112">See Also</span></span>

- [<span data-ttu-id="1eddc-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1eddc-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1eddc-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1eddc-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1eddc-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1eddc-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
