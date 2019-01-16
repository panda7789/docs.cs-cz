---
title: '&lt;&lt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 79a48d88e2c83b5ad78804367ee3c07f78622c08
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333522"
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="43a7c-102">&lt;&lt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="43a7c-102">&lt;&lt; operator (C# Reference)</span></span>

<span data-ttu-id="43a7c-103">Operátor posunutí doleva (`<<`) staffhubu jeho prvního operandu vlevo o počet bitů určený svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="43a7c-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="43a7c-104">Musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má předdefinované implicitní převod čísla na `int`.</span><span class="sxs-lookup"><span data-stu-id="43a7c-104">The type of the second operand must be an [int](../keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>

## <a name="remarks"></a><span data-ttu-id="43a7c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43a7c-105">Remarks</span></span>

<span data-ttu-id="43a7c-106">Pokud je první operand [int](../keywords/int.md) nebo [uint](../keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="43a7c-106">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="43a7c-107">To znamená, že počet skutečné posunutí je 0 až 31 bitů.</span><span class="sxs-lookup"><span data-stu-id="43a7c-107">That is, the actual shift count is 0 to 31 bits.</span></span>

<span data-ttu-id="43a7c-108">Pokud je první operand [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="43a7c-108">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="43a7c-109">To znamená že počet skutečné posunutí je 0 až 63 bitů.</span><span class="sxs-lookup"><span data-stu-id="43a7c-109">That is, the actual shift count is 0 to 63 bits.</span></span>

<span data-ttu-id="43a7c-110">Všechny nejvyšším bity, které jsou v rozsahu typu prvního operandu po přesun se zahodí a prázdný bity nižšího řádu jsou vyplněny nulami.</span><span class="sxs-lookup"><span data-stu-id="43a7c-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="43a7c-111">Operace posunutí nikdy nezpůsobí přetečení.</span><span class="sxs-lookup"><span data-stu-id="43a7c-111">Shift operations never cause overflows.</span></span>

<span data-ttu-id="43a7c-112">Lze přetěžovat uživatelsky definované typy `<<` – operátor (naleznete v tématu [operátor](../keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu `int`.</span><span class="sxs-lookup"><span data-stu-id="43a7c-112">User-defined types can overload the `<<` operator (see [operator](../keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="43a7c-113">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="43a7c-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="43a7c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="43a7c-114">Example</span></span>

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a><span data-ttu-id="43a7c-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="43a7c-115">Comments</span></span>

<span data-ttu-id="43a7c-116">Všimněte si, že `i<<1` a `i<<33` poskytují stejný výsledek, protože 1 a 33 mají stejné pět bity nižšího řádu.</span><span class="sxs-lookup"><span data-stu-id="43a7c-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>

## <a name="see-also"></a><span data-ttu-id="43a7c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43a7c-117">See also</span></span>

- [<span data-ttu-id="43a7c-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43a7c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43a7c-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="43a7c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43a7c-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="43a7c-120">C# Operators</span></span>](index.md)
