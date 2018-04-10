---
title: '&amp; Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
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
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f26305bfa1e8c9ba45493ad2ab4937d554590911
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="71866-102">&amp; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="71866-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="71866-103">`&` Operátor může fungovat jako unární operátor nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="71866-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71866-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71866-104">Remarks</span></span>  
 <span data-ttu-id="71866-105">Unární `&` operátor vrátí adresu jeho operand (vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu).</span><span class="sxs-lookup"><span data-stu-id="71866-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="71866-106">Binární `&` jsou operátory předdefinovány pro integrální typy a `bool`.</span><span class="sxs-lookup"><span data-stu-id="71866-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="71866-107">Pro integrální typy & vypočítá logické bitové operace AND z operandů.</span><span class="sxs-lookup"><span data-stu-id="71866-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="71866-108">Pro `bool` operandy & výpočtů logické a operandů; výsledek je `true` Pokud jsou obě jejími operandy `true`.</span><span class="sxs-lookup"><span data-stu-id="71866-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="71866-109">Binárního souboru `&` operátor vyhodnotí oba operátory bez ohledu na první z nich je hodnotu, na rozdíl od [operátor podmíněného AND](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="71866-109">The binary `&` operator evaluates both operators regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="71866-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="71866-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="71866-111">Uživatelem definované typy může přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="71866-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="71866-112">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="71866-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="71866-113">Při binární operátor je přetížena, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="71866-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71866-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="71866-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="71866-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="71866-115">See Also</span></span>  
 [<span data-ttu-id="71866-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71866-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71866-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="71866-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71866-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71866-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
