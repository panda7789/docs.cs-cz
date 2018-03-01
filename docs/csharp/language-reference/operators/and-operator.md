---
title: "&amp;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="037d3-102">&amp;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="037d3-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="037d3-103">& Operátor může fungovat jako unární operátor nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="037d3-103">The & operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="037d3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="037d3-104">Remarks</span></span>  
 <span data-ttu-id="037d3-105">Operátor unární & vrátí adresu jeho operand (vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu).</span><span class="sxs-lookup"><span data-stu-id="037d3-105">The unary & operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="037d3-106">Binární & operátory jsou předdefinovány pro integrální typy a `bool`.</span><span class="sxs-lookup"><span data-stu-id="037d3-106">Binary & operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="037d3-107">Pro integrální typy & vypočítá logické bitové operace AND z operandů.</span><span class="sxs-lookup"><span data-stu-id="037d3-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="037d3-108">Pro `bool` operandy & výpočtů logické a operandů; výsledek je `true` Pokud jsou obě jejími operandy `true`.</span><span class="sxs-lookup"><span data-stu-id="037d3-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="037d3-109">`&` Operátor vyhodnotí oba operátory bez ohledu na první z nich je hodnota.</span><span class="sxs-lookup"><span data-stu-id="037d3-109">The `&` operator evaluates both operators regardless of the first one's value.</span></span> <span data-ttu-id="037d3-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="037d3-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="037d3-111">Uživatelem definované typy může přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="037d3-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="037d3-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="037d3-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="037d3-113">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="037d3-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="037d3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="037d3-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="037d3-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="037d3-115">See Also</span></span>  
 [<span data-ttu-id="037d3-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="037d3-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="037d3-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="037d3-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="037d3-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="037d3-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
