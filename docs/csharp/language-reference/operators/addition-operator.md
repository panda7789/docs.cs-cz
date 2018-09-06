---
title: + – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: b49694bc8937c58bd295f0f8e57c378802d0dfb9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871803"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ef320-102">+ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ef320-102">+ Operator (C# Reference)</span></span>
<span data-ttu-id="ef320-103">`+` Operátor může fungovat jako unární nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="ef320-103">The `+` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ef320-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef320-104">Remarks</span></span>  
 <span data-ttu-id="ef320-105">Unární `+` operátory jsou předdefinované pro všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="ef320-105">Unary `+` operators are predefined for all numeric types.</span></span> <span data-ttu-id="ef320-106">Výsledek unární `+` operace na číselný typ je hodnota operandu.</span><span class="sxs-lookup"><span data-stu-id="ef320-106">The result of a unary `+` operation on a numeric type is just the value of the operand.</span></span>  
  
 <span data-ttu-id="ef320-107">Binární `+` operátory jsou předdefinované typy číselným a řetězcovým.</span><span class="sxs-lookup"><span data-stu-id="ef320-107">Binary `+` operators are predefined for numeric and string types.</span></span> <span data-ttu-id="ef320-108">Pro číselné typy a vypočítá součet dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="ef320-108">For numeric types, + computes the sum of its two operands.</span></span> <span data-ttu-id="ef320-109">Pokud jeden nebo oba operandy jsou typu řetězec + zřetězí řetězcové reprezentace operandy.</span><span class="sxs-lookup"><span data-stu-id="ef320-109">When one or both operands are of type string, + concatenates the string representations of the operands.</span></span>  
  
 <span data-ttu-id="ef320-110">Typy delegátů také poskytují binární soubor `+` operátor, který provádí řetězení delegáta.</span><span class="sxs-lookup"><span data-stu-id="ef320-110">Delegate types also provide a binary `+` operator, which performs delegate concatenation.</span></span>  
  
 <span data-ttu-id="ef320-111">Uživatelem definované typy mohou přetížit unární `+` a binární `+` operátory.</span><span class="sxs-lookup"><span data-stu-id="ef320-111">User-defined types can overload the unary `+` and binary `+` operators.</span></span> <span data-ttu-id="ef320-112">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="ef320-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="ef320-113">Další informace najdete v tématu [– operátor (referenční dokumentace jazyka C#)](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="ef320-113">For more information, see [operator (C# Reference)](../../../csharp/language-reference/keywords/operator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef320-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef320-114">Example</span></span>  
 [!code-csharp[csRefOperators#28](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ef320-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef320-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ef320-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef320-116">See Also</span></span>

- [<span data-ttu-id="ef320-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef320-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ef320-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ef320-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ef320-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ef320-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="ef320-120">– Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ef320-120">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)
