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
ms.openlocfilehash: 80e38d8e75b9ad573b635d544d6381950f107583
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333681"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="a0c6a-102">&gt;&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a0c6a-102">&gt;&gt; operator (C# Reference)</span></span>

<span data-ttu-id="a0c6a-103">Operátor posunutí doprava (`>>`) posune jeho prvního operandu vpravo o počet bitů určený svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0c6a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a0c6a-104">Remarks</span></span>

<span data-ttu-id="a0c6a-105">Pokud je první operand [int](../keywords/int.md) nebo [uint](../keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu (Druhý operand & 0x1f).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-105">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>

<span data-ttu-id="a0c6a-106">Pokud je první operand [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu (Druhý operand & 0x3f).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-106">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>

<span data-ttu-id="a0c6a-107">Pokud je první operand [int](../keywords/int.md) nebo [dlouhé](../keywords/long.md), pravého posunutí je aritmetické posun (horní prázdnou bity jsou nastaveny na bit znaménka).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-107">If the first operand is an [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="a0c6a-108">Pokud je první operand je typu [uint](../keywords/uint.md) nebo [ulong](../keywords/ulong.md), pravého posunutí je logický posun (bity nejvyšším jsou vyplněny nulami).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-108">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>

<span data-ttu-id="a0c6a-109">Lze přetěžovat uživatelsky definované typy `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu [int](../keywords/int.md). Další informace najdete v tématu [operátor](../keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="a0c6a-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../keywords/int.md). For more information, see [operator](../keywords/operator.md).</span></span> <span data-ttu-id="a0c6a-110">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="a0c6a-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="a0c6a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0c6a-111">Example</span></span>

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a><span data-ttu-id="a0c6a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0c6a-112">See Also</span></span>

- [<span data-ttu-id="a0c6a-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a0c6a-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a0c6a-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a0c6a-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a0c6a-115">C#operátory</span><span class="sxs-lookup"><span data-stu-id="a0c6a-115">C# operators</span></span>](index.md)