---
title: '|| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: 25
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6f8e9-102">|| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6f8e9-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="6f8e9-103">Operátor podmíněného OR (`||`) provede logickou funkcí – nebo jeho `bool` operandy.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="6f8e9-104">Pokud je výsledkem první operand `true`, druhý operand, nebude hodnocen.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="6f8e9-105">Pokud je výsledkem první operand `false`, druhý operátor určuje, zda výraz OR jako celek vyhodnotí `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f8e9-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f8e9-106">Remarks</span></span>  
 <span data-ttu-id="6f8e9-107">Operaci</span><span class="sxs-lookup"><span data-stu-id="6f8e9-107">The operation</span></span>  
  
```  
x || y  
```  
  
 <span data-ttu-id="6f8e9-108">odpovídá operaci</span><span class="sxs-lookup"><span data-stu-id="6f8e9-108">corresponds to the operation</span></span>  
  
```  
x | y  
```  
  
 <span data-ttu-id="6f8e9-109">s výjimkou, že pokud `x` je `true`, `y` není vyhodnotit, protože operace nebo je `true` bez ohledu na hodnotu `y`.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="6f8e9-110">Tento koncept se označuje jako "krátká smyčka –" vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="6f8e9-111">Operátor podmíněného OR nemohou být přetíženy, ale přetížení regulární logických operátorů a [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) operátory se s určitými omezeními také považuje za přetížení Podmíněné logické operátory.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f8e9-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="6f8e9-112">Example</span></span>  
 <span data-ttu-id="6f8e9-113">V následujících příkladech výraz, který používá `||` vyhodnotí pouze první operand.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="6f8e9-114">Výraz, který používá `|` vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="6f8e9-115">V druhém příkladu došlo k výjimce běhu Pokud oba operandy, jsou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="6f8e9-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6f8e9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f8e9-116">See Also</span></span>  
 [<span data-ttu-id="6f8e9-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f8e9-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6f8e9-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6f8e9-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6f8e9-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6f8e9-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
