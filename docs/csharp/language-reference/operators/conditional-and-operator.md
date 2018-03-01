---
title: "&amp;&amp;Operátor (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="5ad22-102">&amp;&amp;Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5ad22-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="5ad22-103">Podmínku – a – operátor (`&&`) provede logickou- a jeho `bool` operandy, ale pouze vyhodnotí svůj druhý operand v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="5ad22-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ad22-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ad22-104">Remarks</span></span>  
 <span data-ttu-id="5ad22-105">Operaci</span><span class="sxs-lookup"><span data-stu-id="5ad22-105">The operation</span></span>  
  
```  
x && y  
```  
  
 <span data-ttu-id="5ad22-106">odpovídá operaci</span><span class="sxs-lookup"><span data-stu-id="5ad22-106">corresponds to the operation</span></span>  
  
```  
x & y  
```  
  
 <span data-ttu-id="5ad22-107">s výjimkou, že pokud `x` je `false`, `y` není vyhodnotit, protože je výsledek operace a `false` bez ohledu na to, jaké hodnota `y` je.</span><span class="sxs-lookup"><span data-stu-id="5ad22-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="5ad22-108">To se označuje jako "krátká smyčka –" vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="5ad22-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="5ad22-109">Podmínku- a operátor nemůže být přetížené, ale přetížení regulární logické operátory a operátory [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) jsou, s určitými omezeními také považovány za přetížení Podmíněné logické operátory.</span><span class="sxs-lookup"><span data-stu-id="5ad22-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ad22-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ad22-110">Example</span></span>  
 <span data-ttu-id="5ad22-111">V následujícím příkladu, podmíněným výrazem za sekundu `if` příkaz vyhodnocuje pouze první operand, protože operand vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="5ad22-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="5ad22-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ad22-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ad22-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ad22-113">See Also</span></span>  
 [<span data-ttu-id="5ad22-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ad22-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5ad22-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5ad22-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5ad22-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5ad22-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
