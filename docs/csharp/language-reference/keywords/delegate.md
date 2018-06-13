---
title: delegate (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: 4eafd0ffb6da191db80fd69f1980a167dbfc742b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172107"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="8a9dd-102">delegate (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8a9dd-102">delegate (C# Reference)</span></span>
<span data-ttu-id="8a9dd-103">Deklarace typu delegáta je podobná podpis metody.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="8a9dd-104">Má návratovou hodnotu a libovolný počet parametrů libovolného typu:</span><span class="sxs-lookup"><span data-stu-id="8a9dd-104">It has a return value and any number of parameters of any type:</span></span>  
  
```csharp  
public delegate void TestDelegate(string message);  
public delegate int TestDelegate(MyType m, long num);  
```  
  
 <span data-ttu-id="8a9dd-105">A `delegate` je odkaz na typ, který slouží k zapouzdření pojmenovaná nebo anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="8a9dd-106">Delegáti jsou podobná ukazatelů na funkce v jazyce C++; Delegáti jsou však bezpečnost typů a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="8a9dd-107">Aplikace delegáti, naleznete v [delegáti](../../../csharp/programming-guide/delegates/index.md) a [obecní delegáti](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="8a9dd-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a9dd-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a9dd-108">Remarks</span></span>  
 <span data-ttu-id="8a9dd-109">Delegáti slouží jako základ pro [události](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="8a9dd-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>  
  
 <span data-ttu-id="8a9dd-110">Delegát se dá vytvořit instance tím, že přidružíte buď pomocí metody s názvem nebo anonymní.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="8a9dd-111">Další informace najdete v tématu [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) a [anonymní metody](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="8a9dd-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>  
  
 <span data-ttu-id="8a9dd-112">Delegát musí být vytvořena s metoda nebo lambda výraz, který má kompatibilní návratový typ a vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="8a9dd-113">Další informace o stupeň odchylky, který je povolen v podpis metody naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="8a9dd-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="8a9dd-114">Pro použití s anonymní metody jsou delegát a kód, který se má přidružit ho deklarovat společně.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="8a9dd-115">Obou směrech konkretizujete Delegáti jsou popsané v této části.</span><span class="sxs-lookup"><span data-stu-id="8a9dd-115">Both ways of instantiating delegates are discussed in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a9dd-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a9dd-116">Example</span></span>  
 [!code-csharp[csrefKeywordsTypes#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/delegate_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8a9dd-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8a9dd-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8a9dd-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a9dd-118">See Also</span></span>  
 [<span data-ttu-id="8a9dd-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8a9dd-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8a9dd-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8a9dd-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8a9dd-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8a9dd-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8a9dd-122">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="8a9dd-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="8a9dd-123">Delegáti</span><span class="sxs-lookup"><span data-stu-id="8a9dd-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="8a9dd-124">Události</span><span class="sxs-lookup"><span data-stu-id="8a9dd-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
 [<span data-ttu-id="8a9dd-125">Delegáti s pojmenovanými vs. anonymními metodami</span><span class="sxs-lookup"><span data-stu-id="8a9dd-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
 [<span data-ttu-id="8a9dd-126">Anonymní metody</span><span class="sxs-lookup"><span data-stu-id="8a9dd-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
