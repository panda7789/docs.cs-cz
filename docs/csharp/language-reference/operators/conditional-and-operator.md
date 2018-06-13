---
title: '&amp;&amp; Operátor (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 15bb3e9702f04cc805af63767c7ecbfc68160368
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171912"
---
# <a name="ampamp-operator-c-reference"></a><span data-ttu-id="8b297-102">&amp;&amp; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8b297-102">&amp;&amp; Operator (C# Reference)</span></span>
<span data-ttu-id="8b297-103">Podmínku – a – operátor (`&&`) provede logickou- a jeho `bool` operandy, ale pouze vyhodnotí svůj druhý operand v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="8b297-103">The conditional-AND operator (`&&`) performs a logical-AND of its `bool` operands, but only evaluates its second operand if necessary.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b297-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b297-104">Remarks</span></span>  
 <span data-ttu-id="8b297-105">Operaci</span><span class="sxs-lookup"><span data-stu-id="8b297-105">The operation</span></span>  
  
```csharp  
x && y  
```  
  
 <span data-ttu-id="8b297-106">odpovídá operaci</span><span class="sxs-lookup"><span data-stu-id="8b297-106">corresponds to the operation</span></span>  
  
```csharp  
x & y  
```  
  
 <span data-ttu-id="8b297-107">s výjimkou, že pokud `x` je `false`, `y` není vyhodnotit, protože je výsledek operace a `false` bez ohledu na to, jaké hodnota `y` je.</span><span class="sxs-lookup"><span data-stu-id="8b297-107">except that if `x` is `false`, `y` is not evaluated, because the result of the AND operation is `false` no matter what the value of `y`  is.</span></span> <span data-ttu-id="8b297-108">To se označuje jako "krátká smyčka –" vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="8b297-108">This is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="8b297-109">Podmínku- a operátor nemůže být přetížené, ale přetížení regulární logické operátory a operátory [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) jsou, s určitými omezeními také považovány za přetížení Podmíněné logické operátory.</span><span class="sxs-lookup"><span data-stu-id="8b297-109">The conditional-AND operator cannot be overloaded, but overloads of the regular logical operators and operators [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) are, with certain restrictions, also considered overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b297-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8b297-110">Example</span></span>  
 <span data-ttu-id="8b297-111">V následujícím příkladu, podmíněným výrazem za sekundu `if` příkaz vyhodnocuje pouze první operand, protože operand vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="8b297-111">In the following example, the conditional expression in the second `if` statement evaluates only the first operand because the operand returns `false`.</span></span>  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8b297-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b297-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8b297-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b297-113">See Also</span></span>  
 [<span data-ttu-id="8b297-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b297-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8b297-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8b297-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8b297-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8b297-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
