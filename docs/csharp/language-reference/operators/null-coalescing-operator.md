---
title: ?? Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ??_CSharpKeyword
helpviewer_keywords:
- coalesce operator [C#]
- ?? operator [C#]
- conditional-AND operator (&&) [C#]
ms.assetid: 088b1f0d-c1af-4fe1-b4b8-196fd5ea9132
ms.openlocfilehash: 8fa751654acaf5939fb8f8068c7323e365f7bdab
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e3c98-103">??</span><span class="sxs-lookup"><span data-stu-id="e3c98-103">??</span></span> <span data-ttu-id="e3c98-104">Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e3c98-104">Operator (C# Reference)</span></span>
<span data-ttu-id="e3c98-105">`??` Operátor se označuje jako operátor slučování hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="e3c98-105">The `??` operator is called the null-coalescing operator.</span></span>  <span data-ttu-id="e3c98-106">Vrátí levý operand, pokud hodnota operandu není null; v opačném případě vrátí pravý operand.</span><span class="sxs-lookup"><span data-stu-id="e3c98-106">It returns the left-hand operand if the operand is not null; otherwise it returns the right hand operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3c98-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3c98-107">Remarks</span></span>  
 <span data-ttu-id="e3c98-108">Typ povolené hodnoty null představuje hodnotu z domény typu, hodnotu lze také definovat (v takovém případě je hodnota null).</span><span class="sxs-lookup"><span data-stu-id="e3c98-108">A nullable type can represent a value from the type’s domain, or the value can be undefined (in which case the value is null).</span></span> <span data-ttu-id="e3c98-109">Můžete použít `??` operátor je syntaktická expressiveness vrátit hodnotu odpovídající (pravém operand) Pokud má levý operand typu s povolenou hodnotou Null, jehož hodnota je null.</span><span class="sxs-lookup"><span data-stu-id="e3c98-109">You can use the `??` operator’s syntactic expressiveness to return an appropriate value (the right hand operand) when the left operand has a nullable type whose value is null.</span></span> <span data-ttu-id="e3c98-110">Pokud se pokusíte přiřadit typ s možnou hodnotou Null hodnoty typu hodnot neumožňující hodnotu Null bez použití `??` operátor, vygeneruje chyby kompilace.</span><span class="sxs-lookup"><span data-stu-id="e3c98-110">If you try to assign a nullable value type to a non-nullable value type without using the `??` operator, you will generate a compile-time error.</span></span> <span data-ttu-id="e3c98-111">Pokud používáte přetypování a typ s možnou hodnotou Null hodnoty je aktuálně definován `InvalidOperationException` dojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="e3c98-111">If you use a cast, and the nullable value type is currently undefined, an `InvalidOperationException` exception will be thrown.</span></span>  
  
 <span data-ttu-id="e3c98-112">Další informace najdete v tématu [typy s možnou hodnotou Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3c98-112">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
 <span data-ttu-id="e3c98-113">Výsledek??</span><span class="sxs-lookup"><span data-stu-id="e3c98-113">The result of a ??</span></span> <span data-ttu-id="e3c98-114">operátor se nepovažuje za konstanta, i když jsou oba argumenty konstanty.</span><span class="sxs-lookup"><span data-stu-id="e3c98-114">operator is not considered to be a constant even if both its arguments are constants.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3c98-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3c98-115">Example</span></span>  
 [!code-csharp[csRefOperators#53](../../../csharp/language-reference/operators/codesnippet/CSharp/null-conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3c98-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3c98-116">See Also</span></span>  
 [<span data-ttu-id="e3c98-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3c98-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e3c98-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e3c98-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3c98-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e3c98-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="e3c98-120">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="e3c98-120">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="e3c98-121">Jaké přesně nemá 'Zrušit' znamená?</span><span class="sxs-lookup"><span data-stu-id="e3c98-121">What Exactly Does 'Lifted' mean?</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
