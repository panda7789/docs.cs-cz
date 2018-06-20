---
title: () – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 82dfc2e11d6a8a025aa9b7557255a13b69ffa508
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208375"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bdef8-102">() – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bdef8-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="bdef8-103">Kromě používají k určení pořadí operací ve výrazu, kulaté závorky lze provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bdef8-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="bdef8-104">Zadejte přetypování a převody typu.</span><span class="sxs-lookup"><span data-stu-id="bdef8-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="bdef8-105">Vyvolání metody nebo delegáti.</span><span class="sxs-lookup"><span data-stu-id="bdef8-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="bdef8-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdef8-106">Remarks</span></span>  
 <span data-ttu-id="bdef8-107">Přetypování explicitně vyvolá operátor převodu z jednoho typu přetypování selže, pokud je definovaný žádný převod operátor.</span><span class="sxs-lookup"><span data-stu-id="bdef8-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="bdef8-108">Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="bdef8-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="bdef8-109">`()` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="bdef8-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="bdef8-110">Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="bdef8-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="bdef8-111">Další informace o volání metody najdete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="bdef8-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bdef8-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bdef8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bdef8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdef8-113">See Also</span></span>  
 [<span data-ttu-id="bdef8-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bdef8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bdef8-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bdef8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bdef8-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bdef8-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
