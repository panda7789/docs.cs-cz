---
title: '?: – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 150149453a67d8e5319461266865cb25be180347
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506429"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="fdb91-102">?: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fdb91-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="fdb91-103">Podmíněný operátor (`?:`), obvykle označovaný jako Ternární podmiňovací operátor vrátí jednu ze dvou hodnot v závislosti na hodnotě logického výrazu.</span><span class="sxs-lookup"><span data-stu-id="fdb91-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="fdb91-104">Následuje syntaxe pro podmiňovací operátor.</span><span class="sxs-lookup"><span data-stu-id="fdb91-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="fdb91-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fdb91-105">Remarks</span></span>  
 <span data-ttu-id="fdb91-106">`condition` Se musí vyhodnotit na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="fdb91-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="fdb91-107">Pokud `condition` je `true`, `first_expression` jsou vyhodnoceny a výsledek.</span><span class="sxs-lookup"><span data-stu-id="fdb91-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="fdb91-108">Pokud `condition` je `false`, `second_expression` jsou vyhodnoceny a výsledek.</span><span class="sxs-lookup"><span data-stu-id="fdb91-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="fdb91-109">Je vyhodnocen pouze jeden ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="fdb91-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="fdb91-110">Typ parametru `first_expression` a `second_expression` musí být stejné, nebo musí existovat implicitní převod z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="fdb91-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="fdb91-111">Můžete vyjádřit výpočty, které by jinak vyžadovaly `if-else` konstrukce více stručně a výstižně pomocí podmíněného operátoru.</span><span class="sxs-lookup"><span data-stu-id="fdb91-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="fdb91-112">Například následující kód používá nejprve `if` příkaz a poté podmiňovací operátor pro klasifikaci celého čísla jako kladné nebo záporné.</span><span class="sxs-lookup"><span data-stu-id="fdb91-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="fdb91-113">Podmiňovací operátor je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="fdb91-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="fdb91-114">Výraz `a ? b : c ? d : e` se vyhodnotí jako `a ? b : (c ? d : e)`, nikoli jako `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="fdb91-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="fdb91-115">Podmiňovací operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="fdb91-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdb91-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdb91-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="fdb91-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdb91-117">See Also</span></span>

- [<span data-ttu-id="fdb91-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fdb91-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fdb91-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fdb91-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fdb91-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fdb91-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="fdb91-121">if-else</span><span class="sxs-lookup"><span data-stu-id="fdb91-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="fdb91-122">[Operátory ?. a ?[]](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="fdb91-122">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="fdb91-123">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="fdb91-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
