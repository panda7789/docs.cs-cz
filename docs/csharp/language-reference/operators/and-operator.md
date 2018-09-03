---
title: '&amp; – Operátor (referenční dokumentace jazyka C#)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467371"
---
# <a name="amp-operator-c-reference"></a><span data-ttu-id="e761c-102">&amp; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e761c-102">&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="e761c-103">`&` Operátor může fungovat jako unární nebo binární operátor.</span><span class="sxs-lookup"><span data-stu-id="e761c-103">The `&` operator can function as either a unary or a binary operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e761c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e761c-104">Remarks</span></span>  
 <span data-ttu-id="e761c-105">Unární `&` operátor vrátí adresu svého operandu (vyžaduje [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) kontext).</span><span class="sxs-lookup"><span data-stu-id="e761c-105">The unary `&` operator returns the address of its operand (requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context).</span></span>  
  
 <span data-ttu-id="e761c-106">Binární `&` pro integrální typy jsou předdefinované operátory a `bool`.</span><span class="sxs-lookup"><span data-stu-id="e761c-106">Binary `&` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="e761c-107">Pro integrální typy & vypočítá logické bitové operace AND operandů.</span><span class="sxs-lookup"><span data-stu-id="e761c-107">For integral types, & computes the logical bitwise AND of its operands.</span></span> <span data-ttu-id="e761c-108">Pro `bool` operandy & logický výpočetní prostředí a jeho operandy; to znamená, výsledek je `true` pouze v případě jsou oba operandy jeho `true`.</span><span class="sxs-lookup"><span data-stu-id="e761c-108">For `bool` operands, & computes the logical AND of its operands; that is, the result is `true` if and only if both its operands are `true`.</span></span>  
  
 <span data-ttu-id="e761c-109">Binární soubor `&` operátor vyhodnotí oba operandy bez ohledu na to první hodnotu, oproti k [podmiňovací operátor AND](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span><span class="sxs-lookup"><span data-stu-id="e761c-109">The binary `&` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional AND operator](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`.</span></span> <span data-ttu-id="e761c-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e761c-110">For example:</span></span>  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 <span data-ttu-id="e761c-111">Uživatelem definované typy mohou přetížit binárního souboru `&` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="e761c-111">User-defined types can overload the binary `&` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="e761c-112">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="e761c-112">Operations on integral types are generally allowed on enumeration.</span></span> <span data-ttu-id="e761c-113">Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="e761c-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e761c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="e761c-114">Example</span></span>  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e761c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e761c-115">See Also</span></span>

- [<span data-ttu-id="e761c-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e761c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e761c-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e761c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e761c-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e761c-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
