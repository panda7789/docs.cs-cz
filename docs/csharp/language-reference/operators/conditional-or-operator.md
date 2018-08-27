---
title: '|| – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925537"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b4f23-102">|| – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b4f23-102">|| Operator (C# Reference)</span></span>
<span data-ttu-id="b4f23-103">Operátor podmíněného OR (`||`) provádí logický OR jeho `bool` operandy.</span><span class="sxs-lookup"><span data-stu-id="b4f23-103">The conditional-OR operator (`||`) performs a logical-OR of its `bool` operands.</span></span> <span data-ttu-id="b4f23-104">Pokud je první operand vyhodnocen jako `true`, není vyhodnocen Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="b4f23-104">If the first operand evaluates to `true`, the second operand isn't evaluated.</span></span> <span data-ttu-id="b4f23-105">Pokud je první operand vyhodnocen jako `false`, druhý operátor určuje, jestli jako celek výraz OR vyhodnocen `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="b4f23-105">If the first operand evaluates to `false`, the second operator determines whether the OR expression as a whole evaluates to `true` or `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4f23-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4f23-106">Remarks</span></span>  
 <span data-ttu-id="b4f23-107">Operace</span><span class="sxs-lookup"><span data-stu-id="b4f23-107">The operation</span></span>  
  
```csharp  
x || y  
```  
  
 <span data-ttu-id="b4f23-108">odpovídá operaci</span><span class="sxs-lookup"><span data-stu-id="b4f23-108">corresponds to the operation</span></span>  
  
```csharp  
x | y  
```  
  
 <span data-ttu-id="b4f23-109">s výjimkou, že pokud `x` je `true`, `y` není vyhodnocen, protože operace OR `true` bez ohledu na hodnotu `y`.</span><span class="sxs-lookup"><span data-stu-id="b4f23-109">except that if `x` is `true`, `y` is not evaluated because the OR operation is `true` regardless of the value of `y`.</span></span> <span data-ttu-id="b4f23-110">Tento koncept se označuje jako "zkrácené" vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="b4f23-110">This concept is known as "short-circuit" evaluation.</span></span>  
  
 <span data-ttu-id="b4f23-111">Operátor podmíněného OR nemůže být přetížená, ale přetíženími pravidelné logických operátorů a [true](../../../csharp/language-reference/keywords/true.md) a [false](../../../csharp/language-reference/keywords/false.md) operátorů, s určitými omezeními také považují za přetížení Podmíněné logické operátory.</span><span class="sxs-lookup"><span data-stu-id="b4f23-111">The conditional-OR operator cannot be overloaded, but overloads of the regular logical operators and the [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md) operators are, with certain restrictions, also considered to be overloads of the conditional logical operators.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4f23-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4f23-112">Example</span></span>  
 <span data-ttu-id="b4f23-113">V následujících příkladech, výraz, který používá `||` pouze první operand vyhodnocen jako.</span><span class="sxs-lookup"><span data-stu-id="b4f23-113">In the following examples, the expression that uses `||` evaluates only the first operand.</span></span> <span data-ttu-id="b4f23-114">Výraz, který používá `|` vyhodnotí oba operandy.</span><span class="sxs-lookup"><span data-stu-id="b4f23-114">The expression that uses `|` evaluates both operands.</span></span> <span data-ttu-id="b4f23-115">V druhém příkladu dojde k výjimce za běhu je-li oba operandy vyhodnocují.</span><span class="sxs-lookup"><span data-stu-id="b4f23-115">In the second example, a run-time exception occurs if both operands are evaluated.</span></span>  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b4f23-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4f23-116">See Also</span></span>

- [<span data-ttu-id="b4f23-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b4f23-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b4f23-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b4f23-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b4f23-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b4f23-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
