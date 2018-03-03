---
title: "?: – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbd434e02ece4843bab4ffded6877f81f622950c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="64131-102">?: – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="64131-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="64131-103">Podmíněný operátor (`?:`), často označovaný jako Ternární podmíněný operátor vrátí jeden ze dvou hodnot v závislosti na hodnotě výrazu logické hodnoty.</span><span class="sxs-lookup"><span data-stu-id="64131-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="64131-104">Následuje syntaxe pro podmiňovací operátor.</span><span class="sxs-lookup"><span data-stu-id="64131-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="64131-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="64131-105">Remarks</span></span>  
 <span data-ttu-id="64131-106">`condition` Se musí vyhodnotit `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="64131-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="64131-107">Pokud `condition` je `true`, `first_expression` je vyhodnocena a že bude výsledek.</span><span class="sxs-lookup"><span data-stu-id="64131-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="64131-108">Pokud `condition` je `false`, `second_expression` je vyhodnocena a že bude výsledek.</span><span class="sxs-lookup"><span data-stu-id="64131-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="64131-109">Je vyhodnocen pouze jeden ze dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="64131-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="64131-110">Buď typ `first_expression` a `second_expression` musí být stejné, nebo implicitní převod musí existovat z jednoho typu na druhý.</span><span class="sxs-lookup"><span data-stu-id="64131-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="64131-111">Můžete express výpočty, které mohou vyžadovat jinak `if-else` vytváření více výstižně pomocí podmíněný operátor.</span><span class="sxs-lookup"><span data-stu-id="64131-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="64131-112">Například následující kód používá nejprve `if` příkaz a poté podmíněný operátor klasifikovat jako kladné nebo záporné celé číslo.</span><span class="sxs-lookup"><span data-stu-id="64131-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
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
  
 <span data-ttu-id="64131-113">Podmiňovací operátor je asociativní zprava.</span><span class="sxs-lookup"><span data-stu-id="64131-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="64131-114">Výraz `a ? b : c ? d : e` je vyhodnoceno jako `a ? b : (c ? d : e)`, ne jako `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="64131-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="64131-115">Podmiňovací operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="64131-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64131-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="64131-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64131-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="64131-117">See Also</span></span>  
 [<span data-ttu-id="64131-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64131-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="64131-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="64131-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="64131-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="64131-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="64131-121">if-else</span><span class="sxs-lookup"><span data-stu-id="64131-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 [<span data-ttu-id="64131-122">?. a? Operátory</span><span class="sxs-lookup"><span data-stu-id="64131-122">?. and ?Operators</span></span>](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [<span data-ttu-id="64131-123">?? – operátor</span><span class="sxs-lookup"><span data-stu-id="64131-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
