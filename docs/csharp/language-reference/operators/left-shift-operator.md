---
title: "&lt;&lt;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="6b68c-102">&lt;&lt;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6b68c-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="6b68c-103">Operátor posunutí doleva (`<<`) posuny jeho první operand zbývajících podle počtu bitů určeného její druhý operand.</span><span class="sxs-lookup"><span data-stu-id="6b68c-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="6b68c-104">Musí být typ Druhý operand [int](../../../csharp/language-reference/keywords/int.md) nebo typu, který má předdefinované implicitní číselný převod na `int`.</span><span class="sxs-lookup"><span data-stu-id="6b68c-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b68c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b68c-105">Remarks</span></span>  
 <span data-ttu-id="6b68c-106">Pokud je první operand [int](../../../csharp/language-reference/keywords/int.md) nebo [Celé_číslo](../../../csharp/language-reference/keywords/uint.md) (32bitová verze množství), počet posunutí je dáno nejnižší pět bitů Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="6b68c-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="6b68c-107">Počet skutečné posunutí je bits 0 až 31.</span><span class="sxs-lookup"><span data-stu-id="6b68c-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="6b68c-108">Pokud je první operand [dlouho](../../../csharp/language-reference/keywords/long.md) nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) (množství 64-bit), počet posunutí je dáno na nejnižší šesti bits Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="6b68c-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="6b68c-109">Počet skutečné posunutí je 0 až 63 bitů.</span><span class="sxs-lookup"><span data-stu-id="6b68c-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="6b68c-110">Všechny nejvyšších bitů, které jsou v rozsahu typu první operand po k posunu nejsou zahozena a bits prázdný nejnižší jsou vyplněna nula.</span><span class="sxs-lookup"><span data-stu-id="6b68c-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="6b68c-111">Posunutí operations nikdy příčina přetečení.</span><span class="sxs-lookup"><span data-stu-id="6b68c-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="6b68c-112">Uživatelem definované typy může přetížit `<<` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typ Druhý operand `int`.</span><span class="sxs-lookup"><span data-stu-id="6b68c-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="6b68c-113">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="6b68c-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b68c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b68c-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="6b68c-115">Komentáře</span><span class="sxs-lookup"><span data-stu-id="6b68c-115">Comments</span></span>  
 <span data-ttu-id="6b68c-116">Všimněte si, že `i<<1` a `i<<33` poskytnout stejný výsledek, protože 1 a 33 mají stejné nejnižší pět bits.</span><span class="sxs-lookup"><span data-stu-id="6b68c-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b68c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b68c-117">See Also</span></span>  
 [<span data-ttu-id="6b68c-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b68c-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6b68c-119">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6b68c-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6b68c-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b68c-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
