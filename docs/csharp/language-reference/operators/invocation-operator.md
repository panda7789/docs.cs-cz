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
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275022"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="46448-102">() – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="46448-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="46448-103">Kromě používají k určení pořadí operací ve výrazu, kulaté závorky lze provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="46448-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="46448-104">Zadejte přetypování a převody typu.</span><span class="sxs-lookup"><span data-stu-id="46448-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="46448-105">Vyvolání metody nebo delegáti.</span><span class="sxs-lookup"><span data-stu-id="46448-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="46448-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46448-106">Remarks</span></span>  
 <span data-ttu-id="46448-107">Přetypování explicitně vyvolá operátor převodu z jednoho typu přetypování selže, pokud je definovaný žádný převod operátor.</span><span class="sxs-lookup"><span data-stu-id="46448-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="46448-108">Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="46448-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="46448-109">`()` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="46448-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="46448-110">Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="46448-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="46448-111">Výraz cast může vést k nejednoznačný syntaxe.</span><span class="sxs-lookup"><span data-stu-id="46448-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="46448-112">Například výraz `(x)–y` může být buď interpretovat jako výraz přetypování (přetypování y – typ x) nebo jako doplňkové výrazu kombinovat s výrazu v závorkách, která vypočítá hodnotu x – y.</span><span class="sxs-lookup"><span data-stu-id="46448-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="46448-113">Další informace o volání metody najdete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="46448-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="46448-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46448-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46448-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="46448-115">See Also</span></span>  
 [<span data-ttu-id="46448-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46448-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="46448-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="46448-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="46448-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46448-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
