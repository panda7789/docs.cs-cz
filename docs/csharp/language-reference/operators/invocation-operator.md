---
title: () – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 57c23dbd6ee95597514dba92e7217bdcc3e38f24
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236450"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="df19b-102">() – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="df19b-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="df19b-103">Kromě používá k určení pořadí operací ve výrazu závorky slouží k provádění následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="df19b-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="df19b-104">Zadejte přetypování a převody typů.</span><span class="sxs-lookup"><span data-stu-id="df19b-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="df19b-105">Vyvolání metod a delegátů.</span><span class="sxs-lookup"><span data-stu-id="df19b-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="df19b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="df19b-106">Remarks</span></span>  
 <span data-ttu-id="df19b-107">Přetypování vyvolá explicitní operátor převodu z jednoho typu na jiný; přetypování selže, pokud není definován žádný převod operátor.</span><span class="sxs-lookup"><span data-stu-id="df19b-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="df19b-108">Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../../../csharp/language-reference/keywords/explicit.md) a [implicitní](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="df19b-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="df19b-109">`()` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="df19b-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="df19b-110">Další informace najdete v tématu [přetypování a převody typů](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="df19b-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="df19b-111">Další informace o volání metody, naleznete v tématu [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="df19b-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="df19b-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df19b-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="df19b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="df19b-113">See Also</span></span>

- [<span data-ttu-id="df19b-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df19b-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="df19b-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="df19b-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="df19b-116">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="df19b-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
