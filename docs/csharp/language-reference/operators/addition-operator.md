---
title: + Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b15d5d1a304569b92b2f811a9ea714e4b30d60d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f072a-102">+ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f072a-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="f072a-103">`+` Operátor může fungovat jako unární operátor nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="f072a-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f072a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f072a-104">Remarks</span></span>  
 <span data-ttu-id="f072a-105">Unární `+` jsou operátory předdefinovány pro všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="f072a-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="f072a-106">Výsledek unární operátor `+` je právě hodnota operand operace na číselného typu.</span><span class="sxs-lookup"><span data-stu-id="f072a-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="f072a-107">Binární `+` jsou operátory předdefinovány pro typy číselný a řetězec.</span><span class="sxs-lookup"><span data-stu-id="f072a-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="f072a-108">Pro číselné typy + vypočítá součet jeho dva operandy.</span><span class="sxs-lookup"><span data-stu-id="f072a-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="f072a-109">Pokud jeden nebo oba operandy jsou typu řetězec + zřetězí řetězcové vyjádření operandy.</span><span class="sxs-lookup"><span data-stu-id="f072a-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="f072a-110">Typy delegáta také poskytují binární `+` operátor, který provádí zřetězení delegáta.</span><span class="sxs-lookup"><span data-stu-id="f072a-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="f072a-111">Uživatelem definované typy může přetížit unární `+` a binární `+` operátory.</span><span class="sxs-lookup"><span data-stu-id="f072a-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="f072a-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="f072a-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="f072a-113">Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="f072a-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f072a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f072a-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f072a-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f072a-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f072a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f072a-116">See Also</span></span>  
 [<span data-ttu-id="f072a-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f072a-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f072a-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f072a-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f072a-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f072a-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f072a-120">operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f072a-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
